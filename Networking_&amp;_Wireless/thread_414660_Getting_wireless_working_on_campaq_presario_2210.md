---
title: "Getting wireless working on campaq presario 2210"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by thfccanuck on 2007-04-20
I can't get my wireless connection working.

First I tried using network-admin. But I did not connect.

I don't know what to do: I've tried all the useful docs I find ion this site.

i've done 
lshw: the harware is there
lmod: drivers are loaded

iwconfig: shows eth1 as my wireless hardware.

sadly 
iwlist eth1 scan 
fails with "Interface doesn't support scanning"

I've used 
iwconfig eth1 channel | Mode |  Key | Ap to try and set the required values

dhclient eth1 keeps failing with Network is down.


I know the wireless is working - I am using it to write this post from a windows machine.

What do I do???

---

### Post by thfccanuck on 2007-04-20
bump

---

