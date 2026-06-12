---
title: "Need help with wireless on 7.10"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by randell6564 on 2008-05-17
Hey folks.
It's been a long time sinse I have been here with my stupid questions. So please forgive me if I am repeating myself.

I just installed 7.10 (Gutsy Gibbon) onto my 20Gig IDE slave. (Dual Booting with Windoze), and I cannot remember how to get connected to the internet.

I am using a Linksys WUSB11 ver.2.6 Wireless Antenna, trying to connect to an open network that is made available by the apartment complex that I reside in. The ESSID is 'Rodeway'. It is an Unsecured Network, but for some reason, I still cannot get on the internet.

Could someone please help me configure my network files?  This antenna has always worked before with Ubuntu 7.10.
Thanks!

---

### Post by randell6564 on 2008-05-19
"bump"

---

### Post by superprash2003 on 2008-05-20
so you mean you get connected to the network but the internet still doesnt work?? please post your ifconfig output.. and type ping google.com in the terminal and post output

---

### Post by randell6564 on 2008-05-20
> **superprash2003 said:**
> so you mean you get connected to the network but the internet still doesnt work?? please post your ifconfig output.. and type ping google.com in the terminal and post output
Sorry about the long interval, but I need to go from pc to pc in order to post results, and I have been trying to play around with my /etc/network/interfaces to no avail.
In answer to your question.,No I am not connected to the network. My wusb11 wireless antenna is not even recognized by ubuntu yet. I know it works because it worked last time that I used it with Ubuntu on this system.  I had to configure a network file, but I can't remember which file, or what I had to do to it.

I will post the results of my ifconfig as soon as I can get it and use the computer with the internet connection to post it.
Thanks!

---

### Post by randell6564 on 2008-05-20
Ok, here is the output of:```
iwconfig
```> bigboss@bigboss-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11b  ESSID:"Rodeway"  Nickname:""
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:C5:06:53:50   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality=10/100  Signal level=11/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
Here is the output of ```
ifconfig
```> Interrupt:18 Base address:0xed00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1760 (1.7 KB)  TX bytes:1760 (1.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:06:25:27:49:85  
          inet6 addr: fe80::206:25ff:fe27:4985/64 Scope:Link
          UP BROADCAST RUNNING  MTU:1500  Metric:1
          RX packets:83 errors:0 dropped:0 overruns:0 frame:0
          TX packets:83 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:15267 (14.9 KB)  TX bytes:5090 (4.9 KB)

wlan0:ava Link encap:Ethernet  HWaddr 00:06:25:27:49:85  
          inet addr:169.254.4.131  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING  MTU:1500  Metric:1
Finally, here is the output of:```
gedit /etc/network/interfaces
```> auto lo
iface lo inet loopback




iface eth0 inet dhcp



iface wlan0 inet dhcp
address 172.16.16.189
netmask 255.255.0.0
gateway 172.16.16.1
wireless-essid Rodeway 





auto wlan0
I'm stuck! Does this give any hints of whats wrong?
Thanks!

---

### Post by superprash2003 on 2008-05-21
do you have any other wifi card? cause your ifconfig output shows wlan0 which is normally a wifi card..so ubuntu does recognize it.also please post output of iwconfig

---

### Post by randell6564 on 2008-05-21
> **superprash2003 said:**
> do you have any other wifi card? cause your ifconfig output shows wlan0 which is normally a wifi card..so ubuntu does recognize it.also please post output of iwconfig
Thanks. I already posted the iwconfig output in my last post..#5. :lolflag:

---

### Post by randell6564 on 2008-05-21
I just noticed:> wlan0 IEEE 802.11b ESSID:"Rodeway" Nickname:""
Mode:Managed Frequency:2.462 GHz Access Point: 00:17:C5:06:53:50
Bit Rate:11 Mb/s Tx-Power=15 dBm
Retry limit:8 RTS thr=1536 B Fragment thr=1536 B
Power Managementff
Link Quality=10/100 Signal level=11/100
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
So it is indeed recognized, just like the last time that it was used on this box, but something is missing in some networking file somewhere. :confused:

---

### Post by randell6564 on 2008-05-21
Well, this is silly. And also strange!
For the hell of it, I unplugged my wifi and rebooted. Once I got to the grub screen, I plugged it in again and booted to Ubuntu.  I am now posting via Ubuntu.  YEAHH, it worked!
For some reason, I have to reset my wifi every time that I switch from Ubuntu to Windows, and vise versa. Now that I'm online from my Linux desktop, I will not be able to access the internet from my Windoze desktop after rebooting unless I first unplug my wifi in order to reset it. (Thank God it's USB!)

Anyway, Thanks people!  Hope this helps.

---

