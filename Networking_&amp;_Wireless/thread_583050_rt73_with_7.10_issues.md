---
title: "rt73 with 7.10 issues"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by neonweb on 2007-10-20
Hi there:
I just installed 7.10, and all seems to be ok (BTW, I performed a clean installation). The only issue I was showing is that in the live CD wifi works great but when installed, no wifi networks are showed up.

Some info (commands performed as root):
```

root@adrian-laptop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

root@adrian-laptop:~# ifconfig wlan0 down
root@adrian-laptop:~# ifconfig wlan0 up
SIOCSIFFLAGS: No hay espacio de buffer disponible
root@adrian-laptop:~# iwlist wlan0 scan
wlan0     Interface doesn't support scanning : Network is down
```

duh, I'm really tired about this... does anyone why can't I up wlan0 interface (error: "There is no buffer space available"). I haven't found anything, and I need to get wifi.

---

### Post by wieman01 on 2007-10-20
All I can offer right now is the tutorial in my signature. I have no experience with the RT73, but I will try to help as much as I can. Give it a try.

---

### Post by kevdog on 2007-10-20
Something is configured properly with your drivers it looks like.  Is the module loaded

lsmod | grep rt

---

### Post by neonweb on 2007-10-20
[QUOTE=wieman01]All I can offer right now is the tutorial in my signature. I have no experience with the RT73, but I will try to help as much as I can. Give it a try.[/QUOTE]

thanks a lot! i tried with feisty to set-up it with ndiswrapper but I never succeded... now seems to work fine... thanks for that.

[QUOTE=kevdog]Something is configured properly with your drivers it looks like. Is the module loaded

lsmod | grep rt[/QUOTE]

nope, because network-manager and iwconfig detects the wifi card. but as i write up, that's working fine now

---

### Post by Scott Carlson on 2008-01-15
I just installed Ubuntu 7.10 32 bit on my older 1.7ghz computer with a USB Controller:  VIA Technologies, Inc.  00:10.3 0c03: 1106:3104 (rev 82)  interface.  I have the TP-LINK TL-WN321G wireless USB adapter.  I followed these instructions above  but had some problems with it only working with a few pings.   If I did a flood of pings I would loose the connection to the access point.   I found if I disabled USB 2.0 to only allow USB 1.0 I was able to continue to flood pings and make long connections work.   To try you can do this as root:
# modprobe -r ehci_hcd 

  Now it seems to be working fine.  For details of my system hardware see the added attachment.  Thanks for all your help.  By the way it also is working on my newer AMD64 computer with Ubuntu 64 bit installed even without this added  ehci_hcd note.

I did  the following on both computers:

downloaded and installed as instructed above
rt73-cvs-2008011011

apt-get remove network-manager
apt-get remove wifi-radar   #it didn't work anymore
apt-get install rutilt	    # works as a replacement for above

added to file /etc/modprobe.d/blacklist
blacklist rt73usb

blacklist rt2500usb

blacklist rt2x00usb
blacklist rt2x00lib
blacklist rt2570


only on my computer with VIA USB Controller 
 I found blacklisting won't work for ehci_hcd, something still loads it on reboot.
I did a dirty fix by modifing file at /etc/init.d/networking
added line at top of the file: 
modprobe -r ehci_hcd
 I found that this also makes my USB flash drive work on this computer where it didn't before this.  I'm not sure why this works.  A bug in via usb driver?


added to file  /etc/network/interfaces
  iface wlan0 inet dhcp

  pre-up ifconfig wlan0 up

  pre-up iwconfig wlan0 essid FREENET

After reboot I sometimes still have to unplug and replug my TP-Link to get it start
after that I have to do a ifdown wlan0 then ifup wlan0 to get it working.  Most certainly after a Windows Xp run with my multiboot system to get the firmware to reload.

I found that I am getting a speed of about 400kB/s when I use samba to move files between another computer on my network.  I was able to moved at least 100mb blocks of files over samba without any problems.  Maybe I could get more speed but I have my AP set to 11mb/s.

  Thanks to you all for your help
    Scott Carlson

---

