---
title: "Ubuntu cannot access networked printer (but XP can)"
date: 2008-11-02
forum: Networking &amp; Wireless
---

### Post by aktiv_us on 2008-11-02
I have a bit of mystery that I sense is from something simple.

Just recently installed 8.10 using wubi.  Ubuntu successfully accesses the network using my wireless PCI card.  I am working on getting my HP Deskjet wireless printer set up but I cannot get to the printer - HPLIP is unable to see it.

All computers in the house access the printer (192.168.0.2) through the router (192.168.0.1).  They can currently print to it, they can ping it, and they can access the printer's web page.  This computer, when running XP, can do the same.

However, when running Ubuntu through the same computer, the printer can't be found.  Even though the router still indicates that the printer is attached, I cannot ping it, not access the printer's internal webpage.

I can only guess on a couple of things:
[LIST]
[*]wubi is for kids, do a real install dude.
[*]The frame buffer error that I consistently get on startup (and that I'm able to get through without negative effects on the display) has farther reaching effects than I thought.
[*]There's a real simple setting somewhere that I'm leaving out.
[/LIST]
Any clues anyone?

Thanks!

Keith.

---

### Post by aktiv_us on 2008-11-23
Well, I've got the installation stabilized - no Frame Buffer errors and it can now use my 6-year old monitor without problems  :-)

And since then, in the month or so that I've been stable, the printer network access is consistent only in its inconsistency.  Each bootup can either see the printer, or it can't, and if I can't, I would have to reboot and hope that the next bootup works.

Anyone seen anything like it?  Is it a lucky setting in the router?  Can I change the timeout settings?

Thanks in advance

Keith.

---

### Post by aktiv_us on 2008-11-23
This is what I receive from attempts to ping the printer during those times I can't reach it:

[FONT="System"]~$ping 192.168.0.2
PING 192.168.0.2 (192.168.0.2) 56(84) bytes of data.
From 192.168.0.3 icmp_seq=1 Destination Host Unreachable[/FONT]

Cheers again

Keith.

---

### Post by TutonicMonkey on 2008-11-23
I am have the same issue on several computers using 8.10 and I do have samba installed.  I do not think this has to do with wubi.

Here is my post on the topic:

[http://ubuntuforums.org/showthread.php?t=986574&highlight=ubuntu+8.10+can%27t+see+vista+shares](http://ubuntuforums.org/showthread.php?t=986574&highlight=ubuntu+8.10+can%27t+see+vista+shares)

I have yet to find an answer.

---

