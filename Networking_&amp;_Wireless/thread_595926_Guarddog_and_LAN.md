---
title: "Guarddog and LAN"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by SpinningAround on 2007-10-29
How do I setup guarddog to work with my other computers in the LAN that I use? Before I installed guarddog was I able to connect to my ubuntu station that was running samba from a windows computer but since I installed guarddog is this no longer possible. Any thought in how I should get this working?

---

### Post by SpinningAround on 2007-10-29
Forgot to add:

Both computers are behind a router so they are in there "own" zone where they are behind the firewall of the router.

Since I wish to transfer files from one computer to and other would I like to know how I should do to make this possible.

As I did say do I already got samba running but can't get it working with guarddog

---

### Post by dburnett77 on 2007-10-29
with Guarddog, you create zones.  Name a knew zone something like 'LOC_LAN', and open the same ports by ticking the appropriate box, in ea. of the zones.

---

### Post by SpinningAround on 2007-10-29
> **dburnett77 said:**
> with Guarddog, you create zones.  Name a knew zone something like 'LOC_LAN', and open the same ports by ticking the appropriate box, in ea. of the zones.

I have create a new zone for my local network but it still ain't working :(
The good and the bad with guarddog is that it block everything that you don't allow, so please say what ports I need to have open.

I have the following ports open between my local network and the computer.
TCP 445
TCP/UDP 137

Unsure if there are other ports that samba need to work.

I'm trying to find the iptables log or the guarddog log but don't know where it's did check in /var/log/ but nothing there, is't located somewhere else? :confused:

I notice one thing now when I start guarddog throw terminal using *sudo guarddog* can I see my new added zone but when i only use the command *guarddog* can't I see it. Any thoughts on why is't a feature or a bug or something else?

---

