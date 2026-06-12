---
title: "HOWTO: Zyxel G-302 V3 (Ubuntu 7.04, Feisty Fawn)"
date: 2007-04-23
forum: Networking &amp; Wireless
---

### Post by rictus007 on 2007-04-23
Hi.  I'm like a lot of people that buy this network card because it is cheap and works with linux on most of the distribution right out of the box (with out any configuration).

Well on this new version of Ubuntu it works but with Ndiswrapper


The drivers that works V3 is the one for Windows XP



1) Install Ndiswrapper using synaptic - Install also ndisgtk
2) On the Terminal: sudo ndisgtk
3) Find the drivers an hit OK
4)Restart


That's it....on my case even wep works just fine

---

### Post by m_bridge on 2007-05-05
Not so easy for me...
Same card, it was working in edgy
Now after installing ndiswrapper i get 

bridge@stregatto:~$ ndiswrapper -l
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)
i filled a bug report [on launchpad]("https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/111530")


did you use the driver on the CD or you downloaded it from the official site?

---

### Post by m_bridge on 2007-05-05
:guitar: [COLOR="Red"][SIZE="4"]Yeah![/SIZE][/COLOR]
it finally works! i tried the driver from zyxel homepage instead if the one on CD and it works!

anyway i still get the strange message from ndiswrapper -l...

---

### Post by rictus007 on 2007-05-05
Well the response is a little bit late...but anyways...I use the drivers from the cd.. exactly the ones for windows xp

---

### Post by 2hvybg3yb on 2007-06-08
I cant get mine to work, it will not boot up with PCI card in the PC.. :(

---

### Post by dehjli on 2007-06-14
I followed these instructions, and they worked fine.  The only thing I want to add is that I went to Zyxel's website, and apparently there is a v1 and v2 of the Windows XP drivers.  I tried v2 and it gave me syntax error parsing the driver file when I tried to install.  I installed v1 and it worked fine.  Has anyone successfully installed v2?

---

