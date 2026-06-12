---
title: "Screen Brightness is at a minimum after suspend"
date: 2009-12-27
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-12-27
whenever i suspend my laptop the screen brightness is at a minimum when i wake it up.  does anyone have a fix for this?

---

### Post by bakelitedoorbell on 2010-05-09
Did you find a fix for this?  It's happening with me too, running a fresh install of Lucid Lynx.  Brightness is at the minimum after resuming from hibernate

---

### Post by chris01282 on 2010-05-09
Are you using HP/Compaq laptops ?
If so it is something that my nx6325 laptop used to suffer from when I was using Windows 7 on it, and it could be a hardware/driver issue.
Just a thought as it seems similar to my problem before I install 10.04

---

### Post by neu5eeCh on 2010-05-10
[My laptop]("http://ubuntuforums.org/showthread.php?t=1479372") is doing the same thing. It's [Bug 451282]("https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/451282"), and as far as I can ascertain: 1.)[COLOR=Silver]  there is no solution to the problem[/COLOR] 2.) the bug has been around for years 3.) the bug has a low priority which means, unless I'm mistaken, that Canonical hasn't been, and **isn't** very motivated to fix it.

I was wrong. Mea Culpa.

The solution offered at the Bug Listing worked with a minor tweak that I missed the first time. Here is what I added to /etc/rc.local (as per instructions):

> brt=`cat /sys/devices/virtual/backlight/acpi_video0/brightness`
abrt=`cat /sys/devices/virtual/backlight/acpi_video0/actual_brightness`
if [ "$brt" != "$abrt" ]; then
echo $abrt > /sys/devices/virtual/backlight/acpi_video0/brightness
fi 			 		

---

### Post by vel. on 2010-09-06
Here is the solution:
@ [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451282](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/451282)

> pauls wrote on 2010-04-28:	 #26
I wonder if there was a change in how acpi records / sets brightness and gnome-power-manager was not updated to realize it.

I notice 2 different kernel locations on my system for brightness.

One is /sys/devices/virtual/backlight/acpi_video0/brightness and has the value of 0 on boot up. This seems strange because the lcd is at maximum brightness.

The other is /sys/devices/virtual/backlight/acpi_video0/actual_brightness and has the value of 7 on boot up. On my system, 7 is the maximum.

I suspect on suspend | hibernate that gnome-power-manager is saving "brightness" rather than "actual_brightness" and restoring that upon resume.

So, I added this little script to /etc/rc.local to set them the same.

brt=`cat /sys/devices/virtual/backlight/acpi_video0/brightness`
abrt=`cat /sys/devices/virtual/backlight/acpi_video0/actual_brightness`
if (( $brt != $abrt )) ; then
echo $abrt > /sys/devices/virtual/backlight/acpi_video0/brightness
fi

Now, on my first suspend the bug does not occur.

I'm not sure if this will be the same for everyone. To find out your own brightness, just search /sys/ with this command:

paul :~$ find /sys/ -iname '*bright*'
/sys/devices/virtual/backlight/acpi_video0/brightness
/sys/devices/virtual/backlight/acpi_video0/actual_brightness
/sys/devices/virtual/backlight/acpi_video0/max_brightness
/sys/devices/pci0000:00/0000:00:1e.0/0000:03:01.1/leds/mmc0::/brightness
/sys/devices/pci0000:00/0000:00:1e.0/0000:03:01.1/leds/mmc0::/max_brightness
/sys/module/video/parameters/brightness_switch_enabled

If your locations are different, then change /etc/rc.local to the different values for yours.

regards,

---

