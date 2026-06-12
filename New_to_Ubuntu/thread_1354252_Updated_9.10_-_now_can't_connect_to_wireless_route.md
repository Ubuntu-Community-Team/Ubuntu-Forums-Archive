---
title: "Updated 9.10 - now can't connect to wireless router"
date: 2009-12-13
forum: New to Ubuntu
---

### Post by flopwich on 2009-12-13
[FONT=Arial]I had Ubunto 8.10 and everything worked fine.  Then I upgraded to 9.10 and both Firefox and Evolution stopped connecting to the internet.  I found a clue on here that you could tell Firefox to use IPv4 only and not IPv6.  When I made that change, both Firefox and Evolution started working, for some reason.  

Yesterday I ran update manager and updated my system.  At first Firefox worked fine, but Evolution couldn't find the mail server, even though I could ping it and traceroute to it.  Earlier today I could make a connection to my wireless router, but it would then drop the connection in a matter of a minute or so.  Now I can't connect wirelessly even when I took the computer and sat two feet from the wireless access point.  (I'm using a Windows machine right now that is connecting to the same router at the same time the Ubuntu machine says it can't.  The two machines are side by side.)  I don't know where to begin to figure out what's wrong.  I've tried unplugging the wireless access point, then plugging it back in.  I've tried turning my DSL router off and on.  I've re-booted Ubuntu a number of times, including turning the computer off and trying again later.

The computer is an Acer Aspire One netbook.  I have it set up as a dual-boot machine with XP on it.  The connection to my wireless router works fine on the Windows side.

TIA for any help.
[/FONT]

---

### Post by yeats on 2009-12-14
This could actually be a router issue, not an issue with Ubuntu.  Your router should have logs that you can view about access and access attempts.  Try and see what the router says at the times when you attempted to connect.  It may think you're attempting a spoof attack.

---

### Post by nothingspecial on 2009-12-14
Another possibility is that a kernel update broke your wireless, it happens.

Try booting into the previous one.

---

### Post by ukripper on 2009-12-14
can you post output of this command, i can smell Atheros chipset:
```
lspci
```

---

### Post by aimpau on 2009-12-14
Same example here:

9.04 --> My HP TouchSmart's wireless capabilities are excellent

9.10 --> Doesn't even detect wifi signals



Reason? (My un-geek reason)
When I check hardware drivers in System-->Admin, you have to enable a propriety driver. It only means that in 9.04, it was using a generic driver but now in 9.10, it will now be using a brand new, actually-made-or-shared-by-the-manufacturer driver. Try yours if it will help. :)

---

### Post by flopwich on 2009-12-14
> **chrissharp123 said:**
> This could actually be a router issue, not an issue with Ubuntu.  Your router should have logs that you can view about access and access attempts.  Try and see what the router says at the times when you attempted to connect.  It may think you're attempting a spoof attack.

Well, I'm not sure what's going on.  I got into my router and turned on the log.  When I tried to connect, the computer showed it connected, then disconnected as soon as I opened Firefox.  I checked the log on the router, and it showed that the computer tried to connect to 91.189.94.4.  Under "port", the log listed "ntp".  Then I logged into Windows on the same computer (it's double-boot with Ubuntu) and everything worked just fine.

That IP address, according to WHOIS, is "Douglas in United Kingdom", with ISP Canonical, by the way.  I have no idea why it would be trying to connect to that address, but it's a dead link, anyway.  I couldn't connect to it with from the Windows side, either.

---

### Post by flopwich on 2009-12-14
"Another possibility is that a kernel update broke your wireless, it happens.

Try booting into the previous one. "

I have no clue how to do that.  Could you loan me one?

Thanks.

---

### Post by flopwich on 2009-12-14
> **ukripper said:**
> can you post output of this command, i can smell Atheros chipset:
```
lspci
```

Here you go:

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
01:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)

---

### Post by flopwich on 2009-12-14
> **aimpau said:**
> Same example here:

9.04 --> My HP TouchSmart's wireless capabilities are excellent

9.10 --> Doesn't even detect wifi signals



Reason? (My un-geek reason)
When I check hardware drivers in System-->Admin, you have to enable a propriety driver. It only means that in 9.04, it was using a generic driver but now in 9.10, it will now be using a brand new, actually-made-or-shared-by-the-manufacturer driver. Try yours if it will help. :)

Remember that we're in the "I don't know my butt from a hole in the ground" section here. ;-)  I looked in System, but could find no Admin.  Could you give me a bit more to work with?  Thanks.

---

