---
title: "Help with internet access"
date: 2009-03-16
forum: New to Ubuntu
---

### Post by mksugg on 2009-03-16
Well, this is my first post. Installed Ubuntu 8.4 on a Dell Inspirion. I'm using a Linksys Wireless G notebook adapter WPC54G ver.2
The card is lit up and the Network Manager can see my router, but when I put in the WEP key the manager can't seem to make the connection. After trying a few times to put in the key the manager shuts down and the system freezes. Since the manager can see the router I have to believe that something needs tweeking to make the connection.
Anyone have a simple solution?

---

### Post by lindsay7 on 2009-03-17
It may be a setting in your router. Did you set it up or did someone else do it for you?

---

### Post by mksugg on 2009-03-17
I set it up.

---

### Post by lindsay7 on 2009-03-17
Try going into the setting of your router and make sure that you have your router set up to allow the adapter to connect with it. It could be that the adapter has to be on an access list or that the key or passphrase is not as you remember it. Do you know how to get into the router settings. I can guess for you if you do not.

---

### Post by mksugg on 2009-03-17
Yup, I have looked at the settings and know the wep key. Everything looks ok and I have two other computers connected to the internet through the router working fine.

---

### Post by lindsay7 on 2009-03-17
Ok, so much for my idea. I have trouble getting my wireless adapter to sign on ever though it was also seeing the signal from the router. I broadcased the ssid name and took the wep key off and established a connection on Ubuntu. Then I went back into the router and stopped broadcasting the ssid name and put the key back in place. It does not make sense but it worked. I have the usb version of your adaptor and it has been working well.

One other thing that seemed funny when I set my connection up, I had to add the Ubuntu wireless connection to my access list like it was another computer. I had the wireless adaptor showing with its MAC address for the windows conncection, but the router wanted to consider it like a new computer with a new computer name with the same MAC address for the Ubuntu connection.

---

### Post by mksugg on 2009-03-17
Well, thanks for trying, Lindsay. I really appreciate your response. I wish I knew more about networking. I hate to mess around too much with the settings on the router...don't want to screw up the connection for my other computers.

Anyone else have any bright ideas?

---

### Post by sleepyjon on 2009-03-17
Are you able to connect with WEP disabled?

What's the output of:

```

sudo lshw -C network

```

---

### Post by anewguy on 2009-03-17
Be sure you are selecting the correct bits and type - 64/128 hex or 64/128 ascii in the connect box from network manager.

dave :)

---

### Post by mksugg on 2009-03-17
> **sleepyjon said:**
> Are you able to connect with WEP disabled?

What's the output of:

```

sudo lshw -C network

```

Here is the output:

Hardware Lister (lshw) - b.02.12.01
usage: lshw [-format] [-options...]
lshw -version

-version   print program version (B.02.12.01)

format can be
-html    output hardware tree as HTML
-xml     output hardware tree as XML
-short   output hardware paths
-businfo output bus information

options can be
-class CLASS     only show a certain class of hardware
-C CLASS         same as '-class CLASS'
-disable TEST    disable a test (like pci, isapnp, cpuid, etc. )
-enable TEST     enable a test (like pci, isapnp, cpuid, etc. )
-quiet           don't display status
-sanitize        sanitize output (remove sensitive information   like serial numbers, etc. )

---

### Post by mksugg on 2009-03-17
> **anewguy said:**
> Be sure you are selecting the correct bits and type - 64/128 hex or 64/128 ascii in the connect box from network manager.

dave :)

Yep. I tried them all just to be sure.

---

### Post by mksugg on 2009-03-17
Beginning to wonder if I'll ever be able to solve this. There has got to be a solution!!

---

### Post by anewguy on 2009-03-17
Well, let's try something again that was requested earlier:

you attempt at lshw -C network failed -> for some reason given the output you did provide it looks like a syntax error.  So, please try again:

lshw -C network  <press enter> 

That starting character is a lower case "L", not a "1".  If possible, just copy and paste what I have here.  sudo is not actually needed, even though it will say you should run as su. So that's "lshw", as in "list hardware", followed by a space, then a dash ("-") and capital "C" as in cat, then a space, then the word "network".  If you get output like the last time showing the syntax available rather than the output, then you have typed it wrong.  

I'm also wondering if perhaps you have MAC filtering on your router - perhaps you set it up for the other PC's but haven't added the MAC address for this PC yet.  That would explain it rejecting even if the password is correct.

Another thing to try would be to temporarily turn off any encryption on the router and see if you can connect when the router is wide open.  If so, then the problem does lie in the password or passphrase somewhere.

Dave :)

---

### Post by mksugg on 2009-03-18
> **anewguy said:**
> Well, let's try something again that was requested earlier:

