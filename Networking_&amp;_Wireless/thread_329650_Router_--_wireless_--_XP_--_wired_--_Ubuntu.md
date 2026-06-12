---
title: "Router -- wireless -- XP -- wired -- Ubuntu ?"
date: 2007-01-01
forum: Networking &amp; Wireless
---

### Post by acegolfer on 2007-01-01
Is this possible?

Wireless Router ----(wirelessly)------ XP (ICS enabled) ------- (cross cable) ---- Ubuntu?

I have WUSB54G V4 and it's hard to get it work in Ubuntu within WPA environment. So I'm trying to improvise by connecting Ubuntu to XP using cross cable. ICS in XP will be enabled.

As Ubuntu will see XP as a router/hub, there's nothing that I need to configure. I don't see why this shouldn't work. Am I right?

Then, will other wirelessly networked PCs see Ubuntu? How about will Ubuntu see other networked PCs?

---

### Post by linuchsan on 2007-01-02
I had the same problem with wpa, till i found this [http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=2037&start=15](http://rt2x00.serialmonkey.com/phpBB2/viewtopic.php?t=2037&start=15)

---

### Post by acegolfer on 2007-01-03
It worked after struggling. 

In XP, if ICS is enabled, the XP machine will become DHCP server with 192.168.1.1 address. Unfortunately, my router had the same address. So I had to change the router address to 192.168.0.1. Everything works since then.

---

### Post by FMDragon on 2007-05-03
Think you could elaborate a bit more on how exactly you got that set up to work? It might be the solution to my woes.

---

