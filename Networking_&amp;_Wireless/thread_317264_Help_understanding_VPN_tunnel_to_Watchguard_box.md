---
title: "Help understanding VPN tunnel to Watchguard box"
date: 2006-12-12
forum: Networking &amp; Wireless
---

### Post by jethro10 on 2006-12-12
Hi,
i'm a little lost in understanding this.
At work we use Watchguard SOHO 6 boxes which can have 2 types of VPN tunnels. "Hardware" ones, where both ends use a box and both boxes are 'pointed to each others IP address, setup a few keys and your away - we have several of these.
However watchguard offer MUVPN's I gather Mobile User VPN's where the windows client gets a piece of software (supplied) that can instigate a connection from anywhere, ie the Watchguard box doesn't know where the incoming connection is from, it may be any IP address. Anyhow, the client connects, shares a key and off we got.

With my Linux PC at home are these OpenVPN and racoon VPN thingies emulating the Hardware connections? or is there a linux equivalent to the Mobile User VPN? Or even am I way off in my analysis ?

Just stuck as to what to try
J

---

### Post by Blizzard97 on 2007-09-29
The new 8.6 firmware gives you pptp 10 sessions and you don't to mess with that MUcient they got

---

### Post by Blizzard97 on 2007-09-29
An easy fix is to map 443 to the internal adress on the box then you can HTTPS to it You gotta have a user on the Watchguard to log onto of course

---

### Post by jethro10 on 2007-10-10
> **Blizzard97 said:**
> The new 8.6 firmware gives you pptp 10 sessions and you don't to mess with that MUcient they got
Yeah, but how?

J

---