you attempt at lshw -C network failed -> for some reason given the output you did provide it looks like a syntax error.  So, please try again:

lshw -C network  <press enter> 

That starting character is a lower case "L", not a "1".  If possible, just copy and paste what I have here.  sudo is not actually needed, even though it will say you should run as su. So that's "lshw", as in "list hardware", followed by a space, then a dash ("-") and capital "C" as in cat, then a space, then the word "network".  If you get output like the last time showing the syntax available rather than the output, then you have typed it wrong.  

I'm also wondering if perhaps you have MAC filtering on your router - perhaps you set it up for the other PC's but haven't added the MAC address for this PC yet.  That would explain it rejecting even if the password is correct.

Another thing to try would be to temporarily turn off any encryption on the router and see if you can connect when the router is wide open.  If so, then the problem does lie in the password or passphrase somewhere.

Dave :)

Yup, Dave, you were right...I must have typed it wrong. Here is the output:

WARNING: you should run this program as super-user.
   *-network
        description: Ethernet interface
        product: BCM4401 100Base-T
        vendor: Broadcom Corporation
        physical id: 1
        bus info: pci@0000:02:01.0
        logical name: eth0
        version: 01
        serial: 00:0d:56:32:20:3f
        width: 32 bits
        clock: 33MHz
        capabilities: bus_master cap_list ethernet physical
        configuration: broadcast=yes driver=b44 driverversion=2.0 latency=32 module=ssb multicast=yes
    *-network
        description: Wireless interface
        product: ACX 111 54Mbps Wireless Interface
        vendor: Texas Instruments
        physical id: 0
        bus info: pci@0000:03:00.0
        logial name: wlan0
        virsion: 00
        serial: 00:14:bf:b2:c0:c5
        width: 32 bits
        clock: 33MHz
        capabilities: bus_master cap_list ethernet physical wireless
        configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+

Dave, I **really** appreciate your help.
Kent

---

### Post by anewguy on 2009-03-18
Hummmmm.......seems there are posts about a possible bug in one of the drivers for the ACX 111 (your wireless), but so far I haven't made heads or tails of it.  Here's what I'd like you to try:

reboot

try connecting

when it fails:

go to a terminal window (applications/accessories/terminal) and type (you may want to cut and paste this):

dmesg | tail <press enter> 

The "|" is not a lower case "L", but rather the piping symbol which on my keyboard looks like "--" turned 90 degress so it is vertical (on my keyboard it's on the key abouve the enter key).

Copy and paste the output back here.  The dmesg command is showing the system log, and piping it to tail forces it to only show the last few lines (I think technically it may be the last "n" characters).

Dave :)

---

### Post by mksugg on 2009-03-18
Dave, here are the results of
dmesg | tail
[  324.165165] acx: got IV_Failure (crypto) IRQ(s)
[  324.167936] acx: got IV_Failure (crypto) IRQ(s)
[  324.171060] acx: got IV_Failure (crypto) IRQ(s)
[  351.245782] acx: got IV_Failure (crypto) IRQ(s)
[  357.589040] acx: got IV_Failure (crypto) IRQ(s)
[  443.953571] acx: got IV_Failure (crypto) IRQ(s)
[  491.088709] acx: got IV_Failure (crypto) IRQ(s)
[  510.832547] wlan0: tx error 0x20, buf 06!
[  674.496917] wlan0: tx error 0x20, buf 03!

What do you think?
Kent

---

### Post by mksugg on 2009-03-18
Dave, you wrote

"I'm also wondering if perhaps you have MAC filtering on your router - perhaps you set it up for the other PC's but haven't added the MAC address for this PC yet. That would explain it rejecting even if the password is correct."

I simply don't know enough about the router settings to answer this. If you still think this could be the problem, could you talk me through how to handle this. (I did turn encyption off, but that didn't solve the problem.)

---

### Post by anewguy on 2009-03-18
First, you driver is failing.  I'll have to look more later (or you can do a search on this forum and in Yahoo or Google) for that chipset and see what they say about a driver.  When searching Yahoo! or Google, try using the search string ubuntu acx driver and see what turns up.  you may need to read through a LOT of pages, but that's what we do when we try to look things up.

As far as MAC filtering, ignore that for now - you have problems at the driver end for now.  MAC is a unique address for each piece of network equipment at the time of manufacture.  you can setup a wireless router to only allow those MAC addresses that you approve to connect to your network.  As mentioned though, right now your problem is with the driver.

Dave :)

---

### Post by mksugg on 2009-03-19
Well I took the advise and read a lot about the acx driver. One piece of advise was to disable Network Manager. I'm afraid to do that because I won't know how to reenable it if that doesn't work. It also says, I think, that the driver and firmware for the chipset I have comes with Ubuntu. Is that so? Where to go from here?

---

