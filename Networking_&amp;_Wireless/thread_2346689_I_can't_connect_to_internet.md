---
title: "I can't connect to internet"
date: 2016-12-17
forum: Networking &amp; Wireless
---

### Post by porfiliovmj on 2016-12-17
I am trying to setup ubuntu on an old pc but the ethernet will not work. I did ifconfig -a And bity eth0 and eth1 showed up. But for some reason pluging either in will not work. Please help. The version is 14.04 LTS, I'm trying to connect to my router via ethernet. I will post the outputs soon.

---

### Post by Bashing-om on 2016-12-17
porfiliovmj; Hello; Welcome to the forum.

We will need a lot more information in order to resolve .
1) what release did you install ? A lot has changed with the more recent releases
2) What is in the network ? are you connecting to a router ?
3) what is the hardware ? Post back the outputs of terminal commands:
```

sudo lshw -C network
ip link ls
ip route show
ls /sys/class/net
cat /etc/network/interfaces

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Piggy back from a USB is one method to relay the required info; seeing as how at present there is no internet connectivity .
From there we see where you are at, and get a direction to work toward.

[INDENT][INDENT]a tale gets told
[/INDENT][/INDENT]

---

