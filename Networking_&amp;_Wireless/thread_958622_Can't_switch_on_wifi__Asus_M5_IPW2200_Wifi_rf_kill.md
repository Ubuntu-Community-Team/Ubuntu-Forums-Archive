---
title: "Can't switch on wifi : Asus M5 IPW2200 Wifi rf_kill"
date: 2008-10-25
forum: Networking &amp; Wireless
---

### Post by wanfahmi on 2008-10-25
Hi,

The problem is, when I press the function switch Fn-F2 (Wireless), it will switch off my wifi. Pressing the button again does nothing (I can't switch ON my wifi). A reboot switches on the wifi.
When my wifi is working,
```
cat /sys/class/net/eth1/device/rf_kill
```
Will have an output of **0**
After pressing the hotkey , output is **3**
Doing the following doesn't help, it just changes rf_kill to **2**
```
echo 0 > /sys/bus/pci/drivers/ipw2200/*/rf_kill
```



This is output from /var/log/acpid
```
received event "hotkey ATKD 0000005d 00000000"
notifying client 6327[111:123]
notifying client 6541[0:0]
executing action "/etc/acpi/asus-wireless.sh"
BEGIN HANDLER MESSAGES
END HANDLER MESSAGES
action exited with status 0
```
*So pressing the hotkey, calls this *
/etc/acpi/asus-wireless.sh
```
!/bin/sh
# Find and toggle wireless devices on Asus laptops

. /usr/share/acpi-support/state-funcs

toggleAllWirelessStates;

# Update the Asus LED to reflect the new status of the wireless
! isAnyWirelessPoweredOn;
setLEDAsusWireless $?
```
Which in turn, calls
```
#!/bin/sh
# Paul Sladen, 2006-03-28, 2007-03-26
# Library functions to check/change status of wireless

# Return 0 if there is, allowing you to write   if isAnyWirelessPoweredOn; then ...
isAnyWirelessPoweredOn()
{
    for DEVICE in /sys/class/net/* ; do
	if [ -d $DEVICE/wireless ]; then
	    # if any of the wireless devices are turned on then return success
	    if [ -r $DEVICE/device/power/state ] && [ "`cat $DEVICE/device/power/state`" -eq 0 ]
	    then
		return 0
	    fi
	    if [ -r $DEVICE/device/rf_kill ] && [ "`cat $DEVICE/device/rf_kill`" -eq 0 ]
	    then
		return 0
	    fi
	fi
    done
    # otherwise return failure
    return 1
}

# Takes no parameters, toggles all wireless devices.
# TODO: Should possible toggle all wireless devices to the state of the first one.
# Attempts to use 'rf_kill' first, and then tries 'power/state', though that
# will fail on >=2.6.18 kernels since upstream removed the functionality...
toggleAllWirelessStates()
{
    for DEVICE in /sys/class/net/* ; do
	if [ -d $DEVICE/wireless ] ; then
	    # $DEVICE is a wireless device. Check if it's powered on:
	    ON=0
	    OFF=1  # 1 for rf_kill, 2 for power/state
	    for CONTROL in $DEVICE/device/rf_kill $DEVICE/device/power/state ; do
		if [ -w $CONTROL ] ; then
		    # We have a way of controlling the device, lets try
		    if [ "`cat $CONTROL`" = 0 ] ; then
			# It's powered on. Switch it off.
			if echo -n $OFF > $CONTROL ; then 
			    break
			else
			    OFF=2 # for power/state, second time around
			fi
		    else
			# It's powered off. Switch it on.
			if echo -n $ON > $CONTROL ; then
			    break
			fi
		    fi
		fi
	    done
	fi
    done
}

# Pass '1' to blink suspending LED and '0' to stop LED
setLEDThinkpadSuspending()
{
    action=`test "$1" -ne 0 && echo blink || echo off`
    test -w /proc/acpi/ibm/led && echo -n 7 "$action" > /proc/acpi/ibm/led
}

# Pass '1' to light LED and '0' to dark LED
setLEDAsusWireless()
{
    action=`test "$1" -ne 0 && echo 1 || echo 0`
    test -w /proc/acpi/asus/wled && echo -n "$action" > /proc/acpi/asus/wled
    test -w /sys/devices/platform/asus-laptop/wlan && echo -n "$action" > /sys/devices/platform/asus-laptop/wlan
}
```

I'm guessing, something is not right in the above script. Any help will be much appreciated.

---

### Post by wanfahmi on 2008-10-25
b. Anyone?

---

