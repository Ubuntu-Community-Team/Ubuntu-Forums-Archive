---
title: "Re: Xubuntu/Ubuntu networking questions"
date: 2017-04-10
forum: Networking &amp; Wireless
---

### Post by russkyca on 2017-04-10
I need some help configuring my settings - let me try to summarize and briefly explain what happened....
1) I have two partitions of Ubuntu - Ubuntu Gnome @ 16.04 &
Xubuntu 16.10* (*I upgraded 16.04 to 16.10 - HENCE my selection of this section of the forum for my question(s))   

2) I tried to upgrade the Xubuntu install - I used the GUI way - so I checked for 'check for new versions' or whatever it is - and of course, it asks if you want to upgrade to 16.10 - so I do
Everything seemed to upgrade normally and work EXCEPT my internet connection.... fortunately, I own a smartphone and currently use another partition for an Ubuntu install.... so I google the messages 

I eventually *change* settings in my network files - maybe a major mistake.... (you tell me) because now the settings look different than my 16.04 Ubuntu install - I compared them.... I got the internet connection to work - but then it showed 'Ethernet Networks not managed' or whatever it was.... so I messed around again with settings....  

This is my ifconfig output now:
```
   eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
         inet 192.168.1.X  netmask 255.255.255.0  broadcast 255.255.255.0

         inet6 fe80::224:8cff:fe29:44e8  prefixlen 64  scopeid 0x20<link>
         ether 00:24:8c:29:44:e8  txqueuelen 1000  (Ethernet)
         RX packets 19129  bytes 27798772 (27.7 MB)
         RX errors 0  dropped 0  overruns 0  frame 0
         TX packets 11375  bytes 869998 (869.9 KB)
         TX errors 0  dropped 0 overruns 0  carrier 1  collisions 0
 
 lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
         inet 127.0.0.1  netmask 255.0.0.0
         inet6 ::1  prefixlen 128  scopeid 0x10<host>
         loop  txqueuelen 1  (Local Loopback)
         RX packets 8895  bytes 538275 (538.2 KB)
         RX errors 0  dropped 0  overruns 0  frame 0
         TX packets 8895  bytes 538275 (538.2 KB)
         TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
```

*I changed the ip address.... it's correct and not important here

Xubuntu 16.10   (upgraded from 16.04 to 16.10)
```
 /etc/network/interfaces
 
 # interfaces(5) file used by ifup(8) and ifdown(8)
 auto eth0
 iface eth0 inet dhcp
 
 /etc/NetworkManager/NetworkManager.conf
 [main]
 plugins=ifupdown,keyfile,ofono
 dns=dnsmasq
 
 [ifupdown]
 managed=true
```

I read on some bug list to add an empty file...(in bold)

