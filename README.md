# macOS-system-metrics
These are anythings that find to know system metrics for macOS

<pre>
1. pmset
SETTINGS
     displaysleep - display sleep timer; replaces 'dim' argument in 10.4 (value in minutes, or 0 to disable)
     disksleep - disk spindown timer; replaces 'spindown' argument in 10.4 (value in minutes, or 0 to disable)
     sleep - system sleep timer (value in minutes, or 0 to disable)
     womp - wake on ethernet magic packet (value = 0/1). Same as "Wake for network access" in the Energy Saver preferences.
     ring - wake on modem ring (value = 0/1)
     powernap - enable/disable Power Nap on supported machines (value = 0/1)
     proximitywake - On supported systems, this option controls system wake from sleep based on proximity of devices using same iCloud id. (value = 0/1)
     autorestart - automatic restart on power loss (value = 0/1)
     lidwake - wake the machine when the laptop lid (or clamshell) is opened (value = 0/1)
     acwake - wake the machine when power source (AC/battery) is changed (value = 0/1)
     lessbright - slightly turn down display brightness when switching to this power source (value = 0/1)
     halfdim - display sleep will use an intermediate half-brightness state between full brightness and fully off  (value = 0/1)
     sms - use Sudden Motion Sensor to park disk heads on sudden changes in G force (value = 0/1)
     hibernatemode - change hibernation mode. Please use caution. (value = integer)
     hibernatefile - change hibernation image file location. Image may only be located on the root volume. Please use caution. (value = path)
     ttyskeepawake - prevent idle system sleep when any tty (e.g. remote login session) is 'active'. A tty is 'inactive' only when its idle time exceeds the system sleep timer. (value = 0/1)
     networkoversleep - this setting affects how OS X networking presents shared network services during system sleep. This setting is not used by all platforms; changing its value is
     unsupported.
     destroyfvkeyonstandby - Destroy File Vault Key when going to standby mode. By default File vault keys are retained even when system goes to standby. If the keys are destroyed, user will
     be prompted to enter the password while coming out of standby mode.(value: 1 - Destroy, 0 - Retain)
GETTING
     -g (with no argument) will display the settings currently in use.
     -g live displays the settings currently in use.
     -g custom displays custom settings for all power sources.
     -g cap displays which power management features the machine supports.
     -g sched displays scheduled startup/wake and shutdown/sleep events.
     -g ups displays UPS emergency thresholds.
     -g ps / batt displays status of batteries and UPSs.
     -g pslog displays an ongoing log of power source (battery and UPS) state.
     -g rawlog displays an ongoing log of battery state as read directly from battery.
     -g therm shows thermal conditions that affect CPU speed. Not available on all platforms.
     -g thermlog shows a log of thermal notifications that affect CPU speed. Not available on all platforms.
     -g assertions displays a summary of power assertions. Assertions may prevent system sleep or display sleep. Available 10.6 and later.
     -g assertionslog shows a log of assertion creations and releases. Available 10.6 and later.
     -g sysload displays the "system load advisory" - a summary of system activity available from the IOGetSystemLoadAdvisory API. Available 10.6 and later.
     -g sysloadlog displays an ongoing log of lives changes to the system load advisory. Available 10.6 and later.
     -g ac / adapter will display details about an attached AC power adapter. Only supported for MacBook and MacBook Pro.
     -g log displays a history of sleeps, wakes, and other power management events. This log is for admin & debugging purposes.
     -g uuid displays the currently active sleep/wake UUID; used within OS X to correlate sleep/wake activity within one sleep cycle.  history
     -g uuidlog displays the currently active sleep/wake UUID, and prints a new UUID as they're set by the system.
     -g history is a debugging tool. Prints a timeline of system sleeplwake UUIDs, when enabled with boot-arg io=0x3000000.
     -g historydetailed Prints driver-level timings for a sleep/wake. Pass a UUID as an argument.
     -g powerstate [class names] Prints the current power states for I/O Kit drivers. Caller may provide one or more I/O Kit class names (separated by spaces) as an argument. If no classes
     are provided, it will print all drivers' power states.
     -g powerstatelog [-i interval] [class names] Periodically prints the power state residency times for some drivers. Caller may provide one or more I/O Kit class names (separated by
     spaces). If no classes are provided, it will log the IOPower plane's root registry entry. Caller may specify a polling interval, in seconds with -i <polling interval>; otherwise it
     defaults to 5 seconds.
     -g stats Prints the counts for number sleeps and wakes system has gone thru since boot.
     -g systemstate Prints the current power state of the system and available capabilites.
     -g everything Prints output from every argument under the GETTING header. This is useful for quickly collecting all the output that pmset provides. Available in 10.8.

EXAMPLES
     This command sets displaysleep to a 5 minute timer on battery power, leaving other settings on battery power and other power sources unperturbed.

     pmset -b displaysleep 5

     Sets displaysleep to 10, disksleep to 10, system sleep to 30, and turns on WakeOnMagicPacket for ALL power sources (AC, Battery, and UPS) as appropriate

     pmset -a displaysleep 10 disksleep 10 sleep 30 womp 1

     Restores the system's energy settings to their default values.

     For a system with an attached and supported UPS, this instructs the system to perform an emergency shutdown when UPS battery drains to below 40%.

     pmset -u haltlevel 40

     For a system with an attached and supported UPS, this instructs the system to perform an emergency shutdown when UPS battery drains to below 25%, or when the UPS estimates it has less
     than 30 minutes remaining runtime. The system shuts down as soon as either of these conditions is met.

     pmset -u haltlevel 25 haltremain 30

     For a system with an attached and supported UPS, this instructs the system to perform an emergency shutdown after 2 minutes of running on UPS battery power.

     pmset -u haltafter 2

     Schedules the system to automatically wake from sleep on July 4, 2016, at 8PM.

     pmset schedule wake "07/04/16 20:00:00"

     Schedules a repeating shutdown to occur each day, Tuesday through Saturday, at 11AM.

     pmset repeat shutdown TWRFS 11:00:00

     Schedules a repeating wake or power on event every tuesday at 12:00 noon, and a repeating sleep event every night at 8:00 PM.

     pmset repeat wakeorpoweron T 12:00:00 sleep MTWRFSU 20:00:00

     Prints the power management settings in use by the system.

     pmset -g

     Prints a snapshot of battery/power source state at the moment.

     pmset -g batt

2. sudo powermetrics
DESCRIPTION
     powermetrics gathers and display CPU usage statistics (divided into time spent in user mode and supervisor mode), timer and interrupt wakeup frequency (total and, for near-idle
     workloads, those that resulted in package idle exits), and on supported platforms, interrupt frequencies (categorized by CPU number), package C-state statistics (an indication of the
     time the core complex + integrated graphics, if any, were in low-power idle states), as well as the average execution frequency for each CPU when not idle.

EXAMPLES
	sudo powermactrics | grep "idle-regidency"
	E-Cluster idle residency:  26.64%
	CPU 0 idle residency:  34.85%
	CPU 1 idle residency:  35.65%
	P0-Cluster idle residency:  83.29%
	CPU 2 idle residency:  85.58%
	CPU 3 idle residency:  92.70%
	CPU 4 idle residency:  96.18%
	P1-Cluster idle residency:  96.32%
	CPU 5 idle residency:  96.62%
	CPU 6 idle residency:  98.17%
	CPU 7 idle residency:  98.97%
	GPU idle residency:  71.19%
</pre>
