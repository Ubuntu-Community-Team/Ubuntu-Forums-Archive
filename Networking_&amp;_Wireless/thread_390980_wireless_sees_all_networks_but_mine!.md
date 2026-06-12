---
title: "wireless sees all networks but mine!"
date: 2007-03-22
forum: Networking &amp; Wireless
---

### Post by damu on 2007-03-22
I try to get Ubuntu "ready to go" on a new laptop for a friend.

I followed the how-to of this [thread]("http://www.ubuntuforums.org/showthread.php?t=185174") to get the wireless card broadcom 4310 of the laptop compaq nx6325 vaguely working.

here is what I have now :

> lisa-laptop:~$ **lspci | grep "Network controller"**
30:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)

and

> lisa-laptop:~$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

In the network manager, the wireless network of one or the other of my neighbors pop up from time to time. Never for very long. As they are clever neighbors, I can't even use their protected network to test wireless on this laptop.


The very weird thing is that it never detect my own network , which is used by 4 other computers, 2 of them running Ubuntu. This laptop is the closest of all to the modem/router...

any idea?

---

### Post by daynah on 2007-03-22
This is going to sound really smart-butt, but I don't mean to sound it that way. I'm saying this on the lines of "Make sure your lamp is plugged in."

Is your router broadcasting the name of your network?

I actually has this problem earlier today. If you don't want to go through the trouble of actually checking, and you know the name (for SURE) of the network, try typing it in, instead of trying to select in the drop down box. IF the problem is that you just have your router set not to broadcast (a decent safety measure), then you should be all set.

This is a good thing to check because Windows will remember the names of all of the old wifis, the old Ubuntus will if you've saved it as a location.

---

### Post by damu on 2007-03-23
No that's not the problem, otherwise I would have it with the 4 other computers which are connected to this network, 2 of them being ubuntu boxes. My network is seen by other computers. 

I however tried to add a new wireless connection through the network manager with the ESSID and WEP of my network and it  failed.

---

### Post by PatsyPoo on 2008-04-18
I'm having the exact same problem with my laptop. It was worse a few days ago - the wifi card wouldn't even stay on. At least now it seems like it's working only not with my network. I have checked and my router DOES broadcast the SSID.
Any ideas?
I know this thread is a bit old but I didn't want to start a new one on the exact same topic...
Someone - please! - help me!
:confused:

By the way, I can connect to the router with my ethernet cable...

---

