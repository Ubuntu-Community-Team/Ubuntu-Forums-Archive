---
title: "I need a lil help with connecting Ubuntu to Kubuntu"
date: 2007-02-15
forum: Networking &amp; Wireless
---

### Post by on1ydabest on 2007-02-15
I have a desktop with Ubuntu on it and a laptop with Kubuntu on it. They are both connected to a DLink router (DI-604). I want to be able share files between the two. I have did a few searches and tried a few solutions but I still haven't gotten it to work. Can someone please give me a lil help?

---

### Post by Touch.Code on 2007-02-15
Hmm, set both IP's to the subnet.

---

### Post by on1ydabest on 2007-02-15
I'm a noob so can you explain that a little. I have already given both machine static IPs but I can't figure out how to make them communicate.

---

### Post by saiman on 2007-02-15
can you paste the output from "ifconfig" for both machines here?
do you have "ping" between the machines?
How do you try to access the files? I suppose you'll need to get a samba server running, but after you make sure the networking is all set up.

---

### Post by on1ydabest on 2007-02-15
> **saiman said:**
> can you paste the output from "ifconfig" for both machines here?
do you have "ping" between the machines?
How do you try to access the files? I suppose you'll need to get a samba server running, but after you make sure the networking is all set up.

I can't post the ipcofig right now because I'm at work.
I do have ping between both machines. I tried it on the desktop and a connection setup winows appears on the laptop, but when I go to set it up it says connection lost.
I tried samba but it gives me a firewall error messages. That why I gave them static IP addresses.

---

### Post by dmizer on 2007-02-15
use nfs to share files between linux computers.  4th link in my sig.

---

### Post by on1ydabest on 2007-02-15
> **dmizer said:**
> use nfs to share files between linux computers.  4th link in my sig.

Thanks alot. I'll give it try when I get home.

---

