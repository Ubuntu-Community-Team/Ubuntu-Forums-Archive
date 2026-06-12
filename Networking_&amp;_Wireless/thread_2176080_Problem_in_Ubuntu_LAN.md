---
title: "Problem in Ubuntu LAN"
date: 2013-09-22
forum: Networking &amp; Wireless
---

### Post by waffen on 2013-09-22
Hello,
I want some advise about this problem, the facts are:

1. I just setup a LAN with 11 PC and 1 server 64 bits (SAMBA installed) all with Ubuntu 12.04
2. The PC clients are old more than 4 years, the server is a Ci5
3. The LAN is a simple one all connected to a SWITCH 10/100 DLINK
4. CLient have a very old system(made with FOX DOS version) running using DOSemu with the DBF and other files stored in shared folders in server
5. For shared files in the server machine (his only function) Im using NFS (installed nfs.common and the server package for it too). The folders are mounted in the clients using rc.local script working fine too. In most of them the recommended option with fstab dont work I dont know why...
6. The new Ubuntu server is the replacement for an old Centoos v5 server with mostly the same config.
7 All the machines are located phisically in a 2 floor building with Level 5 cable

All of these are working fine if the clients works with the Centoos, when they change to the Ubuntu server, the RW operations goes a little slow and suddenly one PC hangout and put slow the entire network or take down all, in the server I can see the red light indicator for RW in HD ON all the time, when the PC is shuting down all works fine and the red indicator goes well.

Note: When I made a ping to the Centoos server it return ms=0,120, the same ping from the same PC to the Ubuntu new server ms=0,450 

I cant found any possible reason for this behaviour and Im asking here for some advises about how to proceed. Thanks in advance!

Mario

---

### Post by waffen on 2013-09-23
Note 2: The server ubuntu machine have 10/100/1000 Ethernet card and there is another PC with the same card in the LAN, the rest only 10/100

---

