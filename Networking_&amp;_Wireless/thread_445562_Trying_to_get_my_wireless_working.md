---
title: "Trying to get my wireless working"
date: 2007-05-16
forum: Networking &amp; Wireless
---

### Post by waylow on 2007-05-16
hey everybody,
I am new to Linux - DL a few different OS's over the past few weeks and tested them in a virtual machine
was really happy with ubuntu and ubuntu studio and I ended up installing ubuntu studio as a real dual boot yesterday

I didn't have anyproblems getting my wireless card connected to the router when it was set up as a virtual machine because it thought it was hardwired to the internet

But now I have a great new OS that can't connect - it uses WPA security not WPE
I have been messing around for the past 6 hrs trying a lot of different things from different post but now I think I have made it worse - if that is possible as It wasn't working when I started


I am running an AMD Athlon 64 bit - 3200 - 
I gig Ram

the network card is 
Linksys WMP54g 
Chip set: Broadcom BCM4306  802.11/g Wireless LAN Controller (rev 03)
driver: bcm43xx
Driver version (same as the kernel): 2.6.20-15 low latency 

don't know what I have to do to get a WPA option to appear in the network setting??

didn't think it was going to be this hard cos it work awesome as a virtual machine

any help for this Linux noob would be greatly apprichiated

thanks

---

### Post by grayfood on 2007-05-16
hello

I followed this and got my broadcom 43 working.

I use Wicd to connect to my WPA router as I could not get Network Manager to work.

Alternatively connect to router via another machine and disable security if WPA is the problem

good luck

---

### Post by waylow on 2007-05-16
i will try and see if Wicd works

don't know if WPA is the problem but it is my brothers network not mine so I can't turn WPA off till he gets home tomorrow

---

### Post by waylow on 2007-05-16
couldn't get wicd to see the network

gonna punch it to see if that helps

---

### Post by grayfood on 2007-05-16
hello waylow
 
what do you get if you type in iwconfig in a terminal

sounds like bcm43 not working -

###

i had to remove the bcm43 drivers / blacklist th bcm43 modprobe / install ndiswrapper 1.8 common & utils
install the bcm drivers I got from the windows cd with wireless / modprobe ndiswrapper


if any of this does not make sense reply back

---

### Post by waylow on 2007-05-16
> **grayfood said:**
> hello waylow
 
what do you get if you type in iwconfig in a terminal

sounds like bcm43 not working -

###

i had to remove the bcm43 drivers / blacklist th bcm43 modprobe / install ndiswrapper 1.8 common & utils
install the bcm drivers I got from the windows cd with wireless / modprobe ndiswrapper


if any of this does not make sense reply back

thanks for you response Grayfood

here is the out put of the iwconfig
(i have to type it by hand so excuse the layout - I have borrowed my brothers laptop to connect to the internet )
```

lo         no wireless ext
eth0    no wireless ext

eth1   IEEE 802.11b/g ESSID:""  Nickname:"Broadxom 4306"
          Mode:Managed   Acess Point:Invalid
          RTS thr:off         Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0 Rx invalid crypt:0 Rx inval frag:0
         Tx excwssive retries:0 Invalid misc:0  Missed beacon:0


``` 

don't know have to put something on the black list
and I have tried to install ndiswrapper manually (boot my XP partition - DL - reboot in Ubuntu studio) but had trouble getting it to compile or install or whatever it does

thanks

---

### Post by grayfood on 2007-05-16
hello

try this link first 
[http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper+54+mbps](http://ubuntuforums.org/showthread.php?t=201902&highlight=broadcom+ndiswrapper+54+mbps)


if that fails have a look at this

[http://www.ubuntuforums.org/showthread.php?t=197102](http://www.ubuntuforums.org/showthread.php?t=197102)


hope these help
simon

---

### Post by waylow on 2007-05-16
thanks man

I have tried the first one and all went well but I still can't connect - although it can now see the wireless network

I think the problem is that it still thinks it is eth1 not wlan0
I have tried to gedit the files it asked me to but some of them didn't work

---

### Post by waylow on 2007-05-16
OK I did managed for it to connect when it was set as eth1 - it was connect (ie the network manager icon changed to the bars) but it still wouldn't connect to the internet

Now I think I have changed it to wlan0 correctly and the icon won't connect at all

if i type ifconfig it now says wlan0 instead of eth1

---

### Post by grayfood on 2007-05-16
good sounds like you are making progress

nothing wrong with it saying eth1 (mines set to eth1)

also I think there is a problem with network manager and WPA so .........


try using wicd instead of network manager 

[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)


what you described with the network manager showing the bars is the same that happened to me

only when I used wicd could i connect to the internet

when you use wicd - before you connect click on the little sideways triangle and then advanced settings to set up for WPA - you will need the router password

good luck

---

### Post by waylow on 2007-05-16
I have tried both network manager and Wicd

they both seem to have the same problem - unable to obtain IP adress

I did manage to get Wicd connected to the internet but only when I turned all wireless security off
that tells me that it has something to do with the WPA

so now I have been following the sticky on getting WPA security enabled

with no luck yet :(

i'll keep digging

---

### Post by waylow on 2007-05-16
I have got it working now

still not 100% yet I have to restart networking after every boot
I jad to unistall both Wicd and Network Manager as per [http://ubuntuforums.org/showthread.php?t=202834]("http://ubuntuforums.org/showthread.php?t=202834")

now all I have to do is figure out how to get it to automatically do it on boot

thanks a lot for pointing me in the right direction
I can now go to sleep

---

### Post by grayfood on 2007-05-16
no problem

---

