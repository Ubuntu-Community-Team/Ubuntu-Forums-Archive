---
title: "network card driver problem / module: skge"
date: 2007-08-04
forum: Networking &amp; Wireless
---

### Post by christian_johansson on 2007-08-04
If I try to copy a large file, say 1 gigabytes big, it will go fast for the first 350 megabytes (30-40 mbps). After that, the transfer will basically 'crash'. It drops down to about 1-2 mbps, and stays there for the rest of the file.
Its the exact same every time I try it. First 350 mb:s at 30-40 mbps, then drop to 1-2 mbps, so its easily repeatable.

NIC: Marvell Ykon 1 gb NIC, embedded in motherboard. It runs in full duplex mode. I have a gigabit switch. The gigabit connectivity light is lit on the switch for my NIC.

The computer I am trying to copy the file to is a simpleshare NAS. I have tried mounting the drive on the NAS with both CIFS and NFS, which results in the exact same 350-mb fast-transfer-then-stall scenario.
I have also tried smbfs, but with that I only get 2-3 mbps even from the start of the file.

The simpleshare NAS only has a 100 mbps NIC, so I am not expecting gigabit speeds. 100 mbps speeds would be nice, but I am willing to settle for 30-40 mbps, if it will just be stable.

The module / driver for my NIC is skge.

I _suspect_ that it is the skge driver that bails out and causes the slowdown after 350 megabytes is transferred. I suspect this because the marvell cards seems to have a history of instability and poor functionality under Linux.

Does anyone know whats going on here?
Can anyone confirm if the skge driver is or is not at fault here?

lspci -vv output for the NIC:

00:0a.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)
        Subsystem: ASUSTeK Computer Inc. Marvell 88E8001 Gigabit Ethernet Controller (Asus)
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz+ UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (5750ns min, 7750ns max), Cache Line Size: 64 bytes
        Interrupt: pin A routed to IRQ 17
        Region 0: Memory at f9a00000 (32-bit, non-prefetchable) [size=16K]
        Region 1: I/O ports at a800 [size=256]
        Expansion ROM at f9900000 [disabled] [size=128K]
        Capabilities: [48] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold+)
                Status: D0 PME-Enable- DSel=0 DScale=1 PME-
        Capabilities: [50] Vital Product Data

-----------------------
Thanks.
CJ

---

### Post by noob12 on 2007-08-04
My desktop box is on Feisty with skge 1.9. I've got the Marvell 88E8001 on an ASUS motherboard.  I'm running gigabit with jumbo frames across client and server (which has the same chipset and driver).   I can measure roughly 700+mbps with ftp on files of size about 400MB; I get about 500+mbps with smbget.  (Samba in Nautilus sucks for some reason; it won't go faster than about 90mbps even in this setup; I still haven't figured that out.)

I'll test out some much larger files and get back to you.

In your case the asymmetry may be killing you.  It sounds like you are pushing from the gigabit side.  This is likely to be the poorer direction.  (For comparison copy a file back and see what happens.)  My guess is that you're either getting buffer overruns at the switch or that your TCP window size on the connection is getting shrunk way down due to buffer overruns on the receiving end.  The latter seems more consistent with the degradation pattern.

Problems at the switch might be visible using **ifconfig** dropped/overrun/errors counts compared before and after such a transfer.

It sounds like your NAS probably is not very configurable.  If you can't up buffer sizes there, and you don't have a lot of other gigabit-equipped hosts on your net.  You might want to experiment with forcing the adapter link rate *down* on the gigabit side to 100mbps using **ethtool**.  This may actually improve your overall transfer times.  Assuming your adapter's logical name is eth0, the command would be:

```

sudo ethtool -s eth0 speed 100 duplex full autoneg off

```

If you find this does help, you can put the ethtool invocation in a pre-up in /etc/network/interfaces.

---

### Post by christian_johansson on 2007-08-06
Thanks for your suggestions, noob12.

I tried forcing my NIC down to 100 mbit like you suggested, and that didn't make any difference.
Then I tried a different switch (a 100mbit switch). Still no difference.

I will check the ifconfig stats soon, right now something wierd is going on and when I mount the NAS, I only get told that I don't have permissions to either read or write files to it, although my user owns the dir its mounted in. Weird!

You are right about that I can't configure the NAS much. Its a simpleshare 500g NAS (running a modified busybox distro I think). I've seen some posts here and there talking about some other firmware you can load on this NAS to gain more control. Perhaps the problem lies at its side. It would be nice to be able to ssh into it and check things out, rather than just having the pretty useless web interface.

---

### Post by noob12 on 2007-08-06
Did you try pulling files from the NAS to see if there is a significant difference?

---

### Post by christian_johansson on 2007-08-06
Yep just tried downloading from it, that gives me a seemingly stable transfer rate at about 40 mbits (5-6 mb / s).

There are no dropped / overrun / drops reported by ifconfig for the nic.

One hint at that something must be pretty wrong here is that if I start an upload (which will go very fast in the beginning, 200 mbits (20 mb / s, I miscalculated this in my head when I wrote the first post here), in essence it maxes out the NAS connection completely at first which is good. But once I reach approx 350 megabytes, it will slow down or even stall like I said.
If I cancel the operation at this point, the connection to the NAS will freeze up completely for a minute or so. Any app that tries to communicate with it after that will hang for at least a minute.

What do you think would cause this?  Its like the connection gets 'overheated' and then jams up! :p

---

### Post by christian_johansson on 2007-08-06
I should also mention that once the speed has gone down on the device, it will stay as slow for all consecutive uploads to it. Only if I unmount and remount the NAS will it come back and be fast again for the first 350 megabytes.

---

### Post by noob12 on 2007-08-06
Because pulls work fine, my guess is that this has more to do with running into TCP-level limitations on the receiving end (the NAS) when data is pushed just slightly faster than it can actually handle.

Have you also tried a put using smbclient?

The fact that things come back to normal after a remount suggests that it is not a device-level network issue, but rather tied to something whose scope is the same as the mount.  I think that one smbfs mount uses a single TCP connection, which would be consistent with the TCP window hypthosis, but I'm not sure.  The total lockup might also be a bug in smbfs; when used with moderate traffic a connection should eventually get back to normal window sizes.

You could try to look at window sizes from a tcpdump trace on a push and maybe look at **cat /proc/net/netstat** values that change during the push.  You might try to test with the other congestion avoidance methods like 'vegas', 'westwood' or 'BIC'  (see **man 7 tcp**) and see if it makes any difference.

Sorry, no more ideas.

---

### Post by christian_johansson on 2007-08-07
I get the same symptom using smbclient.

It seems to me its the NAS at fault here anyways, not the NIC driver.

Thank you for your insightful tips on what else I can try, by changing tcp congestion settings and such. I think I've reached the time limit I'm willing to spend on getting this working however, so I think I will send it back to amazon and get a different NAS instead.

---