(in /etc/NetworkManager/conf.d/
```
 **10-globally-managed-devices.conf**

 default-wifi-powersave-on.conf
```

I have to check my other LibreOffice doc (where I saved this info - maybe I should email it to myself?) - where I have the outputs and file content of the 'same' in Ubuntu 16.04....for comparision
I'm not sure comparing these when the Ubuntu OS's are at different versions helps or benefits in helping to answer my questions.... do you know?

Also, in Xubuntu, when you click the 'up/down' arrow for internet connections/network, it shows:   
Ethernet Networks
eth0
Disconnect
Ifupdown (eth0)

I think the configuration and display from my 16.04 install is 'better' configured and makes more sense....
I was wondering if I should just edit the files so they are set up more like that....

What do you think?   My internet connection is working but the configuration/settings look too messed up?
Edit:   P.S.  I'm using a desktop
P.S.S.  I dunno if this should be in the 'networking' section...I did an upgrade and it's primarily a networking issue? :-/

Ubuntu Gnome 16.04   
 
```
  /etc/network/interfaces
   # interfaces(5) file used by ifup(8) and ifdown(8)
 auto lo
 iface lo inet loopback
 
 
 /etc/NetworkManager/NetworkManager.conf 
[main]
 plugins=ifupdown,keyfile,ofono
 dns=dnsmasq
 
 [ifupdown]
 managed=false
 
 $ ifconfig
 eth0      Link encap:Ethernet  HWaddr 00:24:8c:29:44:e8   
           inet addr:192.168.1.X  Bcast:192.168.1.255  Mask:255.255.255.0

           inet6 addr: fe80::21a:4bf4:c3d0:b15b/64 Scope:Link
           UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
           RX packets:62047 errors:0 dropped:0 overruns:0 frame:0
           TX packets:60232 errors:0 dropped:0 overruns:0 carrier:1
           collisions:0 txqueuelen:1000  
           RX bytes:41667187 (41.6 MB)  TX bytes:8846397 (8.8 MB)
 
 lo        Link encap:Local Loopback   
           inet addr:127.0.0.1  Mask:255.0.0.0
           inet6 addr: ::1/128 Scope:Host
           UP LOOPBACK RUNNING  MTU:65536  Metric:1
           RX packets:48 errors:0 dropped:0 overruns:0 frame:0
           TX packets:48 errors:0 dropped:0 overruns:0 carrier:0
           collisions:0 txqueuelen:1  
           RX bytes:5907 (5.9 KB)  TX bytes:5907 (5.9 KB)
```

---

### Post by howefield on 2017-04-11
Moved to the "*Networking & Wireless*" forum.

---

### Post by oldfred on 2017-04-11
Not sure I can help as for my Ubuntu desktop systems, it has just worked. I have had to change settings if I change routers and they use different default IP.

Back with 6.06, I do remember manually editing & changing a lot of settings. Comparing my XP & Ubuntu and writing into margins of Ubuntu book my commands I used.
But all new systems use the gui. I have not even used that for years & had to look to find it. In System settings now, Network, wired, options. Not sure where in Xubuntu.

And some that know networking have posted whatever you do, not not mix use of gui to configure and manual configuration. They then will conflict.

---

### Post by Bucky Ball on 2017-04-11
> **oldfred said:**
> And some that know networking have posted whatever you do, not not mix use of gui to configure and manual configuration. They then will conflict.

This is it, and possibly why you're having issues. I can only help with Xubuntu, but here's my /etc/network/interfaces file (on Xubuntu-core 16.04 LTS):

```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
```

That's it. Network Manager will not play nice with changes in /etc/network/interfaces. If you want to do this solely by configuring that file, remove Network Manager. If not, make your file look like mine and configure your network by editing connection through the Network Manager GUI (click the network icon, 'Edit Connections'). 

Hope that helps a bit and good luck.

---

### Post by russkyca on 2017-04-11
Thanks so much for your subsequent posts, old fred and Bucky Ball!

You helped me think of another question....however, I need to ask users who have 16.10! :)   I wonder if it's even applicable to someone firing up a Live 'CD' of 16.10?   Can you tell me if 16.10 has these settings, too (yours, in 16.04 - which is the same as my Gnome 16.04!!!)

So, the question is, those of you who have tried the live version of 16.10 and/or installed with it, Yakkety Yak OR upgraded to 16.10 (assuming you got that far), have those settings?  Or I should just ask, what do you have in your networking files (content wise) and does your internet connection work (out of the box, as soon as you upgraded) or did you have to configure it somehow?

The main content to ask about is:   /etc/network/interfaces (what content is in yours?)

What file or files is in *your*:
/etc/NetworkManager/conf.d/

When you run 'ifconfig - a' - what is your output?

I'm asking, in particular, those users who have a 16.10 of Ubuntu (doesn't matter which DE/flavour), what do you have?   Also, it might be easier to compare those who are using LAN/wired (i.e. a wired connection) - wireless/wifi will have the associated settings for using wireless.   I don't have a wifi card yet so such settings probably won't help me much, unfortunately.   I think your settings will help me determine which settings I should have - but, I'm inclined to agree with Bucky Bell.... I probably should have left my settings alone and troubleshooted the non-working internet connection another way but I'll see what people have (in 16.10), right now.   

If I don't solve this or I cannot find enough samples, I might just wait until 17.04 is released and install that in the partition where I upgraded 16.04 to 16.10 (i.e. my Xubuntu install).   

I hope I didn't make it more confusing.... you know what I'm talking about (the entire time), right? :-D

FYI, I never touched my settings for Gnome 16.04 (which I also run) -  obviously - since I didn't upgrade it (yet?) and have not had an  internet connection problem.   The internet connection problem happened  AFTER I upgraded my Xubuntu install (Xubuntu 16.04 to 16.10) - once I  did that and after the reboot (following my boot-up to Gnome 16.04 to  run update-grub) into Xubuntu 16.10, I had NO internet connection....  So, I had to again reboot - choose Gnome 16.04 and use the internet to  google the messages (wrote these down).

