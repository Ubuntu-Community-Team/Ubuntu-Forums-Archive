---
title: "WakeOnLan will not stay disabled"
date: 2015-10-16
forum: Networking &amp; Wireless
---

### Post by raptir on 2015-10-16
In the past I have always been able to disable WakeOnLan on my laptop by copying /usr/lib/pm-utils/power.d/disable_wol to /etc/pm/power.d/ and modifying it to set WakeOnLan to "d" for all cases. I am now running Xubuntu 15.04 after a few months away from Linux and this is no longer working for me. After making the change to the file wol is still enabled after every reboot. I can disable in manually using ethtool but it's quite a hassle to do this every time. Is there a new procedure I am not aware of? Unfortunately my laptop's BIOS does not have a way to disable it permanently.

---

### Post by Hadaka on 2015-10-16
Hi,  perhaps this method will help.
[http://ubuntuforums.org/showthread.php?t=2042409&page=2](http://ubuntuforums.org/showthread.php?t=2042409&page=2)

---

### Post by raptir on 2015-10-16
Thank you for the response but that 1) doesn't seem to have anything to do with wakeonlan and 2) is from 2012... But using rc.local doesn't work anyway as it does not keep the setting if you put the computer to sleep.

---

### Post by Hadaka on 2015-10-16
Hi, my thought was more along the line of using /etc/fstab
while it is most often used for mounting, it can also be used for
an auto start script,,,as can .bashrc. 
* This may be a fix for you..
[http://boston-linux-unix-general-discussion-list.996279.n3.nabble.com/Unable-to-disable-Wake-On-Lan-td49339.html](http://boston-linux-unix-general-discussion-list.996279.n3.nabble.com/Unable-to-disable-Wake-On-Lan-td49339.html)
Don't discount by the date or os of the link. in the end,,,,the statement from the OP is..
```
I am pleased to report that this problem has been resolved. 

In /etc/network/interfaces: 

#The primary network interface 
iface eth0 lo inet loopback 
        post-up /sbin/ethtool -s eth0 wol d 

Removing 'auto eth0' from this file caused ethtool to run the command 
successfully, to disable wake-on-lan. 

'ethtool eth0' now shows: 

Wake-on: d
```
He also has his EthTool call in .../etc/rc.local

info commands..
you can toggle on/off wol with ethtool and see what the i.d. numbers are for your device
```
cat /proc/acpi/wakeup
```
be sure to stretch the terminal the full width for this one to line up the device i.d. output
```
lspci
```
then look for a match in the acpi output

I also went here looking for a wakeup file,.,but had none,,,nor do i have ethtool
i did however cat some the files i did have and some showed single status such as,,,disabled or enabled
```
/sys/class/net/eth0/device/power
```
good luck

---

### Post by raptir on 2015-10-17
Thanks for the additional follow-up. I tried adding the block to /etc/network/interfaces but it did not work. Adding it to rc.local worked for the first boot but when I put the computer to sleep and woke it back up wol was again enabled (and as it is a laptop, I do put it to sleep regularly).

I was able to resolve it using udev. In /etc/udev/rules.d/70-persistent-net.rules, I added the following to the line that defines eth0:

```
RUN+="/sbin/ethtool -s eth0 wol d"
```

And this persists across reboots and suspend/resume.

Edit: I thought that worked but it seemed to have been a fluke. Again my issue is when I suspend and resume. It works whenever I reboot, but if I put the computer to sleep it's enabled again when I wake it up.

---

### Post by Hadaka on 2015-10-17
Hi, try this. its alot like you were doing..with a couple minor changes.
is this the file and modification you did? see attached...
[ATTACH=CONFIG]265005[/ATTACH][ATTACH=CONFIG]265004[/ATTACH]
i also included the script file for /etc/rc.local
try these again as shown,script and rc.local location as well 
then ..make this change to your pm code. on the "**disable **line only.
```
disable) ethtool -s "${d##*/}" wol **[COLOR=#ff0000]g[/COLOR]**>/dev/null 2>&1;;
```
trade "d for g" at first it doesnt seem logical.,.but it is.

The **enabled** line should of course stay modified..
swap "g for d"
```
enable) ethtool -s "${d##*/}" wol **[COLOR=#ff0000]d[/COLOR]**>/dev/null 2>&1;;
``` this info pilfered from..
[http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/](http://www.hecticgeek.com/2012/09/disabling-wake-on-lan-in-ubuntu-might-save-a-tiny-bit-of-power-on-your-laptop/)

---

### Post by tgalati4 on 2015-10-18
Some network cards need to toggle the WoL switch with each boot.  Perhaps a firmware change or BIOS update changed the behavior.  Try removing the card and reseating.  Some laptops have easy access.  Many don't.  That you will have to research.

---

### Post by raptir on 2015-10-25
> **tgalati4 said:**
> Some network cards need to toggle the WoL switch with each boot.  Perhaps a firmware change or BIOS update changed the behavior.  Try removing the card and reseating.  Some laptops have easy access.  Many don't.  That you will have to research.

Haven't had a BIOS update in a long time and it worked with the script in 14.10 and earlier.

I installed 15.10 though and it seems to disable WOL by default on my system, so I guess this is a non-issue unless a future update changes the behavior again.

---

### Post by raptir on 2015-11-06
So I marked this as unsolved again... I had installed ubuntu-mate 15.10 and did not have an issue. I went back to xubuntu 15.10 (which I want to use) and I am now seeing the problem again.

---

### Post by tgalati4 on 2015-11-06
Perhaps compare the udev rules between MATE and xubuntu and see if there is a difference.  Also compare to your 14.10 distro that worked.  There may be a difference in the sleep settings between the distro's.  Reloading a network module could reset the WoL behavior.  So now you have to go through the sleep scripts as well (/etc/acpi).

---

### Post by raptir on 2015-11-06
Well in Xubuntu 15.10 I'm not seeing any udev rules in /etc/udev. Are they located somewhere else or is udev not really used with systemd here?

---

