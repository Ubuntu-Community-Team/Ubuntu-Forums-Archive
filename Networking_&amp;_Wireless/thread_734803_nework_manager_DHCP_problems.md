---
title: "nework manager DHCP problems"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by slowpoke115 on 2008-03-25
I've been through the forums with DHCP and network manager in and generally the conclusion is the same - ditch network manager.

I've got a laptop with ubuntu on and network manager, it worked successfully for awhile, then I messed around attempting to configure a DHCP server, got this working ok and deleted (stupid I know sudo apt-get remove dhcp*) the DHCP files. I managed to fix the vast majority of stuff (network manager back) and dhcbdb) but my wireless card isn't picking up and IP's, I had to statically assign them.

Any ideas what I'm doing wrong/what I'll need to get this working?

Forgot to mention that I really want to keep network manager if possible ;) If the problems with a DHCP module I'm missing or havent configured replacing network manager isnt a solution anyway.

OS is gutsy.

---

### Post by Paris Heng on 2008-03-25
> **slowpoke115 said:**
> I've been through the forums with DHCP and network manager in and generally the conclusion is the same - ditch network manager.

I've got a laptop with ubuntu on and network manager, it worked successfully for awhile, then I messed around attempting to configure a DHCP server, got this working ok and deleted (stupid I know sudo apt-get remove dhcp*) the DHCP files. I managed to fix the vast majority of stuff (network manager back) and dhcbdb) but my wireless card isn't picking up and IP's, I had to statically assign them.

Any ideas what I'm doing wrong/what I'll need to get this working?

Forgot to mention that I really want to keep network manager if possible ;) If the problems with a DHCP module I'm missing or havent configured replacing network manager isnt a solution anyway.

OS is gutsy.

Don't use the NM, just manually set up the network. 

Go **/etc/network/interfaces** to edit.

After edit, just restart **/etc/init.d/networking restart**

This is most reliable and conventional ways in setting up the network.

---

### Post by slowpoke115 on 2008-03-25
I wonna do roaming though, get the internets all around the World!

---

