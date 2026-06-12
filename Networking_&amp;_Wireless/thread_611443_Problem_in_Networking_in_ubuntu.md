---
title: "Problem in Networking in ubuntu"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by myharshdesigner on 2007-11-12
i have a  ubuntu pc and windows xp pc.

now i have a ubuntu 7.10 version.

i can able to access my windows pc.

but the problem is that ubuntu show's me my all drive of windows xp PC.

i have 4 drives in my windows.

i have shared only 1 drive in windows xp pc.

but ubuntu 7.10 show me all drives with read and wright mode.

so any one can able to help me out.

how to Restrict or shared folder's or Drive in UBUNTU 7.10 ?

PL help.

and 

is ubuntu 7.10 have pre install samba server ?
if no then how ubuntu 7.10 can able to access my windows xp PC ?



Thanks in advance

Harsh

---

### Post by rivalarrival on 2007-11-13
The problem is not with Ubuntu, but with your windows setup.

Most versions of Windows have what they call "Administrative" shares on each and every drive in your system. You should not be able to read or write to those shares, even though they show up when you browse that computer over the network. (they all start with a $ symbol, don't they?) 

Samba Server allows you to share a folder from your ubuntu machine to another network machine. You do not need to run samba server if you're trying to access another machine on the network.

---

### Post by myharshdesigner on 2007-11-13
ok thanks,

yaa you are right those drives who's are not share on my windows pc show's me on ubuntu starts with $ but i also can able to access thes drives which start with $

like Folder name     $C   ,   $web

---

### Post by myharshdesigner on 2007-11-13
and one more thing what thing ubuntu use for networking and accessing other pc and cross plateform ?

can any one tell me that . I am new to linux.

---

### Post by myharshdesigner on 2007-11-18
there is no one who can able to solv my problem

---

