---
title: "Netgear WG121 USB (v2) - I'm done for?"
date: 2006-10-02
forum: Networking &amp; Wireless
---

### Post by beemonk on 2006-10-02
I've tried everything I can find on the internet....and i just want to cry now, ubuntu has beaten me :(


I have a USB Netgear WG121 USB (v2) wireless card.


    lsusb
Bus 004 Device 007: ID 0846:4210 Netgear, Inc. WG121 Wifi (v2)

    ndiswrapper -v
utils version: 1.9
driver version : 1.24
vermagic: 2.6.15-27-386 preempt 486 gcc-4.0

    ndiswrapper -l
netwg121    driver installed, hardware (0846:4210) present

    iwconfig
lo   no wireless extensions
eth0 no wireless extensions
sit0 no wireless extensions

    ifconfig
lo Link encap:Local Loopback
   <random data>...

    sudo modprobe ndiswrapper
no errors

    sudo depmod -a
no errors

I uninstalled the old ndiswrapper, downloaded the newest one and compiled/made/installed it. I followed the tutorial on blacklisting islsm from these forums and followed that...before i blacklisted islsm, both lights came on on the device, now no lights are on(not sure if thas good or bad) I used the netgear ndis5/netwg121.inf (version 2.0) from the website...



I'm pretty new to Ubuntu, but I have looked all over google and found nothing.](*,) ..If ANYONE has a solution to this...marry me <3 (oh and give me the answer aswell :KS )


update 

    sudo ndiswrapper -m
modprobe config already contains alias directive

    sudo ifup wlan0
SIOCSIFADDR: NO such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up wlan0


---------------------------------
Update
---------------------------------
After de-blacklisting islsm, the lights have come back on the device, and the card is recognised as eth1 in Networking.

---

### Post by alanmzifa on 2006-10-02
Commiserations.

I've been trying off and on since I first started using Ubuntu 4/5 weeks ago to get a WG121 set up too. Closest I came was having it set up temporarily without any security (which isn't acceptable to me where I live).

Now I have 1 Netgear WG121 about to find it's way on to E-bay and I'm struggling to get it's replacement set up, a Safecom USB adapter that uses the Zydas ZD1211B chipset. As far as I know that will be supoported natively in the kernel from 2.6.18. There are threads now for how to get that chipset (in about 60 diferent devices) up and running in the current kernels.

My advice would be to get a Ralink 2500 chipped device. Got one of those for a laptop running Ubuntu and it was relatively easy as drivers are built into Ubuntu and are actively being developed by the OS community as are the Zydas ones.

Of course if someone comes back with a good news story on the WG121....


Either way, good luck!

---

### Post by Pffester on 2007-05-10
Well.. I'm in the same boat. 

..a Ubuntu Newbie whose spent Days following every piece of info I can find and Still not running my Netgear wg121.   I've given up......

What I'm asking for here is a list of wireless cards that I can just plug in and will work. Hell, I'll spend the money.

Anyone? Manufacturers, Model numbers.....

Thanks in advance

---

