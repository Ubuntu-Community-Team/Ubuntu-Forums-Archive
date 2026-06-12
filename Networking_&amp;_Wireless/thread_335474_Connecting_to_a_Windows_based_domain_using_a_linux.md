---
title: "Connecting to a Windows based domain using a linux server, with a linux client"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by renzokuken on 2007-01-10
ok, so in my office at uni we have a Linux based server running Fedora, to which all the network (client workstations) computers connect. 

all the workstations are running XP.

my question is, i want to dual boot on my workstation with ubuntu, but can it connect to the fedora server/domain in the same way that XP does, and if so, how would i go about setting that up?

thanks

---

### Post by kebes on 2007-01-10
The answer is probably yes.

It depends on what services the server is running (and which of those you want). But, for instance, if it's acting as a file server using samba, then you can certainly connect to it and browse files.

(For a samba share you can just click "connect to server" and enter the information, including username and workgroup, and then it will be mounted into your Ubuntu filesystem.)


If you want more specific answers, try to come up with a list of services you want to be able to access (mention the software running on the Fedora server if you have access to that information...).

Hope that helps.

---

### Post by renzokuken on 2007-01-10
its primarily, actually solely a file server running samba.

if i use the same username and password for my ubuntu as my samba password on the fedora server will it give me the same access?

---

### Post by kebes on 2007-01-10
> **renzokuken said:**
> its primarily, actually solely a file server running samba.

if i use the same username and password for my ubuntu as my samba password on the fedora server will it give me the same access?

Yes but you don't have to. (If I recall correctly.)

The username/password for your Ubuntu login account can be different from the username/password required to login to the samba share (on Windows they are the same but on Linux they can be different if you want).

On Linux, when you connect to the samba share you'll have the option to enter the username to use, the workgroup to use, and the password to use.


However for convenience you may prefer having all the username/passwords be the same.



P.S.: One of the great things about Linux is the fact that you can test alot of this stuff with LiveCDs. Burn a copy of the Ubuntu LiveCD and boot it up on your computer. You'll enter a full (albeit slow) desktop session, and you'll be able to try to connect to the samba share in the way I just described.

---

### Post by renzokuken on 2007-01-11
> **kebes said:**
> 
P.S.: One of the great things about Linux is the fact that you can test alot of this stuff with LiveCDs. Burn a copy of the Ubuntu LiveCD and boot it up on your computer. You'll enter a full (albeit slow) desktop session, and you'll be able to try to connect to the samba share in the way I just described.

superb idea, i never thought about that. thanks

---

