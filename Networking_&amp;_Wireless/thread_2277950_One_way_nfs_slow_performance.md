---
title: "One way nfs slow performance"
date: 2015-05-12
forum: Networking &amp; Wireless
---

### Post by xeddog on 2015-05-12
I have computers that run SABnzbd+, SickBeard, and CouchPotatoServer (with different usenet providers).  When these computers complete downloads they move the files from local storage to a Popcorn Hour A410.  According to the system monitor I am seeing a transfer rate of about 500-600[COLOR="#FF0000"]K[/COLOR]Bps.   I have been battling this nfs performance problem for quite some time now with no resolution.  I have tested using sync/async, tcp/udp, various rsize/wsize from 1500 though 32K, and nfs version.  Nothing seems to make any difference.  

But I have found out that this performance problem is one way.  From a computer, I can open two file manager windows.  One for local storage, and one for the A410 storage.  If I drag-and-drop a large file from the computers local storage to the A410, I get just under 1MBps transfer rate which is unacceptable.  If I drag-and-drop a large file from the A410 storage to the computer's local storage, I get around 40MBps which is quite acceptable, and probably about all the A410 can handle.   But even at that, the graph that the system monitor shows is all over the place.  It never shows a constant rate looking more like the outline of a mountain range.  The ifconfig on the A410 shows a few framing errors.  When I started a 6GB file transfer there were 28 errors, and when it finished there were 29.  If I drag-and-drop between the two linux machines, it's all good both ways.

All this started last year when I upgraded the two computers from Ubuntu 13.10 to 14.04.  One of the machines was an upgrade, the other was a fresh install of 14.40.  Also at that time I had a Popcorn Hour A210 which just recently died and was replaced with the A410.  Also since then, all network components have been replaced.  All cabling is new except for one cat5 cable between two switches.  I would like to replace this cable but access and complexity don't allow it.  At any rate, I don't think this is an issue since I can get satisfactory transfer rates with ftp, and also from the A410 to the computer.

I've said a lot, but the bottom line is that the nfs performance from computer to A410 is poor.  I have an open case with CloudMedia (the company that sells the PCH), and they have no answer.  So what can I look at on the linux side to find out why this is happening?


Thanks,

Wayne





Computer 1 -
Recently Upgraded from Ubuntu 14.04 to 14.10
Intel I-7 3.5Ghz
16GB ram
Built-in Intel gigabit ethernet

Computer 2 -
Recently Upgraded from Ubuntu 14.04 to 14.10 to 15.04
Also Intel I-7, but an older model
8GB RAM
Built-in Intel Gigabit ethernet

Media Server - 
Popcorn Hour A410
1gB RAM
Processor is unknown but runs a stripped down purpose-built linux system
Built-in Gigabit Ethernet 

Network - 
Computer->CAT6 cable->Netgear gigabit switch->CAT5 cable->TPLink gigabit switch with PoE->CAT6 cable->A410 but the A410 is connected to a port that does not provide PoE.

---

