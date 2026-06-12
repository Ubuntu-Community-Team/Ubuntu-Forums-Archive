---
title: "Changing from orinoco to hostap drivers"
date: 2005-11-20
forum: Networking &amp; Wireless
---

### Post by untwisted on 2005-11-20
I can't find any sort of configurator for me to change the driver for my wireless card.  What I've tried so far was this:

Used synaptic to install the hostap_source, and all the other fun stuff associated with the hostap driver
I popped out the wifi card (its PCMICA), ran a modprobe -r orinoco, then did a modprobe hostap

lsmod | grep hostap showed the driver installed, but as soon as I put the card back in the orinoco drivers are reinstalled and it makes use of them.  They work for my card, but when I use them the card constantly loses signal and sometimes even causes the system to hang.

Thanks!

---

### Post by Lambert on 2005-11-20
after you modprobe -r add the orinoco module to the blacklist.

echo orinoco >> /etc/modprobed/blacklist

---

### Post by Storo on 2006-01-06
I've tried all the described steps but my card is still running on orinoco drivers. 
I'm a beginer but i think that blacklist step isn't good. Are you sure that echo **orinoco** >> /etc/modprobed/blacklist  is correct because my output for dmesg | grep orinoco is 


```
root@Storo:~# dmesg | grep orinoco
[4294752.474000] orinoco.c 0.13e (David Gibson <hermes@gibson.dropbear.id.au> and others)
[4294752.513000] orinoco_cs.c 0.13e (David Gibson <hermes@gibson.dropbear.id.au> and others)
[4294752.515000] orinoco_lock() called with hw_unavailable (dev=f775c800)
```

Please help!!!!!!

---

### Post by Lambert on 2006-01-06
No, I was incorrect on this. I'm using dapper which has some changes as it doesn't use hotplug anymore so it's correct for dapper.

If you are using breezy you'll find the blacklist at /etc/hotplug/

---

