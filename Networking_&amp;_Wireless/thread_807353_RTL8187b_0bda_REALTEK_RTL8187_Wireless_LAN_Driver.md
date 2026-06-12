---
title: "RTL8187b 0bda REALTEK RTL8187 Wireless LAN Driver"
date: 2008-05-25
forum: Networking &amp; Wireless
---

### Post by Tlingit on 2008-05-25
This is the exact way to get this card to work!

It is short and easy.

The links didn't work for me to down load them right form the command line but get a working connection copy and past the links in the url download the files.

Unzip and install them when necessary as fallows in the instructions and wammo you should have it.

If you need any assistance with the command line commands to install them just let me know and i will try to help you but fallow this exactly up until the first reboot!

[http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

---

### Post by go_beep_yourself on 2008-05-27
> **Tlingit said:**
> This is the exact way to get this card to work!

It is short and easy.

The links didn't work for me to down load them right form the command line but get a working connection copy and past the links in the url download the files.

Unzip and install them when necessary as fallows in the instructions and wammo you should have it.

If you need any assistance with the command line commands to install them just let me know and i will try to help you but fallow this exactly up until the first reboot!

[http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187)

Hey, I really appreciate the response on your other post sending me to here. I never did realize there could be a native Linux driver when so many were using ndiswrapper. You've got to excuse my Fedora 9 x86_64. I see the directions for Gentoo worked on Ubuntu as well, so it should make no difference if I'm using Fedora. The module succesfully compiled with the directions and loaded into the kernel.

Here's what I did:

```
[chris@localhost Desktop]$ /sbin/lsusb 
Bus 001 Device 005: ID 0781:5151 SanDisk Corp. Cruzer Micro 256/512MB Flash Drive
Bus 001 Device 003: ID 0bda:8189 Realtek Semiconductor Corp. RTL8187B Wireless 802.11g 54Mbps Network Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 002: ID 046d:c00e Logitech, Inc. M-BJ58/M-BJ69 Optical Wheel Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[chris@localhost Desktop]$ 
```

This is after rebooting.

```
[root@localhost ~]# modprobe rtl8187
[root@localhost ~]# lsmod | grep rtl
rtl8187                40960  0 
mac80211              228080  1 rtl8187
eeprom_93cx6           10496  1 rtl8187
cfg80211               33808  2 rtl8187,mac80211
[root@localhost ~]# ifconfig wlan0 up
wlan0: unknown interface: No such device
[root@localhost ~]# ifconfig 
eth0      Link encap:Ethernet  HWaddr 00:14:2A:BD:89:A2  
          inet addr:192.168.1.109  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:2aff:febd:89a2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1015 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1027 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:609703 (595.4 KiB)  TX bytes:138181 (134.9 KiB)
          Interrupt:22 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3164 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3164 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:159016 (155.2 KiB)  TX bytes:159016 (155.2 KiB)

[root@localhost ~]# cat /proc/modules | grep rtl
rtl8187 40960 0 - Live 0xffffffff8837f000
mac80211 228080 1 rtl8187, Live 0xffffffff88346000
eeprom_93cx6 10496 1 rtl8187, Live 0xffffffff88342000
cfg80211 33808 2 rtl8187,mac80211, Live 0xffffffff88338000
[root@localhost ~]# 

```

Here's what I see as the problem. If Linux recognized that was a driver for my wireless usb network adapter, etc., then it would automatically load the driver/module without me manually issuing the modprobe command after reboot. I appreciate the effort to help, and I see you've done a lot of research on wireless in Linux. Thanks again.

UPDATE:::::::::::

I reread that link and noticed this.

> General

This page only deals with the ieee80211 version of the r8187 driver. For the mac80211 rtl8187 version see the mac80211 page. To understand the differences, see mac80211 versus ieee80211 stacks write-up.

IMPORTANT
If you have a new kernel that support mac80211 and includes the new rtl8187 driver then you MUST blacklist it otherwise the ieee80211 version of the module below will not work. See blacklisting mac80211 driver version below.

Then I followed a link to see which of the 2 wireless types I have. Command output is supposed to let me know.

```
[root@localhost ~]# airmon-ng start wlan0


Interface	Chipset		Driver


[root@localhost modprobe.d]# iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

[root@localhost modprobe.d]#
```

It's not working, so I remove it from memory where it is being used as a kernel module.

```
[root@localhost modprobe.d]# modprobe -r rtl8187
[root@localhost modprobe.d]# lsmod | grep mac80211
[root@localhost modprobe.d]# modprobe rtl8187
[root@localhost modprobe.d]# lsmod | grep mac80211
mac80211              228080  1 rtl8187
cfg80211               33808  2 rtl8187,mac80211
[root@localhost modprobe.d]# ifconfig wlan0 up
wlan0: unknown interface: No such device
[root@localhost modprobe.d]# 

```

Before, I had lost all hope of ever getting the wireless working without going back to using 32-bit Linux which I wasn't willing to do. Now I'm trying hard again to make it work. I'm going to do some more reading, and then another reboot to see if I can make this work.

---

### Post by Tlingit on 2008-05-28
Well I'm glad i helped you see at least something. Thats great

Ya a little while after I posted that I was doing something else and I noticed that I had the mac80211 loaded. The only place which said I even had that driver loaded was airdriver-ng.

I got to thinking about what that site had said, and go_beep_your_self had also pointed that out with a highlighter so to speek.I will investigate some more Here in the next few days.

Real quickly I tried to unload mac80211 with airdriver-ng and black list it but when I reboot it goes back to using it. For some reason my internet was down so i couldn't unload and install the stack that went with airdriver, but now my net is back up.When I get home I will try and uninstall the mac80211 stack and install the ieee80211 stack. Right now i have to go though [http://www.aircrack-ng.org/doku.php?id=r8187](http://www.aircrack-ng.org/doku.php?id=r8187) this process to get my wifi back up.

If anyone reading this has any suggestions so as to were i don't have to keep doing this that would be great. My connection with this method is really slow. I hate to say this but it works fine in windows.

So hopefully this works and if anyone else has any ideas or something to add to what I plan on doing would be great I hope i didn't bore anyone.

---

### Post by scholzilla on 2008-05-29
I'm glad you guys are working on this too. I tried the patch above and all seems well at first:

```
matt@Darwin:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

matt@Darwin:~$ ndiswrapper -l
net8187b : driver installed
	device (0BDA:8187) present (alternate driver: r8187)
```

I don't know why r8187 is listed as an alternate driver. I can't find such a driver anywhere and blacklisting it doesn't get rid of it. Aside from that, everything looks ok until I do this:

```
matt@Darwin:~$ ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive
```

The message repeats three times, just as above. I checked and only have one copy of ndiswrapper in my /etc/modules file. Needless to say, I'm not getting wireless. Are you guys running this on a 32- or 64-bit architecture?

Thanks

---

### Post by go_beep_yourself on 2008-05-30
> **scholzilla said:**
> I'm glad you guys are working on this too. I tried the patch above and all seems well at first:

```
matt@Darwin:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=27 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

matt@Darwin:~$ ndiswrapper -l
net8187b : driver installed
	device (0BDA:8187) present (alternate driver: r8187)
```

I don't know why r8187 is listed as an alternate driver. I can't find such a driver anywhere and blacklisting it doesn't get rid of it. Aside from that, everything looks ok until I do this:

```
matt@Darwin:~$ ndiswrapper -m
module configuration already contains alias directive

module configuration already contains alias directive

module configuration already contains alias directive
```

The message repeats three times, just as above. I checked and only have one copy of ndiswrapper in my /etc/modules file. Needless to say, I'm not getting wireless. Are you guys running this on a 32- or 64-bit architecture?

Thanks

You appear to be using a windows driver through ndiswrapper, not the native Linux driver that we've been discussing here. My problem with Ndiswrapper is that I am using 64-bit Linux and the driver is win32 which means I have to switch back to 32 bit Linux, and I'm not willing to do that. I like going FAST!

---

### Post by scholzilla on 2008-05-30
You're correct. What is the native linux driver? Is it the r8187? Where do I get it? Forgive me ignorance.

---

### Post by Tlingit on 2008-05-31
> **scholzilla said:**
> You're correct. What is the native linux driver? Is it the r8187? Where do I get it? Forgive me ignorance.

sudo locate rtl8187

---

### Post by Tlingit on 2008-06-01
Hey anyone have any idea how i can learn how to rebuild my kernel with the ieee80211 stack into it?

---

