---
title: "mini 9 wireless issues"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by JRSinOK on 2009-01-01
Just got my mini 9.  Out of the box I could find my wireless network (at work, WEP encrypted) and connect to the internet.  Started downloading updates and then it happened!  The connectivity read 0% and I could not reconnect to the router no matter what I tried to do.  

Figured it was my router so I packed everything up and went home.

At home I tried the same thing, and got the same results.  Found the network (had taken off the security as I figured that may be the issue) and got on.  Started downloading updates and same thing happened, connectivity went to 0%.  Try to reconnect and the NM acts like it can't see anything.  Not my network or my neighbors.

So, I plugged in the LAN and downloaded all the updates (multi and uni, etc.)

Have restarted 100 times and read every help thread I could find on this issue.  Best I can tell it has something to do with the BCM4310 USB controller that is my wireless card, and some issue with the non-open source drivers for that (w|).  I have read some discussions about ndiswrapper and ndisgtk, but I cannot get the ndisgtk to install.  Apt-get can't find it.

Anyway, help, advice, or guidance would be appreciated.  I am pretty new to linux/ubuntu and have exhausted my research skills and new vocabulary.  

Thanks in advance for the help!

---

### Post by cozmicharlie on 2009-01-01
I am a bit confused - you mention "BCM4310 _USB_ controller that is my wireless card".  Are you plugging the wireless in a usb port?   Also, are you using the native install that came with the Mini 9?  The reason I ask is the wireless should work right out of the box.  You should not have to do anything (like install ndswrapper etc.).  The fact that you can see the network (at least for a short period of time) indicates the wireless is working.  On my Mini 9, I installed the newest version of nm (see post #11 from this thread:  [http://ubuntuforums.org/showthread.php?t=1019121&page=2](http://ubuntuforums.org/showthread.php?t=1019121&page=2)).  It works better and has better support for wpa and broadband (make sure you set up the version for Hardy).

---

### Post by JRSinOK on 2009-01-01
I'm sorry, I may be confusing the terminology. I am using the built-in wireless card.  Not sure which one it is or how to find that out.

I agree it SHOULD work out of the box, but it doesn't work for any prolonged period of time.  

I have read through the thread you referenced and I think we need to take a step backward from that.  I am not having problems with the types of encryption.  I am trying to get on an unprotected wireless router.  Once I get that done and working (for longer than a minute of two) I will tackle the encryption issue.  

How would you trouble shoot the problem of lost or dropped network connections?

---

### Post by Talon2 on 2009-01-01
> **JRSinOK said:**
> 

How would you trouble shoot the problem of lost or dropped network connections?

This site contains some information that might help:

[https://help.ubuntu.com/community/DellMini9](https://help.ubuntu.com/community/DellMini9)

---

### Post by cozmicharlie on 2009-01-01
> **JRSinOK said:**
> I'm sorry, I may be confusing the terminology. I am using the built-in wireless card.  Not sure which one it is or how to find that out.

I agree it SHOULD work out of the box, but it doesn't work for any prolonged period of time.  

I have read through the thread you referenced and I think we need to take a step backward from that.  I am not having problems with the types of encryption.  I am trying to get on an unprotected wireless router.  Once I get that done and working (for longer than a minute of two) I will tackle the encryption issue.  

How would you trouble shoot the problem of lost or dropped network connections?

Yes - but I would still add the newer version of NM.  It is just more stable for me and I have less problems than v6.  Have you narrowed it down to the computer vs the router?  That is, do you have other computers you can use the wireless without any problems?  If so then you may have a defective wireless.  You may want to call Dell support.

---

### Post by JRSinOK on 2009-01-01
Yes, I'm using two other computers on the same wireless router right now.  I'm pretty sure it's the machine.  

As I said, I'm new to linux.  But if I had gotten this problem in XP the first thing I would have done would be to delete the driver and re-install it.  Is that possible and good practice in linux?  If so, how do you do it?

---

### Post by cozmicharlie on 2009-01-01
Linux is different than windows in that the drivers are incorporated in the kernel.  If you go to Administration>Hardware Drivers and you should see it listed.  If not activated go ahead and activate.  You could try and deactivate>reactivate and see if that helps.  The alternative is to install the windows driver via ndiswrapper but you really should not need to do that.  You state you tried the ndisgtk and could not find it - you don't need it.  This is only the gui for ndiswrapper - you can use ndiswrapper without it via the command line (just search the forums - lotsd of how to's).

---

### Post by Talon2 on 2009-01-01
> **JRSinOK said:**
> Yes, I'm using two other computers on the same wireless router right now.  I'm pretty sure it's the machine.  



But what within the machine is the problem?

I suspect the problem to be either the Broadcom wireless hardware or the closed source Broadcom driver.  Dell made a mistake using Broadcom hardware when very well supported Intel wireless hardware is available.  I will not buy Dell hardware again if it contains Broadcom hardware.

With that said, I have multiple Ubuntu systems running in a home/home office environment.  I have two access points connected to a router.  One access point serves up SuperG while the other is just 802.11g.  My Mini 9 does show problems sometimes with the SuperG AP but I've never seen a problem using the 802.11g router.

---

### Post by JRSinOK on 2009-01-01
Ok, not sure what I did, but after re-starting for for the xth time today, the wireless seems to be working.  I did check all the multivers, universe, open source, etc. in the software update section.  I wouldn't consider this problem solved, but now it's working.  Maybe its becasue I have two quartes in my left pocket?!?  I don't know why it works, but I won't question as long as it does.  

I do agree about the Broadcom stuff, though.  

Both routers I refrenced (work and home) are capable of N, but my other computers are only running on G.

Thanks for your help and input.

---

### Post by JRSinOK on 2009-01-02
Okay, I must have taken the quarters out of my left pocket, because I'm back to having the same problem.  I know the hardware works and the drivers work and the router works, some of the time!?!  

Any thoughts on how to trouble shoot this?

---

### Post by cozmicharlie on 2009-01-03
> **JRSinOK said:**
> Okay, I must have taken the quarters out of my left pocket, because I'm back to having the same problem.  I know the hardware works and the drivers work and the router works, some of the time!?!  

Any thoughts on how to trouble shoot this?

In your first post you mentioned that you "figured it was my router so you packed up ..."  Did you try this on someone else's router first?  If not, you may want to find a friend with a working wireless router and see if you can sign on to their wireless.  At least this would narrow it down to a router vs computer issue.

Do you have the stock Ubuntu installed that comes with the Dell Mini 9?
You mentioned that you updated and it stopped.  Did you finish the update or did it disconnect while it was updating?
I assume it connects to a the wired connection on your router - is that correct?
Open a terminal and type ifconfig at the prompt.  Paste the results and post them.
If you go to menu>administration>hardware drivers it is activated correct?
This might have some info that helps.
[https://help.ubuntu.com/community/DellMini9#Knows%20issues%20and%20usage%20notes%20for%20all%20Mini%209%20systems](https://help.ubuntu.com/community/DellMini9#Knows%20issues%20and%20usage%20notes%20for%20all%20Mini%209%20systems)

---

### Post by JRSinOK on 2009-01-04
*> In your first post you mentioned that you "figured it was my router so you packed up ..." Did you try this on someone else's router first? If not, you may want to find a friend with a working wireless router and see if you can sign on to their wireless. At least this would narrow it down to a router vs computer issue.*

I have had it connected to four routers (two wep encrypted, two with no encryption).  This is a hardware/software problem, not a router problem.

> Do you have the stock Ubuntu installed that comes with the Dell Mini 9?  

Yes this is the OS that came installed.  
> 
You mentioned that you updated and it stopped. Did you finish the update or did it disconnect while it was updating?

It disconnected so I went home and finished updating via a LAN.

> I assume it connects to a the wired connection on your router - is that correct?

Yes that is how I updated it.

> Open a terminal and type ifconfig at the prompt. Paste the results and post them.

These are the results when everything is working.  I will post the results after the wireless quits, too.

Working.......

jimmy@jimmy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:d5:95:d5  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1210438825 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1268 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1268 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:63400 (61.9 KB)  TX bytes:63400 (61.9 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:08:48:ed:77  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8ff:fe48:ed77/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:547 errors:0 dropped:0 overruns:0 frame:0
          TX packets:557 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:604801 (590.6 KB)  TX bytes:73028 (71.3 KB)
          Interrupt:16 Memory:f0200000-f0204000 



> If you go to menu>administration>hardware drivers it is activated correctly?

This brings up an interesting question,  Based on some information I found on this website, I have installed ndiswrapper, Blacklisted the Broadcom driver (wl) and I am using the suggested alternate.  But this Broadcom driver still shows that it's in use on th hardware drivers page?
> 

This might have some info that helps.
[https://help.ubuntu.com/community/De...%209%20systems](https://help.ubuntu.com/community/De...%209%20systems)

Thanks, read it before.  This is apperanlty a unique problem as have found  only one other post that has anything similar.  In that post someone suggested it's a function of the wireless card getting too hot.  That doesn't make any sense though, mine does it very quickly afer start-up sometimes.

---

### Post by JRSinOK on 2009-01-04
Here is the output when not working...........
```

jimmy@jimmy:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:21:70:d5:95:d5  
          inet6 addr: fe80::221:70ff:fed5:95d5/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4353 errors:0 dropped:3852212809 overruns:0 frame:0
          TX packets:4207 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4434168 (4.2 MB)  TX bytes:1281001 (1.2 MB)
          Interrupt:220 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1264 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1264 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68310 (66.7 KB)  TX bytes:68310 (66.7 KB)

wlan0     Link encap:Ethernet  HWaddr 00:23:08:48:ed:77  
          inet6 addr: fe80::223:8ff:fe48:ed77/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:286 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3135 (3.0 KB)  TX bytes:7085 (6.9 KB)
          Interrupt:16 Memory:f0200000-f0204000 

```

In addition, here is the system log when the connection quits...

```
Jan  4 09:55:34 jimmy NetworkManager: <info>  (wlan0): device state change: 8 -> 3 
Jan  4 09:55:34 jimmy NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Jan  4 09:55:34 jimmy NetworkManager: <info>  wlan0: canceled DHCP transaction, dhcp client pid 5621 
Jan  4 09:55:34 jimmy NetworkManager: <WARN>  check_one_route(): (wlan0) error -34 returned from rtnl_route_del(): Missing link name TLV (errno = Invalid argument) 
Jan  4 09:55:34 jimmy avahi-daemon[4693]: Withdrawing address record for 192.168.1.101 on wlan0.
Jan  4 09:55:34 jimmy avahi-daemon[4693]: Leaving mDNS multicast group on interface wlan0.IPv4 with address 192.168.1.101.
Jan  4 09:55:34 jimmy avahi-daemon[4693]: Interface wlan0.IPv4 no longer relevant for mDNS.
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) starting connection 'Stallings' 
Jan  4 09:55:34 jimmy NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan  4 09:55:34 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 7 -> 0 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan  4 09:55:34 jimmy NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0/wireless): connection 'Stallings' requires no security.  No secrets needed. 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Config: added 'ssid' value 'stallings' 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan  4 09:55:34 jimmy NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan  4 09:55:34 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Jan  4 09:55:39 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Jan  4 09:55:49 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Jan  4 09:55:49 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Jan  4 09:55:53 jimmy ntpd[5720]: sendto(91.189.94.4) (fd=23): Invalid argument
Jan  4 09:55:54 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Jan  4 09:55:59 jimmy NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation. 
Jan  4 09:55:59 jimmy NetworkManager: <info>  (wlan0): device state change: 5 -> 9 
Jan  4 09:55:59 jimmy NetworkManager: <info>  Activation (wlan0) failed for access point (stallings) 
Jan  4 09:55:59 jimmy NetworkManager: <info>  Marking connection 'Stallings' invalid. 
Jan  4 09:55:59 jimmy NetworkManager: <info>  Activation (wlan0) failed. 
Jan  4 09:55:59 jimmy NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Jan  4 09:55:59 jimmy NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) starting connection 'Stallings' 
Jan  4 09:56:08 jimmy NetworkManager: <info>  (wlan0): device state change: 3 -> 4 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled... 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) started... 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled... 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) Stage 1 of 5 (Device Prepare) complete. 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) starting... 
Jan  4 09:56:08 jimmy NetworkManager: <info>  (wlan0): device state change: 4 -> 5 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0/wireless): connection 'Stallings' requires no security.  No secrets needed. 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Config: added 'ssid' value 'stallings' 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Config: added 'scan_ssid' value '1' 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Config: added 'key_mgmt' value 'NONE' 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete. 
Jan  4 09:56:08 jimmy NetworkManager: <info>  Config: set interface ap_scan to 1 
Jan  4 09:56:08 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Jan  4 09:56:13 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Jan  4 09:56:23 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 3 -> 0 
Jan  4 09:56:23 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 0 -> 2 
Jan  4 09:56:28 jimmy NetworkManager: <info>  (wlan0): supplicant connection state change: 2 -> 3 
Jan  4 09:56:33 jimmy NetworkManager: <info>  Activation (wlan0/wireless): association took too long, failing activation. 
Jan  4 09:56:33 jimmy NetworkManager: <info>  (wlan0): device state change: 5 -> 9 
Jan  4 09:56:33 jimmy NetworkManager: <info>  Activation (wlan0) failed for access point (stallings) 
Jan  4 09:56:33 jimmy NetworkManager: <info>  Marking connection 'Stallings' invalid. 
Jan  4 09:56:33 jimmy NetworkManager: <info>  Activation (wlan0) failed. 
Jan  4 09:56:33 jimmy NetworkManager: <info>  (wlan0): device state change: 9 -> 3 
Jan  4 09:56:33 jimmy NetworkManager: <info>  (wlan0): deactivating device (reason: 0). 
```

---

### Post by cozmicharlie on 2009-01-05
post the output from this command:
sudo lshw -C network

I would suggest that you try to obtain either a usb or live cd verison of 8:10 and run it on the computer to see if the wireless will work in 8:10 (it has better wireless support).  You can create a live usb stick by following these instructions:
[http://cdimage.ubuntu.com/releases/intrepid/release/](http://cdimage.ubuntu.com/releases/intrepid/release/)

Also, the Dell has something called airport mode were it shuts down a number of functions to save the battery - one of those is the wireless.  I read somewhere that people were having trouble with this and had to shut it off.  I think it is under preferences>power management.

---

### Post by JRSinOK on 2009-01-05
I am familiar with the "airport" mode and I know that's not the issue, assuming the machine function properly or it wouldn't let me on in the first place.  

I will give 8.10 a try wit the live USB Stick.  

Here is output requested.

Thanks for you help.

```
jimmy@jimmy:~$ sudo lshw -C network
[sudo] password for jimmy: 
  *-network               
       description: Wireless interface
       product: BCM4310 USB Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:23:08:48:ed:77
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+bcmwl5 driverversion=1.52+Broadcom,09/20/2007, 4.170. latency=0 link=yes module=ndiswrapper multicast=yes wireless=IEEE 802.11g
  *-network
       description: Ethernet interface
       product: RTL8101E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:21:70:d5:95:d5
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.2LK duplex=full ip=192.168.1.104 latency=0 link=yes module=r8169 multicast=yes port=twisted pair speed=100MB/s
```

---

### Post by cozmicharlie on 2009-01-05
Everything on your output looks fine.  It is showing that it is seeing your card and it is using the driver you installed from ndswrapper (driver=ndiswrapper+bcmwl5).  I am thinking you may have a defective card.  Lets see if it works when you try 8:10.  I have also searched on the Dell forums and in other places and I have not come up with anything related to your specific problem that you haven't already tried.  I would normally not recommend this but you could try posting using a different subject line.  Usually, wireless problems get as lot of responses and you are not.  I think it is because the subject is specific for "Mini 9".  If you post something like "wireless broadcam discconecting problem" you would probably attract more responses and hopefully some network guru that might have an answer.  Or, alternatively post to one of the many threads already dealing with broadcom cards.  The mods don't like double posting so make sure you word it different.  Or you could try posting on the Mini 9 Dell forum.  I am just at a loss as to why this is happening to you. Everything looks to be set up properly.

---

### Post by JRSinOK on 2009-01-05
Thanks for your help.  I'll try over at the wireless/networking forum.  If nothing else I've learned a lot about the OS and software drivers.  

I appricate your time and intrest.  

I finally got through to Dell.  Those lazy SOB's just told me to re-install the OS.  And that wouldn't be a big deal if they sent the computer with a bootable USB, but now I guess I have to buy an optical drive to do this.

Anyway, thanks again.  I let you know how 8.10 goes

---

### Post by thomaston on 2009-01-05
Yep, I'm the guy having the same problem. After spending the last hour talking to Dell, I got a dispatch# and they're sending me a box to ship it back in. I initially was told to just re-install the OS, but had to keep pushing for some actual warranty work to get done.

---

### Post by cozmicharlie on 2009-01-05
> **JRSinOK said:**
> Thanks for your help.  I'll try over at the wireless/networking forum.  If nothing else I've learned a lot about the OS and software drivers.  

I appricate your time and intrest.  

I finally got through to Dell.  Those lazy SOB's just told me to re-install the OS.  And that wouldn't be a big deal if they sent the computer with a bootable USB, but now I guess I have to buy an optical drive to do this.

Anyway, thanks again.  I let you know how 8.10 goes

No you don't have to buy an optical drive.  You can install any version of Ubuntu from a usb drive. Their are a couple options - 1. is the link I sent and 2. is a package called unetbootin.  This will show you how:
[http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Using_Unetbootin](http://www.ubuntu-eee.com/wiki/index.php5?title=How_to:_Using_Unetbootin)
You simply install unetbootin then load the iso from the cd that came with the Dell. Make sure you use a usb drive that is bootable.  Plug in the drive with the computer off.  Hit F2 (or whatever the command is to get to the boot menu) and choose the usb drive to boot from.  You should then be able to install it.
 
That is why I had you make an 8:10 usb drive- so you could try 8:10 (as long as you use a live cd version) without having to install it.  If 8:10 does not work then something is wrong with your card and you should return it to Dell.  

Keep posting and let us know if you find a solution or if you need any help reinstalling.

---

### Post by JRSinOK on 2009-01-05
I figured out the USB boot trick and re-installed factory ISO.  It made things worse.  When I went back to the wl driver that came with the computer I coulnd't get it to connect with my router at work. I took of the encryption and that didn't help either.  

Finally Dell gave in and said to send it back to them, like thomaston.

At this point, I think I have ruled out everything on the software side.

Oh yeah, I did make a bootable install of 8.10. I never fully installed it, but the live version did the same thing as 8.04 that came with the computer.  

Oh, well.  Love the computer and the OS and I got to learn a lot about both in this processs.  I just hope when I get it back that it works like it's suppose to.

This mini was for my wife.  She wanted a new computer and I wanted to learn about Linux.  So far, I would say I got the better end of the deal.

---

### Post by cozmicharlie on 2009-01-05
I think you did the right thing by sending it back.  Hopefully the new one will work like it is supposed to.  Post back when you get it and let me know if the new one works for you.

---

### Post by NoobBiscUiT on 2009-01-14
hey, 

i got mine working in kubuntu using wicd network manager instead of network manager. there is a good article about this in kubutu forums. i had the same card as you.

i have a dell mini also, and i recently purchased the Gigabyte GN-WI06N-RH.

i have yet to get this card working in ubuntu, and it bugs me. 

hopefully wicd work for you if you try it out :D

---

### Post by JRSinOK on 2009-01-20
Well, I got the computer back and everything is working great.  All Dell sent was a form letter saying the "keyboard and wireless card" had be repaired.
Don't know what was wrong and I guess it doesn't really matter, as long as everything works now.

Thanks for all the input.

---

### Post by cozmicharlie on 2009-01-22
Great - glad to hear it is working for you.

enjoy

---

### Post by thomaston on 2009-01-23
I got mine back from Dell today. All they did was a OS re-install, but it's working fine so far. I've got the same wireless card, so apparently it was a software issue after all.

---

