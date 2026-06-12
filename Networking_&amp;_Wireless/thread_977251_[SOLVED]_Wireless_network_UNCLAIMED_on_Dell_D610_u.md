---
title: "[SOLVED] Wireless network UNCLAIMED on Dell D610 using Ubuntu 8.10"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by nrobinson on 2008-11-10
After installing installing ubuntu 8.10 the other day I have been unable to access any wireless networks either at home or at work.

There is no option to enable wireless networking when the network manager icon is right clicked, nor can any networks be seen in System -> Administration -> Network Connections -> wireless (tab).

sudo lshw -C network produces the following output

>   *-network               
       description: Ethernet interface
       product: NetXtreme BCM5751 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:14:22:d2:c2:a3
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5751-v3.29a latency=0 link=no module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network UNCLAIMED
       description: Network controller
       product: PRO/Wireless 2915ABG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:03:03.0
       version: 05
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=64 maxlatency=24 mingnt=3
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: e2:fe:aa:79:e7:5c
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

The wired network fine when an ethernet cable is connected.

Any help would be much appreciated.

Regards,

Nathan

---

### Post by ciscosurfer on 2008-11-10
Does this laptop have a wireless killswitch?  Is it enabled (meaning wireless is disabled)?  Is [this part of the problem]("http://www.ubuntu.com/getubuntu/releasenotes/810#Cannot%20reactivate%20Intel%203945/4965%20wireless%20if%20booting%20with%20killswitch%20enabled")?

---

### Post by nrobinson on 2008-11-10
It does have a kill switch. This switch is connected to with the std wireless and the bluetooth. It can be turned on/off with Fn+F2. This only affects the bluetooth light but affects the wireless devices on/off status in the bios and the presence of a bluetooth icon in the top right info bar. 

The problem persists regardless of the on off state of the wireless system.

Hope this answers your question,

Nathan

---

### Post by ciscosurfer on 2008-11-10
And what about the other known issue link I posted?  Does it apply to you?  Is there a physical killswitch, like a toggle on the side or do you just use a key combo?  I'm just throwing ideas out there...

---

### Post by nrobinson on 2008-11-10
There is no physical kill switch, just a key combo.

I failed to follow the hyperlink in your comment before. I have done so now and noted the point about the wireless being enabled upon boot. 

I Enabled wireless, disconnected ethernet, restarted and the problem persists.

---

### Post by ciscosurfer on 2008-11-10
Hmm.  Well, [this link should help you]("http://www.google.com/search?hl=en&q=site%3Aubuntuforums.org+dell+d610+8.10+wireless&btnG=Search") peruse the forums via a keyword search on google.  Using the Advanced Search functions are also helpful there.  Sorry :-(

---

### Post by ciscosurfer on 2008-11-10
> **nrobinson said:**
> There is no physical kill switch, just a key combo.

I failed to follow the hyperlink in your comment before. I have done so now and noted the point about the wireless being enabled upon boot. 

I Enabled wireless, disconnected ethernet, restarted and the problem persists.I believe the Release Notes say in that situation to leave the killswitch in the "off" position when booting up (if this is truly your chipset)...I could have read it wrong though.

---

### Post by ciscosurfer on 2008-11-10
nrobinson, I found [this thread]("http://ubuntuforums.org/showthread.php?t=973552") and it may speak to your issues.  You should pop over there and take a look.

---

### Post by nrobinson on 2008-11-10
Thanks,

I am following the advice there and will see how it goes. 

if it helps:

the command iwconfig produces the output
> lo          no wireless extensions.
eth0               no wireless extensions.
pan0               no wireless extensions.

---

### Post by nrobinson on 2008-11-10
Also about your previous comment:


The guide quotes

> ...starting the system with the killswitch enabled (i.e., with wireless disabled) will prevent re-enabling the wireless by toggling the killswitch. 

---

### Post by ciscosurfer on 2008-11-10
Isn't wordplay fun?  enabled, disabled, prevent, re-enabled...oh my head...Just for the sake of it, have you tried the reverse?  It's probably not a definitive test, but you may as well try it out (in both directions) to allow the prevention of enablement via the toggling of the flux capacitor.  

I think it's time for me to go night-night. :lolflag:

---

### Post by nrobinson on 2008-11-10
Trying as we speak. I don't hold out much hope though.

Good night.

---

### Post by ciscosurfer on 2008-11-10
It is worthy to mention that Ubuntu Forums also has a sub-forum called [Dell Ubuntu Support]("http://ubuntuforums.org/forumdisplay.php?f=342").

---

### Post by nrobinson on 2008-11-10
The latest auto update fixed all problems.

Thanks.

---

### Post by ciscosurfer on 2008-11-10
> **nrobinson said:**
> The latest auto update fixed all problems.

Thanks.That's awesome!  Glad to hear it!

---

