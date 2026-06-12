---
title: "What does [13979.066076] ERROR @wl_cfg80211_scan :WLC_SCAN error (-22) mean?"
date: 2014-01-01
forum: Networking &amp; Wireless
---

### Post by cigtoxdoc on 2014-01-01
I did an update this afternoon on the Ubuntu side of my DELL Vostro 3500 laptop.  When it rebooted is started giving number as in the title bu much smaller.  Several times a minute, the numbers increase by around 60.  The Wifi driver was not in use.  I think that fsck is working.  Is that correct? The Crucial 256 GB SSD is split about 50/50 Ubuntu 12.04/Win XP Pro SP3.

What is going on?  Will it stop by itself?  Will it hurt the Win XP side (mission critical part on business is still on XP due to KineticD being more relaible than SpiderOak).  If it is still doing the same thing come sunrise, how do I stop it other than turning PC off.  How do I reboot into Ubuntu w/o getting the current nonsense?

The number is now 14458.239978.

John

---

### Post by r3dd on 2014-01-01
[COLOR=#000000][FONT=verdana]Here is the solution that I found in another thread.


Hi, the Broadcom STA driver does not work with your card, all being well this should get you up and running.
[/FONT][/COLOR][COLOR=#000000][FONT=verdana]
With an ethernet cable plugged in run these commands in a terminal please.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]```
sudo apt-get purge bcmwl-kernel-source
```
 to remove the non-working one. Then run [/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]```
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer
```[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]It might be easier to copy and paste the commands. [/FONT][/COLOR][COLOR=#000000][FONT=verdana]When the terminal has finished wait a few seconds for the dust to settle and check the Network-Manager icon at the top of the screen for any available networks. [/FONT][/COLOR][COLOR=#000000][FONT=verdana]If none show just reboot the machine and all should be working.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Let us know how it goes.[/FONT][/COLOR]

[COLOR=#000000][FONT=verdana]Thank you.[/FONT][/COLOR][COLOR=#000000][FONT=verdana]

[/FONT][/COLOR][http://ubuntuforums.org/archive/index.php/t-2159331.html](http://ubuntuforums.org/archive/index.php/t-2159331.html)

---

### Post by cigtoxdoc on 2014-01-02
Thank you for your message.  Unfortunately, it did not solve my problem.  First, to do what you suggested requires Ethernet drivers loaded.  If you cannot get the system to boot into Ubuntu, no drivers.  Second calling up the backup version of the OS, only will get you the root prompt.  I took a look at the xorg.conf, and it had been trashed, so I remounted file system as rw and renamed it.  Third, I can still get the Win XP to load.  The Wifi hardware is DW1520 Wireless-N Half-Mini Card.  The Win XP driver is Broadcomm.  Fourth, what I really need help on is keeping "ERROR @wl_cfg80211_scan :WLC_SCAN error (-22)" from interfering with the boot.

Please remember the only thing I get on boot is the root prompt which I need to change to read/write.

Is there a set of bailout instructions for users who get in this situation?

John

---

