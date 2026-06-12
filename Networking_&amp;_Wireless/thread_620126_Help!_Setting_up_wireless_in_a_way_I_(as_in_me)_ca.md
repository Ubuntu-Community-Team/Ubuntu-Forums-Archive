---
title: "Help! Setting up wireless in a way I (as in me) can understand."
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by superdave7380 on 2007-11-22
Yes, I know. There are countless threads on this. I think I've read 'em all. Forgive me. I'm an idiot.

The last instructions I followed were from the following..:

[http://ubuntuforums.org/showthread.php?t=571194](http://ubuntuforums.org/showthread.php?t=571194)

From my terminal...

david@david-laptop:~$ sudo lshw -C network

  *-network:0             
       description: Wireless interface
       product: PRO/Wireless 2200BG Network Connection
       vendor: Intel Corporation
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:a5:6f:cf
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.0kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) ip=192.168.0.136 latency=32 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off
  *-network:1
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:06:07.0
       logical name: eth0
       version: 10
       serial: 00:16:d3:40:cf:1b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full ip=192.168.0.136 latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

david@david-laptop:~$ gksu gedit /etc/wpa_supplicant.conf (here, I pasted the WPA2 lines from the above link... and added my SSID and password... although, I would like to use the roaming feature to see all the networks...

david@david-laptop:~$ sudo ifconfig eth1 down

david@david-laptop:~$ sudo dhclient -r eth1

Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth1/00:16:6f:a5:6f:cf
Sending on   LPF/eth1/00:16:6f:a5:6f:cf
Sending on   Socket/fallback
david@david-laptop:~$ sudo wpa_supplicant -w -D ipw -i eth1 -c /etc/wpa_supplicant.conf
Line 8: invalid key_mgmt 'RSN'
Line 8: no key_mgmt values configured.
Line 8: failed to parse key_mgmt 'RSN'.
Line 12: failed to parse network block.
Failed to read or parse configuration '/etc/wpa_supplicant.conf'.

I also tried through the network manager (obviously...)

Anyhoo, thanks.

Oh, Intel 2200bg

---

### Post by superdave7380 on 2007-11-23
Hmm... maybe, if this thread has a reply, more people will check it out, and maybe someone WILL HELP ME!!!

---

### Post by superdave7380 on 2007-11-28
Well, I was right about more people viewing the thread... That's gotta count for something.

---

### Post by CHFFriday on 2007-11-28
In your post you will see a line in the lshw -C network listing as this:
maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=radio off

If this is a Laptop the there might be a Button that turns on the wireless radio or it maybe software controlled anyway you need to turn ON the Wireless Radio before you can setup Wireless.

CHFFriday

---

### Post by superdave7380 on 2007-11-28
Hmm...
I do have the wireless button on my laptop... doesn't see to be doing much, though. On Windows, the OSD would tell me it was active... oh, not to mention the little light...
But I've got nuthin'.
Hmm...
Regardless of all that, thank you for answering.

---

### Post by CHFFriday on 2007-11-29
Here is what I would try. Push the Radio button just one time. No lights my come on.
 
Then do the Code: sudo lshw -C network again. See if the radio comes on or if it is still off. If it is off, push the botton one more time the run the run it again.

You have to get the raido on for wireless to work.

Also post what type of Laptop you have. My guess is a HP.

CHFFriday

---

### Post by wirelessmonkey on 2007-11-29
Well, problem #1 is this

> 
david@david-laptop:~$ sudo ifconfig eth1 down

david@david-laptop:~$ sudo dhclient -r eth1



You turned off your wireless card, then tried to get a DHCP address with it.  Counter-intuitive.  

Either leave out the "sudo ifconfig eth1 down" line, or follow it with "sudo ifconfig eth1 up".   Taking the interface down is sometimes a good thing, acting as a reset and getting rid of odd ghosts and goblins.


If this doesn't help you, let me know.

---

### Post by superdave7380 on 2007-11-29
Nope, not an HP.
[B]
ACER TRAVELMATE 2420[/B]

Tried the ol' pushing the button once, and checking... nope.

Tried "sudo ifconfig eth1 up"... nope, wireless radio stays off.

How can  they expect Linux to be adopted by the masses when there's ALWAYS something that doesn't work right outta the box. I want to use Linux. I really do...

Can't one of you guys just come over here and fix it? Geez. It's probably something simple...

Thanks again anyways guys.

---

### Post by superdave7380 on 2007-11-29
PS -- When giving instructions, pretend I'm an idiot. (it would be far from the truth, anyway... ........ when it comes to Linux...)

---

### Post by bjarneh on 2007-11-29
usually there is some FN-key (often placed where the Ctrl-key should have been) which in combination with an F-<some-number>-key will get the radio-antenna up and running again, on my laptop its F5

---

### Post by superdave7380 on 2007-11-29
I've got the FN button... tried all the combos... bleh.
Though, on the flip side, I did find the combo that locks my touchpad! Thanks!

---

