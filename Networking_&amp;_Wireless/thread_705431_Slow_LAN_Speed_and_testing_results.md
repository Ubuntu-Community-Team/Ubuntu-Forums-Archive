---
title: "Slow LAN Speed and testing results"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by najames on 2008-02-23
I want to build an unRAID server to back up large amounts of data and serve media, but it is dependant on fast LAN access.  I have many computers, but started with the two newer PCs to verify LAN speeds using onboard chips.

This video shows how to use Iperf, a common tool for measuring LAN speed.  I decided to use it as a performance verification tool.  [http://www.netpsa.com/videos/iperf.html](http://www.netpsa.com/videos/iperf.html)

I installed iperf with Synaptic, then i downloaded current Realtek Linux drivers for both LAN chips and installed them.  I ran tests on both computers as servers and clients.  One computer has a Gigabyte GA-MA69GM-S2H motherboard with a Realtek 8110SC LAN chip and the other has a BIostar TA690G motherboard has a Realtek 8111B LAN chip.  All systems are connected with a SMC Gigabit 8505T 5port switch.  Both PCs are running Mint Daryna (32bit).

Running iperf revealed that one or both these LAN chips are very slow, server/client roles were both similar to this. 

Client connecting to 192.168.1.109, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  6] local 192.168.1.101 port 39037 connected with 192.168.1.109 port 5001
**[  6]  0.0-10.0 sec  16.7 MBytes  14.0 Mbits/sec**
**[  5]  0.0-10.1 sec    212 MBytes    176 Mbits/sec**

I tried using Nautilus to copy a Linux ISO file from a Samba, it goes at about 8MBps.  I tried using smbget and got about 14MBps, still very slow for gigabit parts.  

Then I installed an older Trendnet TEG-PCITXR Gigabit LAN card, which uses a Realtek 8169 LAN chip, on the Gigabyte motherboard.  Linux recognized the card, but I couldn't use it, even with the onboard chip disabled.   I found that if I moved the card to the outer slot on the  Gigabyte GA-MA69GM-S2H board, it would work.   There must be an interrupt conflict using the inner PCI slot.  This is the Iperf results from using the PCI Trendnet card and current drivers, 2.5 times a fast as the onboard LAN.  

Client connecting to 192.168.1.106, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  5] local 192.168.1.101 port 41224 connected with 192.168.1.106 port 5001
[  4] local 192.168.1.101 port 5001 connected with 192.168.1.106 port 43096
[B][  5]  0.0-10.0 sec  37.8 MBytes  31.7 Mbits/sec
[  4]  0.0-10.0 sec    542 MBytes    453 Mbits/sec[/B]

Natulis Samba copies got 25-30MBps with this Trendnet card in another PC with a failing RAID5, coypying back to the Biostar 8111b.  All LAN chips do not seem to be created eual!! 

In a search for faster throughput I wanted to try an Intel based PCI-e x1 LAN card is next, oops got an Intel PCI card too from a trip to TigerDirect.

IPERF server on Biostar Realtek onboard 8111b, 
cleint on WinXP MSI Neo2 Platinum Nforce3 running Intel Pro1000 in a PCI slot 

Client connecting to 192.168.1.101, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  5] local 192.168.1.101 port 1197 connected with 192.168.1.101 port 5001
[  4] local 192.168.1.101 port 5001 connected with 192.168.1.101 port 52572
[B][  5]  0.0-9.5 sec     725 MBytes    638 Mbits/sec
[  4]  0.0-10.2 sec    153 MBytes    125 Mbits/sec[/B]

Iperf server on Gigabyte board using Trendnet TEG-PCITXR gigabit card, cleint on WinXP MSI Neo2 Platinum running Intel Pro1000 PCI card

Client connecting to 192.168.1.106, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  5] local 192.168.1.107 port 1035 connected with 192.168.1.106 port 5001
[  4] local 192.168.1.107 port 5001 connected with 192.168.1.106 port 34999
[B][  5]  0.0-10.0 sec    525 MBytes    440 Mbits/sec
[  4]  0.0-10.2 sec    120 MBytes    98.1 Mbits/sec[/B]


Iperf Server running on the A8N-E with PCI-e x1 Intel Pro1000, client is the Biostar 8111B onboard.  I downloaded the Linux driver for the Intel Pro1000 chip and installed it in Mint Daryna.  Things are getting speedy here, now I need to find a way to make it fast both ways.  The Realtek 8111b has redeemed itself here.

Client connecting to 192.168.1.108, TCP port 5001
TCP window size: 16.0 KByte (default)
------------------------------------------------------------
[  4] local 192.168.1.101 port 5001 connected with 192.168.1.108 port 57392
[  5] local 192.168.1.101 port 36236 connected with 192.168.1.108 port 5001
[B][  5]  0.0-10.0 sec  1011 MBytes    849 Mbits/sec
[  4]  0.0-10.0 sec    204 MBytes    170 Mbits/sec[/B]

