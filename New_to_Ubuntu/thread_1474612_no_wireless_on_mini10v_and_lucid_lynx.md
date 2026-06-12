---
title: "no wireless on mini10v and lucid lynx"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Matt__ on 2010-05-06
[FONT=arial][SIZE=2][COLOR=black]this is yet another no wireless post for 10.04 on a dell mini 10v
 I have the Broadcom Corporation BCM4312 802.11b/g (rev 01) wireless chip and just cant get it to connect.
 so far I have tried (from these forums and others)
 
[LIST]
[*]use restricetd driver b43**
[*]use restricted driver STA
[*]install b43-fwcutter
[*]wicd
[*]reinstall bcmwl-kernel-source
[*]ndiswrapper
[*]reinstall lucid 10.04
[/LIST]
 none of this has had effect. periodically I have had access to a list of wireless networks but I cannot connect to any of them, but mostly it shows NO networks and not even a listing under the panel icon for wireless.

 Ive now run out of forum posts to follow and have no idea how to proceed so any help appreciated.

Just switched over to 10.04 to get terminal info and wireless networks are now showing and connect! but no data is transfered at all?!?!

a few results from terminal commands...

[/COLOR][/SIZE][/FONT][FONT=arial][SIZE=2][COLOR=black]**lspci -nn**

03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11b/g [14e4:4315] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

**iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:199
          Rx invalid nwid:0  invalid crypt:1  invalid misc:0

**sudo lshw -c network**

  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 0c:60:76:21:72:34
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:f0100000-f0103fff

any advice please?
[/COLOR][/SIZE][/FONT]

---

### Post by Matt__ on 2010-05-06
been messing with this all day again and still no joy...anyone?

---

### Post by sb5551 on 2010-05-06
Anybody? I have this same problem.

---

### Post by TransitMan on 2010-05-06
Very odd.
I installed 10.04 on a Dell Mini 910 and used the restricted driver b43** with no problems.

After I installed the "driver", I rebooted and then went to the network icon, and made the changes for a wireless connection and was online through my wireless router.
The person I did this for took it home, and with some phone coaching, was able to connect to their wireless router with no problem.

I'd suggest you uninstall everything, and then start from scratch again, using only the restricetd driver b43**. Just remember to reboot after you install, or you will frustrate yourself at not being able to get online.

---

### Post by sb5551 on 2010-05-07
So, I completely reinstalled everything. Everything works great on the mini, now I just have to reinstall everything on the laptop that is having the same problem.

---

### Post by TransitMan on 2010-05-08
This is a good thing to hear.

---

### Post by Matt__ on 2010-05-09
Ubuntu is getting as screwy as windows it seems!!!
been running 9.04 from a key, but ran out of space on it..so booted to netbooks install of 10.04, and damn me if the wireless didnt detect and work instantly!!!
now to see if it sticks lol


so the moral of the story is keep rebooting and messing until it works!! even if you think youve exhausted all avenues of approach.

---

