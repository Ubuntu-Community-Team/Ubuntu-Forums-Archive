---
title: "Problems with ndiswrapper"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by ANTDx1 on 2006-10-08
Hi everyone.  I have a very big problem: my Ubuntu 6.06 LTS partition will not boot.  For the past week, I have been attempting to get my wireless card (Broadcom 4318) to work with my laptop (hp zv6000).  Wired connection worked just fine, but I wanted to be able to take it around my college campus without having to use Windows.  I was lucky enough to be one step from abandoning Windows completely: wireless.  First, I tried some directions that worked for general broadcom cards.  I later found out that they did not work for mine.  I moved to others, which allowed me to set ndiswrapper up and use wireless.  However, upon restarting my computer, Ubuntu boot started hangig at the "loading manual drivers" step of the boot process.  Mounting the partition and deleting ndiswrapper from the modules file fixed this, but also made me unable to use wireless.  I tried again, this time clearing the old driver that I had installed before the working one, thinking that that might help the problem.  It did not.  However, this time, when I boot into Ubuntu, even with ndiswrapper commented out in the modules file, the boot hangs at "configuring networking devices".  if I leave ndiswrapper uncommented, the boot still hangs at "loading manual drivers."  I am very new to Ubuntu, but I really enjoyed using it.  It is a refreshig experience over the Windows XP I am currently using.  If anyone has any ideas which would atleast let me boot into Ubuntu and try to work on wireless later, they would be greatly appreciated.  Thanks for reading, and for your help.

---

### Post by H.E. Pennypacker on 2006-10-08
Damn it! I wish I had kept track of all the guides I used to get my card (the exact same as yours) to work with Ubuntu.  Unlike so many other people using this card, I have no problems at all.  It's just great, but not when I used to use PCLinuxOS.

Anyhow, do not give up.  Hopefully someone will pick up on this.

---

### Post by NoTiG on 2006-10-08
well i had a problem a while ago where it would hang at that part as well... Try removing ndiswrapper from your /etc/modprobe.d file........ and manually modprobe it after gnome loads

---

### Post by ANTDx1 on 2006-10-09
Alright I tried the idea of modprobing it on my own.  Either I didn't clear out the modprobe list right, or it just doesn't work.  It worked the first time I tried it, but this morning when I tried to do it manually, the computer froze.  After that, I restarted and reconfigured ndiwrapper.  It worked again now.  I am, however, hoping for something that will work ALL the time.  I don't mind manually modprobing ndiswrapper everytime I need wireless, as long as it works.

---

### Post by NoTiG on 2006-10-09
if it doesnt work the uninstall the driver with ndiswrapper, then reinstall it with ndiswrapper -i again... then modprobe again

---

### Post by ANTDx1 on 2006-10-09
So far, so good.  I had one issue this morning, which I eventually worked out.  I'll keep up with the many threads discussing this wireless setup and see if I can't find a better solution.  Until then, this works just fine.  Thank you for all your help.  Getting two replies within an hour or two of my post is pretty impressive, in my opinion.

---

