---
title: "How i got my datel wifi max usb dongle working as an access point for my wii"
date: 2007-04-25
forum: Networking &amp; Wireless
---

### Post by henrik_daver on 2007-04-25
After months of struggling with different methods, drivers, packages etc. today i finally got my wifi max usb dongle to start acting as an access point. Through it my nintendo wii and ds can connect to the internet. I'm using ubuntu 7.04 (feisty fawn) and an amd64 processor.

First, i followed **part one** of [shof2k's howto on installing the zd1211 driver]("http://ubuntuforums.org/showthread.php?t=288753&highlight=zd1211") . Notice that the driver should be the "zd1211b" one, so in chapter 9, set

```
ZD1211REV_B=1
```

and replace "zd1211" with "zd1211b" in the forthcoming chapters.

i did not edit the /etc/network/interfaces file.

after that, i used ["bfg9000it at spymac dot com"'s guide on using a zd1211 usb dongle as an access point]("http://zd1211.ath.cx/wiki/MasterMode"). note that you have to have the "bridge-utils" and "dhcpcd" packages installed and that all the commands should be written as a superuser.

this worked for me, so now when i want to set up my network i use the terminal and write (as a superuser, so use "sudo -s" before doing this):

```
modprobe -r zd1211b
depmod
modprobe -v zd1211b
modprobe zd1211b
ip link set dev wlan0 up
iwconfig wlan0 mode master key s:Prova
iwconfig wlan0 essid "Prova_AP"
ifconfig eth0 0.0.0.0 up
ifconfig wlan0 0.0.0.0 up
brctl addbr br0
brctl addif br0 eth0
brctl addif br0 wlan0
ifconfig br0 up
dhcpcd br0
```

where "eth0" is my wired connection, "wlan0" is my wireless connection that came up after installing the zd1211b driver, "Prova_AP" is the essid and "Prova" is the key for connecting to the AP.

please don't ask me why this work, i just know THAT it works.

i had to detach my wireless keyboard and mouse, otherwise the wireless connection hung up after a couple of minutes.

if there is anyone who knows how to make this the default settings, so i won't have to struggle with the terminal every time i want to connect my wii and ds to the internet, please notify me!

yours sincerely,
Henrik

---

### Post by yonexFactory on 2007-05-08
When I try

dhcpcd br0, I get this:

dhcpcd.exe: wrong interface name "br0"

Any suggestions?

---

### Post by henrik_daver on 2007-05-14
I get that one too, yet anyway it seems to work. If i type the command once again, I get a message that says something like "the bridge is already open".

---

### Post by yonexFactory on 2007-05-17
Hmmm.... well, I'm still getting the same message no matter what, so any help would be much appreciated.

---

### Post by nobrob on 2007-05-28
Gentoo with USB PSP WIFI MAX (ZD1211 - not B). I've used this dongle as an access point before in Windows so I know it works OK.

When following these instructions I can get to 
```
brctl addif br0 wlan0
```
Where brctl hangs for a while then returns a segmentation fault :(

Could this be because I don't have "ip"? Which package should I emerge (apt-get for you Ubuntu users) to get the ip command?

Thanks :)

---

### Post by nobrob on 2007-05-28
> **yonexFactory said:**
> When I try

dhcpcd br0, I get this:

dhcpcd.exe: wrong interface name "br0"

Any suggestions?

Do you have the TUN/TAP module loaded? [http://edeca.net/articles/bridging/host-kernel.html](http://edeca.net/articles/bridging/host-kernel.html)

---

### Post by nobrob on 2007-06-04
It works!

I managed to compile my kernel in such a way that brctl no longer panics, but then I came across another problem: make sure your USB port is POWERED.

If unsure, use a hub that has its own power supply and try again :)

---

### Post by Miroku on 2007-06-15
> download a working version of the ZD1211 driver from [http://zd1211.ath.cx/download/](http://zd1211.ath.cx/download/).

is there a mirror for the files at that website?

i want to try to get this working so i dont need to login into windows just for my ds
and anyone know if anyone is working on a fix for this 'master mode' problem?

thanks.

---

