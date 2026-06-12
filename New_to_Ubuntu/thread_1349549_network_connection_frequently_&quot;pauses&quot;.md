---
title: "network connection frequently &quot;pauses&quot;"
date: 2009-12-08
forum: New to Ubuntu
---

### Post by AlphaWhelp on 2009-12-08
There is a really irritating problem I have with this computer where the network connection I am uses frequently pauses, pretty much as if a firewall has decided to block all traffic for a few seconds.  This is barely noticable when I am browsing the internet, but when I am accessing network drives, sometimes even clicking on a different folder can take a long time to load and it's getting annoying.  Can someone help me with this?  I'm using some kind of integrated wireless adapter, I'm not sure which one it is, though, and not sure how I would go about finding out which one it is.

---

### Post by ukripper on 2009-12-08
can you explain more about your network drives. Are they formatted in FAT, NTFS, EXT3 or EXT4? Are you accessing drives via samba or NFS?

---

### Post by AlphaWhelp on 2009-12-08
the network drives are NTFS but even when I'm downloading from the internet my downloads will pause for a few seconds frequently.

---

### Post by ukripper on 2009-12-08
sounds very much of a ipv6 issue. Some routers don't support ipv6 by default.

Can you try below in firefox:


1. Type about:config in your address entry bar (in firefox)
2. Type "ipv6" in the filter
3. Change the value of "network.dns.disableIPv6" to true

if it works fine for you and you see no download freezing issues, then we go from there.

---

### Post by AlphaWhelp on 2009-12-08
well this router is old enough that it definitely doesn't support ipv6 but when I inspect this network under the network connections configuration, ipv6 is set to "ignore" do I still have to disable it somewhere else?

---

### Post by AlphaWhelp on 2009-12-08
I disabled it regardless and the internet downloads still pause, sometimes they pause after every meg, sometimes it gets as high as 20 megs before it pauses.

---

### Post by ukripper on 2009-12-08
i believe your wireless card is atheros based. Had heard drivers problem with them. Can you post output of this command:
```
lspci
```

---

### Post by AlphaWhelp on 2009-12-08
yeah you were right, it is Atheros

```
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02)
01:00.0 Ethernet controller: Attansic Technology Corp. Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```
/\ there it is...

Is there a fix?

---