This is a couple days worth of hacking around and I feel like I've only scratched the surface.  I have not looked at Iperf nor gotten into settings for the cards, especially the Intel PCI-e x1 card.  Everything is configurable and I am running it at all default settings.  I have about 10 LAN chips here in various boxes and have only documented a few.   If others of importance come along I will share them.  I think the server I have with dual Broadcoms might be interesting to add in the mix.  Right now, I'd say that little x1 Intel card is the big dawg.

Time for an update.  This is "real world testing" after the initial examples. 

All tests were done with either Mint Linux (based on Ubuntu 7.10) or Ubuntu 8.04 with current drivers installed.  File being transferred is a Linux Mint 4.iso (full CD).

**Server used:**
Asus A8N-E with Intel Pro1000 running on PCI-e x1 slot, default settings

**Clients used:**
Biostar TA690 with Realtek 8111b running on the PCI-e bus
Gigabyte GA-MA69GM-S2H with Realtek 8110SC running on PCI bus
MSI Neo2 Platinum with onboard Marvell 88E1111 running on Nforce3 bus
MSI Neo2 Platinum with onboard Realtek 8110S runnning on PCI bus
MSI Neo2 Platinum with Trendnet Realtek 8169S card on PCI bus
Gigabyte GA-MA69GM-S2H with Intel Pro1000 card running on PCI bus

**Protocol for transfer - smbget command**

Asus Intel Pro1000 to Biostar 8111b - 35.984sec @ 19.13MBps
Biostar 8111b to Asus Intel Pro1000 - 34.444sec @ 19.99MBps

Asus Intel Pro1000 to Gigabyte 8110SC - 47.505sec @ 14.50MBps
Gigabyte 8110SC to Asus Intel Pro1000 - 56.785sec @ 12.12MBps

Asus Intel Pro1000 to Gigabyte 8110SC - 47.505sec @ 14.50MBps
Gigabyte 8110SC to Asus Intel Pro1000 - 56.785sec @ 12.12MBps

Asus Intel Pro1000 to MSI Trendnet 8169S card - 30.765sec @ 22.39MBps
MSI Trendnet 8169S card to Asus Intel Pro1000 - 30.276sec @ 22.39MBps

Asus Intel Pro1000 to MSI Marvell 88E1111 - 24.302sec @ 28.33MBps
MSI Marvell 88E1111  to Asus A8NE Intel Pro1000 - 27.663sec @ 24.89MBps

Asus Intel Pro1000 to MSI Realtek 8110S - 23.638sec @ 29.13MBps
MSI Realtek 8110S  to Asus A8NE Intel Pro1000 - 26.546sec @ 25.94MBps

Gigabyte Intel Pro1000 PCI slot to Biostar 8111B - 30.763sec @ 22.387MBps

Asus PCI-e x1 Intel Pro1000 to Gigabyte Intel Pro1000 PCI slot - 26.062sec @ 26.42MBps

I was really surprised at how the "old 2004 hardware" was faster than the newer stuff.  

I was **NOT** satisfied with the speed from using SMB so I installed PureFTP on the "server" via Synaptic, FileZilla on all the clients (no other mods), and re-ran some of the tests.  I used the same Mint 4.iso file to transfer.  Statistics were generated by FileZilla.

**Protocol for transfer - FTP GUI**

Biostar 8111b to Asus Intel Pro1000 - 18.136sec @ 37.97MBps
Asus Intel Pro1000 to Biostar 8111b - 16.462sec @ 41.83MBps

MSI Realtek 8110S to Asus Intel Pro1000 - 18.136sec @ 37.97MBps
Asus Intel Pro1000 to MSI Realtek 8110S  - 27.236sec @ 25.28MBps

MSI Marvell 88E1111 to Asus Intel Pro1000 - 20.095sec @ 34.27MBps
Asus Intel Pro1000 to MSI Marvell 88E1111 - 27.272sec @ 33.97MBps

Gigabyte 8110SC to Asus Intel Pro1000 - 36.315sec @ 18.96MBps
Asus Intel Pro1000 to Gigabyte 8110SC - 15.870sec @ 43.39MBps

Notice that the FTP protocol is much faster than the SMB protocol.   Surprisingly, there is no pattern in predicting system performance from one test to another.  Overall the Biostar 8111B to Asus Intel Pro server was the fastest combination in FTP. 

I ran tests twice on the Gigabyte board to try and understand why it is a total slug in sending FTP data to the Asus server, but screams like the village idiot in receiving data, no explanation.  I do not trust the Realtek 8110SC chip.

My goal is finding a reliable setup that will run transfers of at least 60MBps, don't know if I'll make it.

---

