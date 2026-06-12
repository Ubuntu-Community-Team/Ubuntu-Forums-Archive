---
title: "Absolutely a beginner, help?"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by Kiveya on 2009-03-06
I'm a real complete beginner at this stuff... but I am quick and willing to learn. However, most of the searches I've found assume a greater working knowledge of ubuntu than I currently have. I need help.  :confused:

So here's this: I have downloaded NDISwrapper and the driver for my wireless card onto a usb drive - because as best as I've been able to figure out from these forums, the lack of these items are the reason why my laptop is blind to any and all wifi access points.

I can access the terminal and even manage a few really elementary commands to navigate around directories... in a very timid sort of way.

I'm at loss now. I don't know where to go from here. I've read a few threads that supposedly walk you through installing stuff and they have failed me.

Can someone please help me? I am willing to learn, good at following directions, and very very humbled by my experience with this operating system thus far (in a good way!)

Reply here, pm me, or ding me on aim: kiveya

---

### Post by Kareeser on 2009-03-06
Hi Kiveya!

Before we begin, can you type "lshw -C network" into the terminal and paste what it says into a reply?

You can select text with the mouse, and copy with "Control-Shift-C", similar to Windows, but added a shift.

---

### Post by Kiveya on 2009-03-06
Hi Kareeser, thanks for helping me out!  Did I mention I wasn't posting via my ubuntu computer? Wups...

First, let me update my status. I found some more help on the forums and ended up connecting my laptop via ethernet and downloaded tons of updates (what can I say? I didn't know!). One of which included a driver for the wireless card.  I even got Wine installed (I think?). 

Still unable to connect to my wifi though, even after checking my router settings and double-checking, etc.

Let me hook up the laptop again and I'll be able to copy/paste the results of that command here.

---

### Post by Kiveya on 2009-03-06
davena@Laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Network controller
       product: BCM4312 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb
  *-network
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: eth0
       version: 02
       serial: 00:19:b9:56:5a:e5
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=b44 driverversion=2.0 ip=192.168.1.101 latency=64 module=ssb multicast=yes
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:19:7d:7e:69:e3
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: be:8a:51:1f:e2:86
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
davena@Laptop:~$ 



Ok, how's that?

---

### Post by cptr13 on 2009-03-06
I have the same card, it shouuld work out of the box after the updates.

However, you need to activate it within "restricted drivers"
Its under "system", I don't remember which area but easy to find.

open restrictedd drivers, activate the broadcom driver (you'll need your ethernet running for this because it downloads information).

I suspect you'll be up and running after that.

or...did you already do that part?

---

### Post by ClaytonOT on 2009-03-06
> **cptr13 said:**
> I have the same card, it shouuld work out of the box after the updates.

However, you need to activate it within "restricted drivers"
Its under "system", I don't remember which area but easy to find.

open restrictedd drivers, activate the broadcom driver (you'll need your ethernet running for this because it downloads information).

I suspect you'll be up and running after that.

or...did you already do that part?

I suspect you're refering to System>Hardware Drivers?

(Just trying to help out OP)

---

### Post by cptr13 on 2009-03-06
yep exactly.  Sorry I didn't check that before I posted.

---

### Post by Kiveya on 2009-03-06
:(  So far no go...

Under Hardware Drivers it gives me two choices. Broadcom b43, or Broadcom STA.  Well STA apparently does nothing useful I can see? My options for Wireless Network are completely gone...

So B43 seems the right path, but I get my wireless security info in there and it tries and tries and tries and tries to connect, and fails?

---

### Post by stalkier on 2009-03-06
> **Kiveya said:**
> :(  So far no go...

Under Hardware Drivers it gives me two choices. Broadcom b43, or Broadcom STA.  Well STA apparently does nothing useful I can see? My options for Wireless Network are completely gone...

So B43 seems the right path, but I get my wireless security info in there and it tries and tries and tries and tries to connect, and fails?

I had to mess with mine a little bit on my laptop. Try restarting a few times to see if that works.Make sure100% that you have enabled the device (wifi card). If that does not work you could always use a BFH.

---

### Post by Kiveya on 2009-03-06
> **stalkier said:**
> I had to mess with mine a little bit on my laptop. Try restarting a few times to see if that works.Make sure100% that you have enabled the device (wifi card). If that does not work you could always use a BFH.

BFH?


I did make several restarts. After several attempts with multiple security options, I've managed a connection.  Except I can only connect if I leave the wireless unsecured!  Frustratingly if I turn on WEP or WPA, the laptop won't connect. It'll keep coming back to asking for the authentication and gives me the little window to put in the key or passphrase. I've tried all the router options and the laptop won't accept any of them.

---

### Post by Kiveya on 2009-03-06
Ok, strangely it's working now. With security. I'm going to hope it doesn't change, because at this point I don't know what made it work, but as long as it continues to do so I'll be ok...

Thank you every one that pitched in to help me!

---

