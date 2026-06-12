---
title: "General Network and System Issues"
date: 2006-08-15
forum: Networking &amp; Wireless
---

### Post by nildot on 2006-08-15
Hello all,

First off: I'm a newbie. Take it easy on me, yes? :)

Now, I have several issues since a couple of days. I think they started appearing while I was trying to figure out how Ubuntu runs/configures my wifi connection. I found it quite a bit confusing.

Then it all started to break down.

First of all here is my network setup:

Most of the time eth0 (my regular ethernet connection) is connected to the company network and the company's DHCP. All seems fine there.

eth1 (intel pro wireless bg 2200) on this IBM thinkpad r50e, connects to a netgear router with its DHCP activated (192.168.x.x)

While messing around, I suddenly noticed that when I'm trying to call up the Network Settings (System - Administration - Networking or simply by clicking on the Network monitor on the screen, selecting the device and clicking on "Configure") the interface would take incredibly long to load. The basic frame of the window would appear and then it would take easily 4 minutes to finally show me the devices.

Once it displays properly I noticed that no matter how many times I try to deactivate the device I thought was causing the problem, it would be active again the next time I checked the Network Settings.

So I tried to reboot. Hah. No-go. The entire machine doesn't reboot/shut down properly anymore. It takes very long to even load the GUI for reboot/shut down and when I finally make my choice, the system would freeze while trying to close some application such as Mozilla Thunderbird.

Fine, so I force a shutdown of my IBM and restart. I notice that not only does it fail to "Deconfigure Network Devices", but it also fails to initiate them on a reboot.

Starting Basic Network Failed
Configuring Network Interfaces Failed.

However, when the system booted completely, I found my eth0 connection to work just fine. I was internet-connected and the rest of the network worked fine as well. Though, I still have the problem of not being able to get into Network Settings without waiting for ages. Disabled devices still return to being activated. Shutdown -still- doesn't function properly.

I manage to reboot again, after I somehow, for no apparent reasong lose my internet connection. After seeing the same Failure messages as last time, the system boots up and I notice that my network connections aren't even configured this time. They'are somehow gone. No networking devices found.

I try sudo dhclient.

That solved it. But only for now. All my other described problems still persist.

Does anyone know what I might have broken?
Does anyone know how to fix it?

Or am I just better off backing up my data and reinstalling ubuntu?

I'd appreciate your help, guys.

Thanks,

nildot

---

### Post by nildot on 2006-08-15
I forgot to mention something:

My "lo" has vanished. I can't find it anymore. Not in ifconfig nor in the Network Settings GUI.

I hate not knowing my way around a system. I should really do some more reading on the documentation.

---

### Post by nildot on 2006-08-15
Ah well.

The problem was too annoying to sit around and wait. I couldn't find any conclusive answers anywhere else so I simply reinstalled the system. Things are just dandy, now.

However, for future reference, a possible solution would still be welcomed.

Regards,

nildot

---

