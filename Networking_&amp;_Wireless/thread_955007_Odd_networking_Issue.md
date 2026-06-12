---
title: "Odd networking Issue"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by anton_pm on 2008-10-21
Got a bit of a strange one that I can't work out here. Basically when I try to stream media or download files over http to/from my PS3 from my HP Box , the packets will stop for about 30 seconds and then resume again which isn't too great.

Ok, what I've tried so far:

Sending to another node on the network - couldn't replicate

Sending from another node to the PS3 - didn't replicate, plays and downlaods fine from a 32-bit 7.04 machine.

Swapping the cables between working and non-working nodes. 

Using another OS (Windows XP) - sent packets on the ML115

The offending box is an HP ML115 server running 64-bit 8.04 and is fully up-to-date regarding updates (problem occured before and after updating). I'm using the latest apache to host files and Mediatomb to stream media, the effect is the same on both. 

The PS3 is connected wirelessly, as is the second working receiving node. Both "sending nodes" (ML115 and GX240) are connected by cable. I am using a Netgear DG834GT broadband router to network the nodes. 

The last thing to try I guess would be another switch, but it's odd that another node can send packets fine using the existing one. 

Any help would be greatly appreciated.

---

### Post by anton_pm on 2008-10-23
Tried a re-install, did nothing at all, if anything it's worse now! 

Might try 8.10 beta or another network card, but I really don't understand why this suddenly started happening on it's own.

---

### Post by tigon5 on 2009-02-10
I think I have similar issue.
I am moving over from 32bit intrepid to an amd64 intrepid.  Both updated (10feb09).
My movie files are stored on a lan drive (smb) and is mounted with the same options using cifs on both pc's.  Both have apache setup in the same way.  
I can watch the films from ps3 by browser fine when served from the 32 machine; but when I try to watch from the 64 machine I get an error message (data type not supported - evn though same file).  I am afraid I cannot describe the problem in terms of packets as the original post did - but do not really know where the error could be: apache, ps3, cifs.
Films stored locally on both the 32 and 64 machine, play fine when served up to the ps3!
If you could briefly say how you assessed packet droppage - then I would like to try the same to see if its same issue.

---

