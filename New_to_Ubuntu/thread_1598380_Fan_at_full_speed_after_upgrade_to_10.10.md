---
title: "Fan at full speed after upgrade to 10.10"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by Sjeik on 2010-10-16
I got an NetBox-nT330i (Intel Atom Dual Core 330, nVIDIA MCP7A-ION chipset) which functions as a HTPC (XBMC on ubuntu). This worked great on ubuntu 10.04. When I upgraded to 10.10 and was asked to reboot the fan on my NetBox makes a terrible noise (I didn't even know the fan could run this fast).

These are the things I tried:
```
tom@NetBox:~$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +22.0Â°C  (crit = +90.0Â°C)

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +25.0Â°C  (crit = +90.0Â°C)
```
```
tom@NetBox:~$ fancontrol
Loading configuration from /etc/fancontrol ...
Error: Can't read configuration file
```
```
tom@NetBox:~$ sudo pwmconfig
[sudo] password for tom:
# pwmconfig revision 5770 (2009-09-16)
This program will search your sensors for pulse width modulation (pwm)
controls, and test each one to see if it controls a fan on
your motherboard. Note that many motherboards do not have pwm
circuitry installed, even if your sensor chip supports pwm.

We will attempt to briefly stop each fan using the pwm controls.
The program will attempt to restore each fan to full speed
after testing. However, it is ** very important ** that you
physically verify that the fans have been to full speed
after the program has completed.

/usr/sbin/pwmconfig: There are no pwm-capable sensor modules installed
```
```
tom@NetBox:~$ sudo sensors-detect
# sensors-detect revision 5818 (2010-01-18 17:22:07 +0100)
# System: Foxconn nT-330i
# Board: To be filled by O.E.M. To be filled by O.E.M.
... stukje weggehaald ...
Now follows a summary of the probes I have just done.
Just press ENTER to continue:

Driver `coretemp':
  * Chip `Intel Atom thermal sensor' (confidence: 9)

To load everything that is needed, add this to /etc/modules:
#----cut here----
# Chip drivers
coretemp
#----cut here----
If you have some drivers built into your kernel, the list above will
contain too many modules. Skip the appropriate ones!
```
I put this in /etc/modules but this didn't help either.
I also checked for running processes with top. There were none.

```
tom@NetBox:~$ ls /etc/fancontrol
ls: cannot access /etc/fancontrol: No such file or directory
```
I updated my bios, but that didn't help. It doesn't have an option like cool 'n quiet.

I also tried a Live disk of 10.10. Miracously the problem didn't excist there. I checked if fancontrol excisted there, but it didn't. The other commands don't work either. Only pwmconfig gives another error ("/usr/sbin/pwmconfig: No sensors found! (modprobe sensor modules?)").

Anyone got any idea how I can fix my fan-speed? It is driving me nuts :(

---

### Post by no2498 on 2010-10-16
fix the problem do not change fan speed's
open a terminal type in htop it tells you how to install it
after install type htop
see what is running to make it hot
now fix it

hope this helps

---

### Post by Sjeik on 2010-10-16
> **no2498 said:**
> fix the problem do not change fan speed's
open a terminal type in htop it tells you how to install it
after install type htop
see what is running to make it hot
now fix it

hope this helps
Hmm, don't think so. There are no processes running that uses a lot of CPU I think. This is what htop says:
```
  1  [|                         0.6%]     Tasks: 209 total, 1 running
  2  [||                        4.4%]     Load average: 0.46 0.23 0.13
  3  [||                        1.8%]     Uptime: 02:54:45
  4  [                          0.0%]
  Mem[||||||||||||||||||||447/1754MB]
  Swp[                      0/4692MB]

  PID USER     PRI  NI  VIRT   RES   SHR S CPU% MEM%   TIME+  Command
 6691 tom       20   0 19680  1496  1104 R  4.0  0.1  0:02.25 htop
 1788 tom       20   0  371M 28272 15068 S  0.0  1.6  1:32.35 transmission
 1787 tom       20   0  371M 28272 15068 S  0.0  1.6  2:35.62 transmission
 5675 tom       20   0  700M  114M 32900 S  0.0  6.5  0:01.18 /usr/lib/firefox-3
    1 root      20   0 23884  2012  1304 S  0.0  0.1  0:01.56 /sbin/init
  386 root      20   0 16964   628   456 S  0.0  0.0  0:00.24 upstart-udev-bridg
  392 root      16  -4 17304  1152   356 S  0.0  0.1  0:00.23 udevd --daemon
  462 root      18  -2 17168   992   316 S  0.0  0.1  0:00.00 udevd --daemon
  463 root      18  -2 17168   992   316 S  0.0  0.1  0:00.00 udevd --daemon
  795 root      20   0 93468  4788  3752 S  0.0  0.3  0:00.07 smbd -F
  809 syslog    20   0  123M  1932  1044 S  0.0  0.1  0:00.02 rsyslogd -c4
  958 syslog    20   0  123M  1932  1044 S  0.0  0.1  0:00.04 rsyslogd -c4
  959 syslog    20   0  123M  1932  1044 S  0.0  0.1  0:00.02 rsyslogd -c4
 6043 syslog    20   0  123M  1932  1044 S  0.0  0.1  0:00.00 rsyslogd -c4
F1Help  F2Setup F3SearchF4InvertF5Tree  F6SortByF7Nice -F8Nice +F9Kill  F10Quit

```

---

### Post by no2498 on 2010-10-16
odd on my 2 computers it was fire fox
see if getting opera helps

[http://www.opera.com/](http://www.opera.com/)

flash worked in opera before it did in/on fire fox any way

---

### Post by AndyM3 on 2010-10-16
Try running PowerTOP, it should fix it if it's a power management error.
```
sudo apt-get install powertop
sudo powertop
```
You'll get a list of the top wakeup causes on your system and it'll prompt you to do some changes (don't worry, you just have to press keys when prompted).

---

### Post by Quackers on 2010-10-16
I think this can occasionally be a ACPI problem.

---

### Post by cariboo on 2010-10-16
Atom cpu's don't need a fan, so it is the gpu fan that is making all the noise, what video driver are you using?

---

### Post by holiday on 2010-10-16
I had a fan problem on my Vaio until I installed the proprietary video driver. Don't ask me why, but the video driver was a boss in the fan control. 

So check your drivers. Who knows who's in charge?  On the system menu bar, System/Administration/Hardware Drivers. See if anything comes up.

---

### Post by Sjeik on 2010-10-16
> **cariboo907 said:**
> Atom cpu's don't need a fan, so it is the gpu fan that is making all the noise, what video driver are you using?
I got the proprietary nvidea driver, version 260.19.06.
I don't see the System/Administration/Hardware Drivers option. I do see the Additional drivers option. There I can choose te proprietary nvidea driver (which is recommended).

---

### Post by Sjeik on 2010-10-17
Anyone got any idea? I installed nvclock and tried to change the fanspeed with that program. Didn't work (Error: adjustment of the fanspeed isn't supported on your type of videocard!) :(

---

### Post by ArigornStrider on 2010-12-02
Hey Sjeik,

I just got this nettop/netbox in today and so far have had no issues with it. I'm installing Ubuntu Netbook 10.10 on it and the fan hasn't spun up yet (very low hum in the background of it just running at it's lowest speed). My setup is a little odd, as instead of installing a SATA hard drive, I just stuck an 8GB SDHC card in the front and am installing to that (frees up space inside for ventilation and removes the hard drive, which can be one of the hottest parts in modern computers next to the CPU/GPU).

Anyway, I'll be putting it through it's paces and seeing how well it will run openGL apps like Minecraft and will let you know if I find anything out.

-ArigornStrider

---

### Post by clarknova on 2011-01-22
Exact same problem here. Zotac ION-itx board with a 4-pin CPU fan header connected to a 120mm 4-pin pwm fan. pwmconfig and nvcontrol won't touch it.

Maybe this page is useful?
[http://www.lm-sensors.org/wiki/Devices](http://www.lm-sensors.org/wiki/Devices)

It says the winbond W83L771W/G is used in many Zotac boards. Could be different depending on your board, I guess. Not sure what is meant by "you can force chip type to lm86". I could just wait for 2.6.37 I guess, I don't really have time to mess with it right now.

---

### Post by lukelang21 on 2011-03-11
I am having a similar problem on my HP dv7 ([http://ubuntuforums.org/showthread.php?t=1702289](http://ubuntuforums.org/showthread.php?t=1702289)) I have avoided updating my proprietary driver for my for my ATI graphics driver because it crashes my system and I have to reinstall every thing after and my computer works fine with out it. Any help? Thanks.

---

### Post by Blaise Descartes on 2011-04-15
I just installed ubuntu 10.10 64-bit on a brand new HP G62-b32eo, and the fan was at high speed and causing a terrible noise until I installed an ATI driver for the graphics card. I install the ATI driver through the following GNOME menu-commands: System->Administration->Additional Drivers

The program 'Additional Drivers' suggested that I install the ATI driver, and after a reboot the fan is now running at normal speed.

---

