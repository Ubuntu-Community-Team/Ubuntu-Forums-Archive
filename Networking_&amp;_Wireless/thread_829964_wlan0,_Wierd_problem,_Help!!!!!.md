---
title: "wlan0, Wierd problem, Help!!!!!"
date: 2008-06-15
forum: Networking &amp; Wireless
---

### Post by The Martian on 2008-06-15
Hi All
I just recently installed Ubuntu, onto my Samsung Q35 laptop, having messed around with Red Hat 6 or 7 some time ago, I'm not overly experienced, had some teething troubles with sound and wireless, but have got everything working now, but I am having a strange problem. When I try to bring up or down the interface wlan0, with ifup/ifdown, it will not work, although the wireless is working fine. The output is:

martin@linuxlaptop1:~$ sudo ifdown wlan0
[sudo] password for martin: 
ifdown: interface wlan0 not configured

Yet trying the command ifconfig <intrfce> down does work, then using the command ifconfig <intrfce> up, brings it back up, as far as ifconfig knows in the terminal, but it still says disconnected in the network manager connection properties, in the GUI, and does'nt come back until I disable/re-enable wireless in the notification area aplet. also if I try to configure either eth0, or wlan0 in the network manager connection properties configure tab, after asking for my passwd then comes up with "interface does not exist".

BTW ifup/ifdown works with eth0.
I also installed Kismet and edited the conf file with wlan0, and it seems to be working fine.

Does anybody have any idea???
What configs need editing???
Any clues at all????

Thanks in advance.
                      The Martian

---

### Post by zgornel on 2008-06-15
Edit /etc/network/interfaces and put in the following lines:
```
auto wlan0
iface wlan0 inet dhcp
```
Should work.

---

### Post by The Martian on 2008-06-15
HiYa mate.
Thanks for the reply.
Funnily enough I asked if this needed inserting in an earlier post.
I just tried it, and although the commands ifup/ifdown worked, wireless networking woul'nt work at all, no wireless network enable came up in the network manager aplet, and I could not get it to enable at all, even though it was supposedly there when I ran, ifconfig.
Has anyone any further ideas?????
Come on you Linux gurus give us a hand!!!!
TIA
         The Martian

---

### Post by zgornel on 2008-06-16
Hmm.Leave the modifications in /etc/network/interfaces there and check that wireless in ON, meaning (this might sound stupid but sometimes people forget to turn it on :D ). Then, not using the network manager check for wireless networks (the network manager creates sometimes problems). Do a ```
iwlist wlan0 scanning
``` and see if any wireless networks are reported.

---

### Post by The Martian on 2008-06-17
Hiya Mate
Yeh it works fine, it reports any in range even with network manager running. athough I can't do it if I leave the config as suggested, networking does'nt work in that config.
I think you may have missunderstood my Q, everything works fine, its just that the command does'nt work on wlan0, and the config button in network MONITOR, when pressed after asking for psswd comes up with "the interface does not exist", even though any working interfaces show up in it. network monitor does also show any working interfaces, and reports sent/recieved and signal OK.
I personaly think its just some small config prob,but I don't know where to go from here.
Thanks
                   The Martian

---

### Post by zgornel on 2008-06-17
Well, it is strange. If you are positive that making the modifications in the 'interfaces' file makes the wireless unusable, leave it as it is :D .

---

### Post by Ayuthia on 2008-06-17
> **The Martian said:**
> Hiya Mate
Yeh it works fine, it reports any in range even with network manager running. athough I can't do it if I leave the config as suggested, networking does'nt work in that config.
I think you may have missunderstood my Q, everything works fine, its just that the command does'nt work on wlan0, and the config button in network MONITOR, when pressed after asking for psswd comes up with "the interface does not exist", even though any working interfaces show up in it. network monitor does also show any working interfaces, and reports sent/recieved and signal OK.
I personaly think its just some small config prob,but I don't know where to go from here.
Thanks
                   The Martian

I am going to ask a couple of possibly dumb questions.  What do the following commands say about your wireless:
```
ifconfig
lshw -C network
```
Is it possible that your wireless name is not wlan0?

---

### Post by zgornel on 2008-06-17
Normally, the Samsung Q35 uses an intel i3945 abg wireless adapter which is identified as wlan0.

---

