---
title: "Wireless Frustration!!!"
date: 2007-01-09
forum: Networking &amp; Wireless
---

### Post by bd_adams on 2007-01-09
Ok I'm trying to get my wmp54g setup but I'm having the following problem. I reinstalled 6.06 LTS because I was told that everything should work out of the box. I found my wireless card and setup the SSID and WEP password. I then activated. I could not surf any web pages. I decided to reboot. When I did I now get hung on configuring network interfaces. It was suggested to boot from the livecd and mount my harddrive however when I try I'm told it's not a removable device. I'm very green when it comes to Linux so I'm not sure of the command line command to do this. I'm trying to get to /etc/network to edit the interfaces file as follows:

auto lo
iface lo inet dhcp

auto eth0
iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp

If anyone can explain how to mount my harddrive I'd greatly appreciate it or if anyone has any other ideas I'd greatly appreciate that too because I'm about to say the hell with it and move the router in the other room and just let the windows device go wireless.

Thanks in advance for your time,

BA

---

### Post by scrooge_74 on 2007-01-09
Hi boot from the iive CD, then open a terminal then

sudo mkdir /mydrive

for the next step you need to mount your drive which probably is /dev/hda1

sudo mount -t ext3 /dev/hda1 /mydrive

with that you should have the drive mounted 

then do sudo nano /mydrive/etc/network/interfaces

You could also try when booting to go into GRUB menu and boot in recovery mode

---

### Post by bd_adams on 2007-01-09
Ok here is what I find in my /etc/network/interfaces file:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface ra0 inet dhcp
wireless-essid XXXXXXXX
wireless-key XXXXXXXX

auto ra0

So I #'d out all but the lo and eth0 and was able to log in. I found it weird that the last entry had the auto ra0 under the iface so I changed the file and put the auto ra0 in front of the iface line and took out the #'s and tried booting. I made it past the configuring network interfaces. However when I put in my username and password it would then hang.

I booted from livecd and mounted my HD and corrected this but I'm not sure what to do next.

Any suggestions?

---

### Post by scrooge_74 on 2007-01-09
next time you do a normal boot, check what ifconfig says about your network cards.

You seem to have to many entries in /etc/network/interfaces

lo is the loop
eth0 is the wired card
and one of the others shoud be your wireless card, I just dont know which one

---

### Post by bd_adams on 2007-01-09
iwconfig:

lo          no wireless extensions

eth1      no wireless extensions

ra0        RT61 Wireless ESSID: ""
             Mode: Auto  Channel:0
             RTS thr=0 B  Fragment thr=0 B
             Link Quality:0  Signal level:0 Noise level:113
             RX invalid nwid:0  RX invalid crypt:0  RX invalid frag:0
             TX excessive retries:0  Invalid misc:0 Missed beacon:0

eth0       no wireless extensions

sit0        no wireless extensions

---

### Post by scrooge_74 on 2007-01-09
So your wireless card is ra0 it would seem.

Did you tried ifconfig or ifconfig ra0 to see what it says about the connection

---

### Post by bd_adams on 2007-01-09
After going to Admin-Networking and enabling ra0 and configuring and activating.

ifconfig ra0

Link encap : Ethernet  HWaddr "xx : xx : xx : xx : xx : xx"
inet6 addr : "xxxx :: xxx : xxxx : xxxx : xxxx/xx" Scope : Link
UP BROADCAST RUNNING MULTICAST  MTU: 1500 Metric:1
RX Packets:596 errors:0 dropped:0 overruns:0 frame:0
TX Packets:1811 errors:0 dropped:0 overruns:0 carrier:0
Collisions:0 txqueuelen:1000
RX bytes:48757 TX bytes: 0 (0.0 b)
Interrupt:209

---

### Post by scrooge_74 on 2007-01-09
seems to be working ok, can you connect to the net using it?

---

### Post by bd_adams on 2007-01-09
Nope looks like I might be having a signal problem. Some noise interference. Not sure what it could be. Maybe too many fans going who knows.

---

### Post by bd_adams on 2007-01-09
Also, do I have to deactivate my wireless in Networking prior to rebooting each time? I rebooted and once again I get to enter my username and password and hang.

---

### Post by scrooge_74 on 2007-01-09
It seems you have some other issues with your card 

Did you try any of the howto's on wireless?

[https://help.ubuntu.com/community/WifiDocs/WPAHowTo](https://help.ubuntu.com/community/WifiDocs/WPAHowTo)
[http://www.ubuntuforums.org/showthread.php?t=202834](http://www.ubuntuforums.org/showthread.php?t=202834)

There is another reference at the end of this thread
[http://www.computing.net/linux/wwwboard/forum/28880.html](http://www.computing.net/linux/wwwboard/forum/28880.html)

    [http://www.linuxquestions.org/questions/showthread.php?t=163937](http://www.linuxquestions.org/questions/showthread.php?t=163937)


I basically have ran out of ideas on how to help you

---

### Post by bd_adams on 2007-01-10
I haven't tried any of the how to's. I started with the ndiswrapper and was told that with my 6.06 LTS everything should work out of the box. So that's where I started. It's just weird that I can connect but my signal strength and noise seem to be a problem now. I had this same card in a Win2kPro machine and it worked like a champ. I'm going to move the router this evening and see if that helps.

---

### Post by scrooge_74 on 2007-01-10
Could be the drivers, remember that the drivers are originally for windows.  Most of the time it will depend on the brands, my wireless card on this thosiba worked no problem.  The modem I had to download the correct set of drivers.  The Nvidia was suppose to be current, but it was a legacy driver.

So is a little of everything, you should check the howtos because if your card is working and can detect the lan it may just be configuration

---

