---
title: "belkin f5d7050 (yes another thread!)"
date: 2011-02-20
forum: New to Ubuntu
---

### Post by bluetac24 on 2011-02-20
Hello, Ive been struggling with this for a week now. I've tried pretty much every tutorial and walkthrough I can get my (increasingly) sweaty mitts on. The latest I've tried is this:
[http://linuxsoftwareblog.com/blog/?p=30](http://linuxsoftwareblog.com/blog/?p=30)

Followed by my own hashed together attempt with ndiswrapper an adding the following to blacklist.conf: [FONT=monospace][/FONT]
```

blacklist rt73usb
blacklist rt2570

```
Each attempt has been with a clean install. I've experimented with wicd with no luck also.

lsusb shows:
```

matt@matt-desktop:~$ lsusb
Bus 002 Device 003: ID 15d9:0a33 Trust International B.V. Optical Mouse
Bus 002 Device 002: ID 050d:705e Belkin Components F5D7050 Wireless G Adapter v5000 [Realtek RTL8187B]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 04f3:0103 Elan Microelectronics Corp. 
Bus 001 Device 002: ID 0781:5150 SanDisk Corp. SDCZ2 Cruzer Mini Flash Drive (thin)
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

iwconfig shows:
```

matt@matt-desktop:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=0/3  
          RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

I don't really know what I'm doing (evidently!!!) so be gentle! Any help greatly appreciated.

---

### Post by arochester on 2011-02-20
First, look in your Menu for an item called "Hardware Drivers." Open that. Does the driver for your wireless card appear in that? If it does, temporarily, connect your computer by wire and click the Enable button. It takes a little while. It should download, install and enable the driver. REBOOT. Job done.

---

### Post by bluetac24 on 2011-02-20
hmmm, hardware devices is apparently additional drivers in 10.10, and it says there are "no proprietaty drivers in use on this system"

---

### Post by marshag63 on 2011-02-21
I have a Belkin F5d7050 USB adapter -it worked out of the box for me with a Mint 9 lxde install (based on 10.04).  It uses rt73usb.

Are you sure you have your access point configured right.  It shows no essid (what you named your network - default would be something like "belkin??"something.  Also make sure you are not too far away from the router.

One thing you can do is boot a live cd, with the usb adatper plugged in and check and see if the belkin adapter's lights flash.  Left click on the network icon and see if it picks up your wireless router.  If lights flash, it is working.  If lights flash and your wireless router is not listed, then there is a problem with your router.  

You can also check what your wifi adapter is picking up by typing "sudo iwlist scan" (without quotes) and entering your password - look for the entry "wlan0".

I can verify it should work out of the box.

Hope this helps.

MDG

---

