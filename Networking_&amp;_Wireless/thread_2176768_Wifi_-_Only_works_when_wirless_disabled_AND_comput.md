---
title: "Wifi - Only works when wirless disabled AND computer rebooted"
date: 2013-09-25
forum: Networking &amp; Wireless
---

### Post by James_Munsch on 2013-09-25
Driver information in pastebin below as suggested by Varunendra : ( [http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385) ) ( find all necessary driver / module / card / wifi / ethernet / information ) 

Hardware / Driver / Module information: [http://pastebin.ubuntu.com/6157052/](http://pastebin.ubuntu.com/6157052/)

Summary: 

The only way I have found to work so I can use wifi is to disable wireless, or make sure the "enable wireless" does not have a check next to it ( in the network manager system tray) and reboot. 

[ATTACH=CONFIG]246512[/ATTACH]

If it is enabled when I shutdown, or reboot, It will not work on next boot time. I have tried all kinds of different combinations of [fn] + [wifi key] / hardware switch / sudo rfkill unblock all / logout / login / reboot ... The only way I have found to consistently work is to disable the wifi and reboot.

I am currently using ubuntu-studio 32bit 12.04... but also had the same issue in ubuntu-desktop 32bit 12.04. This issue seems to be resolved in 13.04, so I am sort of curious what has changed.

I am willing to learn how to modprobe and do whatever is necessary to make sure this issue does not occur for other users of the LTS.

Thanks.

---

### Post by Hadaka on 2013-09-25
Hi, is this your router? 
ESSID:"Caffetto 2.4"
if so, even though you have quotes it's still best not
to have a space..perhaps ESSID:"Caffetto_2.4"
would be better, also click Edit connections. Edit your
essid and be sure the "connect automatically" box is checked.
see attached..
[ATTACH=CONFIG]246514[/ATTACH]
make those changes..boot and report back.
thanks.

---