So...without being more confusing, FYI...my settings in Gnome 16.04:
```
/etc/NetworkManager/NetworkManager.conf
[main]
 plugins=ifupdown,keyfile,ofono
 dns=dnsmasq
 
 [ifupdown]
 managed=false
```

/etc/network/interfaces
```
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```
In my Xubuntu 16.10, they are obviously something else - I posted what  the content was in a previous post.   Trying to determine what should be  there...

---

### Post by oldfred on 2017-04-11
I try to have at least one of every current install somewhere on my system. Already have 2 copies of 17.04 one on flash drive and one on sdb.
Tomorrow I will boot into Yakkety and see what it shows, but it is Ubuntu not any other flavor.

But since 9.10, I have only done clean new installs. Up thru 9.04, I did upgrades from orginal 6.06 and back then video drivers were a hassle.
I had to new a new install as I was converting from 32 bit to 64 bit and it worked so well, I have only done clean installs into a new partition, so I have old install to go back to if needed.

---

### Post by Bucky Ball on 2017-04-11
16.04, 16.10; doesn't matter. Same same. No need to wait. Network Manager and the /etc/network/interfaces file changes will not play together. Period. :)

As for internet settings in a live session; all bets are off. No idea about that and any changes you make there will be lost on reboot anyhow. If you want to see what that file looks like in a live session, boot to a 16.10 live session and open the /etc/network/interfaces file and have a peep.

---

### Post by russkyca on 2017-04-12
> **oldfred said:**
> I try to have at least one of every current install somewhere on my system. Already have 2 copies of 17.04 one on flash drive and one on sdb.
Tomorrow I will boot into Yakkety and see what it shows, but it is Ubuntu not any other flavor.

But since 9.10, I have only done clean new installs. Up thru 9.04, I did upgrades from orginal 6.06 and back then video drivers were a hassle.
I had to new a new install as I was converting from 32 bit to 64 bit and it worked so well, I have only done clean installs into a new partition, so I have old install to go back to if needed.Thank you, very much!  I appreciate it. :)

> **Bucky Ball said:**
> 16.04, 16.10; doesn't matter. Same same. No need to wait. Network Manager and the /etc/network/interfaces file changes will not play together. Period. :)

As for internet settings in a live session; all bets are off. No idea about that and any changes you make there will be lost on reboot anyhow. If you want to see what that file looks like in a live session, boot to a 16.10 live session and open the /etc/network/interfaces file and have a peep.Very interesting....if you are correct.   It makes me think of two questions for you, though. :)   1) Why do some people who upgrade to 16.10 suddenly have no internet connection? ;)   (Like what happened to me).   Do you believe me? :)   

