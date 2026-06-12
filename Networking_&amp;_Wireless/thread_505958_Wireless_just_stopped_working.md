---
title: "Wireless just stopped working"
date: 2007-07-20
forum: Networking &amp; Wireless
---

### Post by DWRZ on 2007-07-20
Since my Ethernet is broken I'm stuck only with wireless, so this is a pretty killer issue for me. I'd really appreciate some help.

I'm on Ubuntu Feisty, have had wireless for days now working without a hitch. Been using network manager. This was through manual configuration, selected a network from the list and set up for automatic DCHP. Today, after turning my PC off for about 5 hours, I boot Ubuntu and wireless doesn't work. I try manual and roaming but I still can't seem to connect to anything. When network manager is set to roaming none of the grey little spheres turn green-- both stay gray. I've looked on google and here in the forums and I've seen some similar issues but no real answers... does anyone have a solution/can help?

---

### Post by JAPrufrock on 2007-07-21
Are you sure it's not the wireless? Try turning the wireless off, wait a few seconds, and then on again.  If that doesn't do anything, try resetting the wireless (usually a small recessed button somewhere).  That will reset it to the factury default config, which usually works.

---

### Post by Barqs on 2007-07-21
nothing wrong with using wireless. :)

---

### Post by DWRZ on 2007-07-21
Thanks. I've tried turning it on and off, nothing. And ao far as I know, there's no reset button. I just dont uncerstand what could have happened. :(

---

### Post by DWRZ on 2007-07-21
Anyone? I basically can't use Ubuntu right now. I keep going back trying what little I know bit I,m steck. This is really excrutiating.

---

### Post by JAPrufrock on 2007-07-21
There's almost always a reset button on the wireless.  Sometimes it's just a small hole that you can stick a wire or papercllip or some other pointed object into.

---

### Post by benx009 on 2007-07-21
this might actually be a problem w/ your wireless router and maybe not your wireless adapter, so you might want to make sure it's working like it ought to.  or maybe your high speed connection is down?

---

### Post by #Reistlehr- on 2007-07-21
hey, post the output to the following if you can, so i can get a better idea.

lshw -C network

cat /etc/iftab

cat /etc/network/interfaces

dmesg |grep wlan0

---

