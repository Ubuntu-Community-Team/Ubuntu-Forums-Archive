---
title: "Dlink DWL-G122 rev B1 Ubuntu fiesty 7.04. howto?!"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by Depressure on 2007-06-18
Hi.

As u can see in the title I'm using the dwl - g122 rev b1. I can see the wireless networks, but I can't connect...
I'm new to linux and need a guide to get my nic working either with ndis or Linux drivers.

---

### Post by karlax on 2007-09-13
I have the same rev. (B1) installed on a ThinkPad T22 running Fiesty.

Same problem here... After plugging the adapter in, the Network Manager seems to deal with it fine, show the available wireless networks (if any), but can't connect to them...

Any idea on manual settings to add to make it smoothly going on?

Thanks in advance!

---

### Post by ashgeo on 2007-10-01
I have excatly the same dongle and have had it working in Feisty (7.04) but have no idea how!  My PC is a Asus A7V133 mother board with a AMD Duron 1.2Ghz processor and 1Gb RAM - home made system (needs updating to something faster but can't be bothered to go the the installation and transferring software/files!).  It just seemed to work, that is until I did some updates the other day.  Now it "sees" the networks but will not connect and causes the system to "hang" forcing me to press the reset button on the front.  Am now having to revert back to WinDoze....  I have no idea why, and what to do!

---

### Post by ashgeo on 2007-10-01
It's decided to work again all by itself after getting a cup of coffee and watching TV. Bizzare.  Will try a restart...

---

### Post by Lambert on 2007-10-01
That dongle uses the ralink chipset and driver from serialmonkey. The networkmanager page says that chipset/driver has a few problems with network manager.

> Supports unencrypted and WEP networks when used with NetworkManager. While the driver supports WPA, it does not use Linux Wireless Extensions for WPA support, which is required for NetworkManager. Note: WPA/WPA2 is working since kernel-2.6.22 with the new Wireless-Stack and the latest rt2x00 CVS version.

I believe gutsy has the new kernel and looks to solve wpa/wpa2 support. Not sure what encryption method you're using but I would suggest trying another manager such as wifi radar.

Otherwise you can open a terminal and try to manually connect. There are some instructions somewhere on here, haven't been around for a while so can't post a link, somebody can jump in and give manual instructions.

Summary:

Look for a howto on installing the latest driver build from cvs.
Look for a different network management tool
Use a manual method from command line to connect 
Look forward to gutsy with improved support. 

If you're still looking for help, I'll be around later tonight (EDT).

---

### Post by maybeway36 on 2007-10-01
You could try editing /etc/network/interfaces as root. Here's what I have with WEP encryption:
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid NameOfNetwork
wireless-key YOURWEPKEY
```
I know WEP is weak, but it keeps away the people who don't want to take the effort to crack it.

---

### Post by Lambert on 2007-10-01
And if you want to use ndiswrapper, there is a sticky at the top of this section with a howto for the ralink. It says dapper, should still be applicable to feisty.

[http://ubuntuforums.org/showthread.php?t=564419](http://ubuntuforums.org/showthread.php?t=564419)

---

### Post by ashgeo on 2007-10-02
Thanks Folks.  It still seems to be working although decides to "disconnect" for no apparent reason which is resolved by a restart. As am new to the Linux world there is so much I don't understand about drivers and compiling software and the rest I'll stick with it and see what happens when 'Gutsy' is released and in the mean time try to get a book or two to learn some more about stuff.  If it gets really frustrating I can always connect my LAN cable directly to the router which always works , and as a last resort boot up in WinDoze !

---

### Post by Bonder5678 on 2007-10-02
I appear to be having a similar problem.  I've got the D-Link DWL-G122 rev B1 working to the point that it can see my wireless network, though, network manager says it has no signal despite being in the same room as my wireless router and my other computer sees it as almost 100% signal.  When I try to connect to my network, it immediately asks for my network key, so I enter it and nothing happens, it never connects.  I have tried connecting from the command line and have been unsuccessful.  And note, that I'm only configuring the computer in the same room as the router (so I can connect directly to the router with wires if i need to download any packages or anything), once it's working, I'll be moving it to another room, so just running wires rather than using wireless isn't really an option.

Any ideas or help would be greatly appreciated.

---

### Post by ashgeo on 2007-10-03
That is exactly the same problem that I get, from time to time.  The dongle has worked perfectly for a few days and then this morning it sees the network but will not connect (am on XP now).  I have no idea why or what can be done other than to get a new ubuntu compatible WiFi card......  Maybe it is something to do with the weather?!!

---

