---
title: "HELP PLEASE Ethernet Port disabled After Lightning Power Outage *Temporary fix*"
date: 2015-05-14
forum: Networking &amp; Wireless
---

### Post by manny9 on 2015-05-14
Ok so after a lightning strike, everything in my house turned off,the tv got ruined and my ethernet and audio port were disabled on my ubuntu computer,Through some googling i found a temporary fix to get my ethernet port to work again after tethering internet on my phone the fix was using this command in terminal

sudo ethtool -s eth0 speed 10 duplex half autoneg off
**I have to enter this command everytime my computer boots,any permanent fix please?**
This command activated the activity lights on the ethernet port,that were disabled as soon as ubuntu booted, what i need is a permanent fix please,cause there are some limitations,i am a gamer so i stutter alot and lag while playing  games like csgo and league of legends,anyone familiar with ubuntu commands,please help me with a permanent command,i found a post  but it did not work for me i dont know why.


Post that did not work:
[http://column80.com/api.v2.php?a=askubuntu&q=600217](http://column80.com/api.v2.php?a=askubuntu&q=600217)

---

### Post by chili555 on 2015-05-14
Did you try any of the alternatives?```
sudo ethtool -s eth0 speed 100 duplex half autoneg off
sudo ethtool -s eth0 speed 10 duplex half autoneg on
sudo ethtool -s eth0 speed 100 duplex full autoneg off
```When you find the setting that works the best, I suggest you do:```
gksudo gedit /etc/rc.local
```Use nano or kate or leafpad if you don't have the text editor gedit. Right above exit 0, add the line:```
ethtool -s eth0 speed 100 duplex half autoneg off
```Or whatever combination of settings seems to work the best. 'sudo' is not needed here.

Proofread carefully, save and close the text editor. You should be all set.

---

### Post by manny9 on 2015-05-14
Thanks chili,it work's after i reboot :) only the 10 duplex worked but i guess better than nothing

---

### Post by chili555 on 2015-05-14
Glad it's working. Please use thread tools to mark Solved. The searchers will appreciate it.

---