2) What do you use for creating the 'live iso?'  I often used 'dd' but now there are a host of programs/applications with GUI interfaces - but, the majority require Windows.   That's fine as I can use Windows 7 for now.   I believe the choices are Rufus (never used yet), Linux Live USB Creator (used a few times), Universal USB Creator (might have used it, can't remember) and Unetbootin (used, several times, found it relatively unreliable....maybe that's changed?).   I often used dd - and had several attempts of trial and error, wouldn't work for me a few times but ultimately, 'I did something correctly' and I could boot up and was able to install.   'Linux Live' worked, too, I think.   I know I didn't use dd every time.  

Looking forward to your answer to #1 though as I am wondering how often it happens and why. ;)

---

### Post by Bucky Ball on 2017-04-12
1/ Yes, I believe you are having trouble with your internet. No, what I'm saying has nothing to do with whether I believe that or not. I wouldn't have the faintest idea why people lose their internet when upgrading to 16.10. Not everyone does so strange question, and unanswerable. Then again, I also wouldn't know why every person that does so upgrades to a release that expires in May from a release that is supported until 2021. But there you go.

These things are by the by and not sure they are related to the issue you are trying to solve, but rather 'hypotheticals'. What I am saying is that if you have Network Manager installed and start screwing with the /etc/network/interfaces file, you are asking for issues. Use the Network Manager GUI to configure your network or uninstall Network Manager.

2/ You do NOT want to use Windows tools on a Linux partition, particularly the / OS partition. Use Linux tools for Linux partitions, Win tools to work with Win partitions. To create a live USB, I have used dd ([mkusb is apparently a safer alternative]("https://help.ubuntu.com/community/mkusb"), but never used it) but generally use UNetbootin.

---

### Post by oldfred on 2017-04-12
I did boot into 16.10, and as Bucky Ball said, it is the same.
And it had not  been updated since I installed(?) and took a while to do all the updates.

I converted to directly booting ISO from grub both from another hard drive or from a flash drive, which is a bit more advanced. But most can use these:
 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Also:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb) 

      
 This will boot an ISO from a hard drive or any second drive or flash drive
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[https://wiki.archlinux.org/index.php/Multiboot_USB_drive](https://wiki.archlinux.org/index.php/Multiboot_USB_drive)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)

---

### Post by russkyca on 2017-04-14
> **Bucky Ball said:**
> 1/ Yes, I believe you are having trouble with your internet. No, what I'm saying has nothing to do with whether I believe that or not. I wouldn't have the faintest idea why people lose their internet when upgrading to 16.10. Not everyone does so strange question, and unanswerable. Then again, I also wouldn't know why every person that does so upgrades to a release that expires in May from a release that is supported until 2021. But there you go.

These things are by the by and not sure they are related to the issue you are trying to solve, but rather 'hypotheticals'. What I am saying is that if you have Network Manager installed and start screwing with the /etc/network/interfaces file, you are asking for issues. Use the Network Manager GUI to configure your network or uninstall Network Manager.

2/ You do NOT want to use Windows tools on a Linux partition, particularly the / OS partition. Use Linux tools for Linux partitions, Win tools to work with Win partitions. To create a live USB, I have used dd ([mkusb is apparently a safer alternative]("https://help.ubuntu.com/community/mkusb"), but never used it) but generally use UNetbootin.

You said not to use Windows software but that's ridiculous.   Most of the Linux sites like pendrivelinux suggest and recommend those programs and most run on Windows.   There's not too many Linux-based tools...other than dd and knowing what to run (CLI) and then there's Unetbootin which I know is sometimes suggested but also often has detractors.   Maybe it's been fixed by now, I don't know but it didn't always work for me.   I started using dd since I could eventually get my usb stick copied with the .iso I downloaded but there's a lot of options one can use - and can be a touch complicated.   

I realize that mkusb has dd 'under the hood' but the program, albeit nice with a gui, is not intuitive and I couldn't get it to do anything.   I just want the .iso I downloaded copied so the usb stick is bootable with it - which dd can do, via CLI and all the Linux programs (on Windows) supposedly do.... some seem better than others.   All of them are way more intuitive and easy compared to this application.

P.S.  16.04 is buggy.   I think it's normal to want to upgrade so one can see if they can get past the bugs.

I keep getting crashes.   'Sorry, Ubuntu 16.04 has experienced an internal error.  If you notice further problems, restart your computer;
/usr/bin/gnome-shell
*Package
gnome-shell 3.18.5-0ubuntu0.2

The message keeps going with other content below that part.  

I hope Gnome 3.24 or whatever the most recent version is, is better than this one.

---

### Post by Bucky Ball on 2017-04-14
You are repeatedly misunderstanding me.

I said don't use Windows software to resize Linux OS partitions and don't use Linux software to resize Win OS partitions. That simple.

Leave you to it. Good luck.

---

### Post by russkyca on 2017-04-15
> **Bucky Ball said:**
> You are repeatedly misunderstanding me.

I said don't use Windows software to resize Linux OS partitions and don't use Linux software to resize Win OS partitions. That simple.

Leave you to it. Good luck.Fair enough but when did I talk about resizing partitions?  Sigh.  Thanks for all the replies, advice and help.

And, btw, I agree with you - that seems like common sense - and I understand you now.

P.S.  I tried Unetbootin to create/copy the .iso onto my usb stick.  Seemed to work.   I booted up and was able to choose the usb drive - upon doing that, I was able to boot Ubuntu Gnome 17.04.   I think I might try it as I have the extra partition.  

Leaving my 16.04 as is and maybe I can solve the gnome error at some point.

I want to give a special thanks again to your replies, you guys.   It saved me lots of time and I was able to confirm that I should have left those networking files alone.   Not sure why I suddenly had no internet after the upgrade to 16.10 (of the other partition w/ Xubuntu).   It's puzzling but I won't worry about it now.   When I tried Ubuntu Gnome 17.04, the internet worked with the live iso.   The question is whether that will be the case when there's a clean install.   I don't see any reason why I'd have any issue.   Might be fun to see what happens.   I saved any work I had and copied files - to an external drive.   So, I can experiment with that partition.   Thanks again.

---

### Post by Bucky Ball on 2017-04-15
My mistake. *I* misunderstood *you*. Apologies. :)

---

