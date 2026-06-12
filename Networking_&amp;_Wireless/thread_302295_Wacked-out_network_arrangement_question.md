---
title: "Wacked-out network arrangement question"
date: 2006-11-18
forum: Networking &amp; Wireless
---

### Post by K.Mandla on 2006-11-18
This is kind of a weird networking question, and not one necessarily confined to Linux. Forgive me if it's newbish.

A friend of mine has ordered cable internet for his house, and bought a wireless router. The problem is that he has two desktop machines in a back room that he would rather not buy wireless cards for, or for that matter, buy 100-foot cables to reach the router.

He has a laptop with a wireless card and a network jack, and he is thinking he can catch the wireless signal with the card and reroute it through the wired connection. From there it would go into his old wired router and be split off into the desktop PCs.

I've never heard of a setup like that, but it seems like it should work. Naturally, network speeds will be limited by the wireless card in the laptop, but he's content with that.

Has anyone ever done anything like that?

---

### Post by mips on 2006-11-18
It will work.

Firestarter on the laptop and enable ICS. configure eth and router in common network and then let the pc's get ips via dhcp.

Better option would be to put the last router into bridged mode if possible.

or just buy a very cheap hub/switch and cut out that last router.

either way it will work'

---

### Post by K.Mandla on 2006-11-18
> **mips said:**
> It will work.

Firestarter on the laptop and enable ICS. configure eth and router in common network and then let the pc's get ips via dhcp.

Better option would be to put the last router into bridged mode if possible.

or just buy a very cheap hub/switch and cut out that last router.

either way it will work'
Sweet. Thanks. He'll be excited.

---

