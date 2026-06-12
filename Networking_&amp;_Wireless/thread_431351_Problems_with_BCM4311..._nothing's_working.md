---
title: "Problems with BCM4311... nothing's working?"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by Kumah on 2007-05-02
Just got this Compaq Presario C500 laptop, and I've been trying to get Ubuntu Feisty Fawn to work properly. 

My primary problem seems to be with the wireless card, a BCM4311. I've tried ndiswrapper and fwcutter but neither have worked. Is there anyone who can for lack of better words, hold my hand through this and help me out?

---

### Post by jubilee33 on 2007-05-03
I have a similar card.  It's BCM4311 in Windows and somehow is shown as BCM4310 UART in ubuntu.  Fwcutter used to work in both dapper (6.06) and edgy (6.10) but I haven't got it to work stably in feisty.  The best I got is to have a seemingly working connection without internet access.

---

### Post by pichulines on 2007-05-03
I'm in the same situation... I've tried fwcutter and ndiswrapper, this worked in Edgy but not in Feisty. Although it turns on the wireless led and detects some wireless networks, it cannot connect to anyone.

It's a pity that Feisty has not improved the wireless support, or at least remain in the same state. As I read in the forums, lot of people have problems with wireless in Feisty, I hope they  release new uptades soon to solve the problem.

---

### Post by Kumah on 2007-05-03
Finally got the driver to install with ndiswrapper: 
"bcmwl5 : driver installed"

However now it won't detect my wireless card at all: 

lspci displays:
06:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)

but ifconfig shows:
eth0      Link encap:Ethernet  HWaddr 00:16:D4:A3:40:4E  
          inet addr:192.168.1.105  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:d4ff:fea3:404e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:998 errors:0 dropped:0 overruns:0 frame:0
          TX packets:856 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:992598 (969.3 KiB)  TX bytes:92692 (90.5 KiB)
          Interrupt:20 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

iwconfig shows: 
lo        no wireless extensions.

eth0      no wireless extensions.


how can I get it to detect my card again? :confused: 


ifconfig:

---

### Post by jck on 2007-05-03
Taken with a grain of salt...because, I'm no expert...but...these are the things to try if you're going to be running on a desktop, in my opinion. 

And as always when experimenting with your system:

** Please backup your files before modifying/installing over them as not to lose anything you want to keep/reinstall.**

1) Get Ubuntu/Kubuntu 7.04 x86 32-bit desktop release and install it

2) go into your /etc/network/interfaces file and comment out everything but your a) lo entry, and b) your wlan0 entry  (if you're going to use wireless, there is not a reason to have ETH0 wired networking)

3) Follow Wieman's examples of how to configure your wlan0 in the /etc/network/interfaces file for your specific type of wireless and encryption.  [Wieman01's How-to on Wireless Security on Ubuntu forums]("http://ubuntuforums.org/showthread.php?t=318539")

3) go to /etc/modprobe.d/blacklist and put in at the bottom:

blacklist bcm43xx

4) reboot

5) once back in, open a console window and do **ifconfig** and **iwconfig** and confirm that wlan0 is active and ticking.

6) do a **iwlist scan** and see if your cards are seeing any wireless points.  If so, your wireless card should now be working.

7) go to your task bar...and right click NetworkManager and set it not to autostart and close it (I've found Network Manager doesn't help me one bit after I have the card already working.  You can always start it again if needed from the menus)


Hope this helps.  I didn't have to ndiswrapper anything on my laptop which is a Dell Inspiron 1501 that has a Broadcom 4311 802.11g card.

Good luck.

---

