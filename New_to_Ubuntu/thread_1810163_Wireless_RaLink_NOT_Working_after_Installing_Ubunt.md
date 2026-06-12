---
title: "Wireless RaLink NOT Working after Installing Ubuntu 10.04.2 LTS on HP Pavilion dv6"
date: 2011-07-22
forum: New to Ubuntu
---

### Post by NCMS on 2011-07-22
[FONT=&quot][SIZE=2]**[COLOR=SandyBrown]MY SYSTEM DETAILS;[/COLOR]**
[B]HP Pavilion dv6

cat /etc/issue[/B]
Ubuntu 10.04.2 LTS

[B]sudo lspci | grep Wirless
[/B]02:0.0 Network controller:  RaLink RT3090 Wireless  802.11n  1T/1R  PCIe
 [/SIZE][/FONT][SIZE=2]
**[FONT=&quot]uname  -a[/FONT]**
[/SIZE]      [FONT=&quot][SIZE=2]2.6.32-28-generic #55-Ubuntu SMP Mon Jan 10 21:21:01 UTC 2011 i686 GNU/Linux


The Wireless is NOT working or can NOT be enabled or started on my [/SIZE]
[/FONT]

---

### Post by NCMS on 2011-07-22
[SIZE=2]I am posting the output of  iwconfig   if it helps in any way 

#  **iwconfig**
lo          no Wireless extensions.

wlan0     RT2860 Wireless   ESSID:""   Nickname:"RT2860STA"
             Mode:Auto   Frequency=2.412 GHz   Access Point:  Not-Associated
             Bit Rate: 1 Mb/s
             RTS thr:off    Fragment thr:off
             Link Quality=10/100  Signal Level:0 dBm  Noise level:-87 dBm
             Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
             Tx excessive retries:0   Invalid misc:0    Missed beacon:0

eth0       no wireless extensions.

pan0      no wireless extensions.


[/SIZE]

---

### Post by gandaran on 2011-07-22
there are many threads on the network and wireless forum section about the RaLink RT3090 chipset, just use the forum search box, see if this one helps.
 [http://ubuntuforums.org/showthread.php?t=1490123&highlight=RaLink+RT3090](http://ubuntuforums.org/showthread.php?t=1490123&highlight=RaLink+RT3090)

---

### Post by NCMS on 2011-07-22
[SIZE=2]MANY THANKS Gandaran .. :popcorn:

The problem [COLOR=Red]**solved **[/COLOR]by using these 3 commands;
[B]
sudo  mkdir -p /etc/Wireless/RT2860STA/

[/B][/SIZE][B][SIZE=2]sudo  [/SIZE][SIZE=2]touch /etc/Wireless/RT2860STA/RT2860STA.dat

[/SIZE][SIZE=2]sudo  [/SIZE][/B][SIZE=2][B]service network-manager restart 			 		
[/B]


Thanks to **[gargok]("http://ubuntuforums.org/member.php?u=1092353")** in the thread you have sent ..[/SIZE]

[SIZE=2]
[/SIZE]

---

