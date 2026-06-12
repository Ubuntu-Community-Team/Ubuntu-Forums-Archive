---
title: "Vista can't see Ubuntu Samba shares and vice versa..."
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by crysys on 2008-07-23
I got a new laptop from work and that means Vista of course. :(  I'd love nothing better than to wipe it and stick Ubuntu on here but for now at least, that ain't happening.

At home I plug the laptop in to a wired broadband router.  My desktop resides at *.*.*.100 and *.*.*.101 is where the laptop ends up.

My desktop hostname is in all caps and the domain matches the one set in the laptop.

I have one samba share named /Share in my home folder with the shared name of /share (no caps) and guest access enabled.

My Firestarter policies are as follows:

```
Outbound: permissive by default.
Inbound:
   Allow connections from host:
      x.x.x.101
   Allow service:
      137-139 445   x.x.x.101
      40000-60000   x.x.x.101

```

I opened up that giant block of ports at 40000 because initially I would see an event on random ports in that range from the laptop when I tried to access DESKTOP in the network view in Vista.  I can see DESKTOP  in the network view but cannot establish a connection to it.  I always get:
```
Windows cannot access \\DESKTOP The network path was not found.
```

I should be able to see a network share at \\DESKTOP\share right?  I can't even manually map a drive letter to that address and I no longer generate events on Firestarter so I assume everything is open.  Vista can see the computer but cannot actually connect to it.  What am I forgetting!?


So after pulling my last hair out on that I figure why not just enable the Public folder on the laptop and access it from the desktop?  I do so but The Network Servers view in Nautilus has one entry, Windows Network, with nothing in it.  Now I have a migraine. :frown:

---

