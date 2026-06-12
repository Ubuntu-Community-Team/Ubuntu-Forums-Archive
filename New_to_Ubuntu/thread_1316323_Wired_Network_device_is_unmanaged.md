---
title: "Wired Network device is unmanaged"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by andyzammy on 2009-11-05
Hi everyone!

after the computer becoming very sluggish, i had to restart the computer manually (shutdown didn't finish and wouldn't budge, only a little bit left on the bar). When it booted up again, the wired network wouldn't connect (device unmanaged). I'm lucky i live right next to a hot spot otherwise i'd be stranded! Unfortunately i have to use it through a proxy and i can't work out how to configure my pidgin to work through it ors i'd irc as this problem needs to be solved right now.

I don't know what to do. I googled and the only result that matched my problem didn't help, the solution didn't work for me:
[http://ubuntuforums.org/showthread.php?t=940558](http://ubuntuforums.org/showthread.php?t=940558)

Can anybody help me get back up and running please?

Zammy

---

### Post by Iowan on 2009-11-05
Still running Intrepid - or have you upgraded? Check contents of */etc/network/interfaces* - should probably have only definition for "lo" (trying to remember Intrepid - one of the versions I skipped).

---

### Post by andyzammy on 2009-11-05
> **Iowan said:**
> Still running Intrepid - or have you upgraded? Check contents of */etc/network/interfaces* - should probably have only definition for "lo" (trying to remember Intrepid - one of the versions I skipped).

still on intrepid.

it did only have lo in, but in order to enable bridged eth0 adapter for VB i needed to add to it - i don't think this broke it (but then again i can't remember if i restarted comp, only networking), but that did solve my VB problem.

here's the contents:

```
auto eth0
iface eth0 inet manual

auto br0
iface br0 inet dhcp
	bridge_ports eth0 vbox0

#the loopback network interface
auto lo
iface lo inet loopback
```

---

### Post by andyzammy on 2009-11-06
is there perhaps a way to re-install ubuntu without affecting my /home folder?

don't know what happened but now the wireless connection i was using stopped working (i connected to it fine its not related to this problem, just internet stopped working) so i had to run a live cd. i really need a quick an easy fix for this problem. i tried removing the extra from the interfaces file but it didn't help any after restarting networking.

---

### Post by andyzammy on 2009-11-06
solved, it *was* the interfaces file. removing the extra stuff helped.

however, i have a new problem of how do i get Bridged Networking to work with VirtualBox? the wiki tells me i need that information in order to use it, but if it breaks my network manager every time i restart the comp, how do i use it safely?

---

