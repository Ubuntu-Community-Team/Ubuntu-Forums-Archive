---
title: "Laptop_mode not enabling"
date: 2009-10-18
forum: New to Ubuntu
---

### Post by humphreybc on 2009-10-18
Hi guys, for some reason laptop_mode on my Toshiba isn't enabling. I first noticed something was wrong when the brightness and CPU Freq wasn't adjusting when I unplugged my laptop. I've also been getting shorter battery life. I looked into it some more, and it turns out laptop mode was giving me an error.

Here's some relevant terminal code:

```

benjamin@benjamin-laptop:~$ sudo laptop_mode
[sudo] password for benjamin: 
Laptop mode disabled, active
benjamin@benjamin-laptop:~$ sudo laptop_mode status
Mounts:
   /dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro,commit=600)
   tmpfs on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
   proc on /proc type proc (rw,noexec,nosuid,nodev)
   sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
   varrun on /var/run type tmpfs (rw,nosuid,mode=0755)
   varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
   udev on /dev type tmpfs (rw,mode=0755)
   tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev)
   devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=620)
   fusectl on /sys/fs/fuse/connections type fusectl (rw)
   lrm on /lib/modules/2.6.28-15-generic/volatile type tmpfs (rw,mode=755)
   /dev/sdb1 on /mnt/media type ext4 (rw,errors=remount-ro,commit=600)
   securityfs on /sys/kernel/security type securityfs (rw)
   binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
   gvfs-fuse-daemon on /home/benjamin/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=benjamin)

Drive power status:
   
   /dev/sda:
    drive state is:  active/idle
   
   /dev/sdb:
    drive state is:  active/idle

(NOTE: drive settings affected by Laptop Mode cannot be retrieved.)

Readahead states:
   /dev/sda1: 3072 kB
   /dev/sdb1: 3072 kB

Laptop Mode Tools is NOT allowed to run: /var/run/laptop-mode-tools/enabled does not exist.

/proc/sys/vm/laptop_mode:
   2

/proc/sys/vm/dirty_ratio:
   60

/proc/sys/vm/dirty_background_ratio:
   1

/proc/sys/vm/dirty_expire_centisecs:
   60003

/proc/sys/vm/dirty_writeback_centisecs:
   60003

/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_cur_freq:
   800000

/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_max_freq:
   2201000

/sys/devices/system/cpu/cpu0/cpufreq/cpuinfo_min_freq:
   800000

/sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_cur_freq:
   800000

/sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_max_freq:
   2201000

/sys/devices/system/cpu/cpu1/cpufreq/cpuinfo_min_freq:
   800000

/sys/devices/system/cpu/cpu0/cpufreq/scaling_governor:
   ondemand

/sys/devices/system/cpu/cpu1/cpufreq/scaling_governor:
   ondemand

/proc/acpi/button/lid/LID/state:
   state:      open

/proc/acpi/ac_adapter/ADP0/state:
   state:                   off-line

/proc/acpi/battery/BAT0/state:
   present:                 yes
   capacity state:          ok
   charging state:          discharging
   present rate:            3084 mA
   remaining capacity:      3645 mAh
   present voltage:         15000 mV

/sys/class/power_supply/ADP0/online:
   0

benjamin@benjamin-laptop:~$ 

```

So the error seems to be 

"Laptop Mode Tools is NOT allowed to run: /var/run/laptop-mode-tools/enabled does not exist."

Sure enough, there is no 'enabled' file in that directory. Is there a way I can re-install/repair laptop_mode?

Attached is my laptop_mode.conf file (converted to .txt)

---

### Post by igknighted on 2009-10-18
Laptop mode only has to do with the way the system writes to your hard drive.  There are pros and cons to using it, most notably that if you were to leave your computer on 24/7, you would wear out the hard drive inside of a year.  However, it can save battery and, for SSD users, limit write cycles to prolong the life of your HD.

So I guess what I am saying is, do some reading on laptop mode before deciding if you do want to use it (this depends a lot on the way you use your computer), and if so how you want to use it.  Then someone could help you to turn on the parts that would be relevant and not accidentally damage your system.

If you are having issues with brightness and CPU frequency, these are ACPI functions.  Did you have to use a 'noacpi' or 'acpi=off' boot parameter?  These would disable that info.  Also, not all ACPI functions are supported on all laptops, so it is possible that yours may just be incompatible.

---

### Post by humphreybc on 2009-10-18
> **igknighted said:**
> Laptop mode only has to do with the way the system writes to your hard drive.  There are pros and cons to using it, most notably that if you were to leave your computer on 24/7, you would wear out the hard drive inside of a year.  However, it can save battery and, for SSD users, limit write cycles to prolong the life of your HD.

So I guess what I am saying is, do some reading on laptop mode before deciding if you do want to use it (this depends a lot on the way you use your computer), and if so how you want to use it.  Then someone could help you to turn on the parts that would be relevant and not accidentally damage your system.

If you are having issues with brightness and CPU frequency, these are ACPI functions.  Did you have to use a 'noacpi' or 'acpi=off' boot parameter?  These would disable that info.  Also, not all ACPI functions are supported on all laptops, so it is possible that yours may just be incompatible.

Hmm okay, fair enough. My brightness seems to be changing when I unplug now... but for some reason when I boot up my computer on battery, the CPU Frequency Scaling defaults to "performance" when in actual fact it should be "powersave" on battery. I've tried looking in gconf-editor for a default value when on battery/AC power, but couldn't find anything. Would you know anything about that?

Also, when I shutdown or restart, 9 times out of 10 my computer will hang until I press Ctrl+Alt+Delete where it tells me it's "stopping all md devices" and then restarts. If I want to shutdown I normally have to hold down the power button.

Is there a way to fix this? Or will it be fixed in Karmic? I know they've done a lot of work on boot/shutdown experience.

---

### Post by laceration on 2009-10-19
What of this acpi?  I have a Toshiba A18 with the Karmic beta and I know acpi is not off because brighten/darken the screen with the fn key works.  But with Karmic the screen will not blank and screensaver will not activate.  If I plug in the AC or disconnect it the computer shuts down.

I also discovered all the acpi modules source, some specific to Toshiba and install scripts, but can't find any guides to them(thats how I got here).  There are even hibernate routines there --  Hibernate this Toshiba? -- if that was not an impossible dream...

How do you configure/tweak acpi?

---

