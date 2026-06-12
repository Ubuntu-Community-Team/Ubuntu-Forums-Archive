---
title: "Ading some memory"
date: 2009-04-05
forum: New to Ubuntu
---

### Post by Pondoro on 2009-04-05
I converted a 6 year old eMachines box to Ubuntu. I liked the results at first but now it seems to me that the machine is slower than it should be. I am thinking of adding some memory. The machine has 256MB of removable memory and (if it was still a Windows machine) can support a maximum of "2048MB DDR PC2700." I have a couple of questions:

1) If I plug in the new memory will Linux automatically find it?
2) What does DDR PC2700 mean? I don't want to buy the wrong stuff.

Thanks

---

### Post by kpatz on 2009-04-05
1) Yes.
2) It's the type/speed of memory.  Make sure the memory you get says DDR (not DDR2) and 2700 on the package and it'll work.

---

### Post by Pondoro on 2009-04-05
Thanks! I forgot to ask, will it be likely to speed up the machine? It seems to open programs slower than when I first installed Ubuntu. Aslo I get some glitches when playing mp3s.

---

### Post by hessczoo on 2009-04-05
RAM can play a factor. You will notice better performance though because 256MB is low for Ubuntu, so it's probably using a lot of slow swap space. The RAM will give you some more speed for sure, and you will be able to run more programs without degredation in speed.

---

### Post by Chemical Imbalance on 2009-04-05
Definitely go for the RAM upgrade.  Get the full 2gb's, you'll notice a nice speed increase from 256mb's!  Again, make sure you get the right kind.

---

### Post by wolfen69 on 2009-04-05
the 2700 part of it isn't as important. if you get 2100ddr, both sticks will run at 2100 speeds. if you get 3200ddr, both will run at 2700 speed. as long as it's 2700 or higher, and DDR, (not DDR2) you will be fine.

---

### Post by Chemical Imbalance on 2009-04-05
Oh and another thing, make sure you get desktop RAM not notebook RAM, and also do not get DDR2 or DDR3.  The MHZ of the RAM isn't a big deal because if you get some ultra fast RAM it will drop down to what your motherboard supports.

---

### Post by raymondh on 2009-04-05
Go for it!

You'll be able to run more apps at the same time.  Though everything has it's own limits, 2GB will have more than the current 512mB.

Have fun.

---

### Post by arapa on 2009-04-05
Ubuntu is using about 732 MB of memory on my set-up (with firefox running). I would suggest upgrading your system to at least 1 GB.

You can see how much memory your system is using at any given time by opening system monitor from the panel menu (SYSTEM>ADMINISTRATION>SYSTEM MONITOR - [Resources Tab] or typing ```
free -m
``` at the terminal.

---

### Post by wolfen69 on 2009-04-05
> **arapa said:**
> Ubuntu is using about 732 MB of memory on my set-up (with firefox running).

something is definitely amiss with your setup. i have never seen more than 400mb used with firefox open on any machine. (40+ pc's)

---

### Post by InfectedWithDrew on 2009-04-05
> **wolfen69 said:**
> something is definitely amiss with your setup. i have never seen more than 400mb used with firefox open on any machine. (40+ pc's)

Firefox, on my Windows XP boot, is running at over 500,000K.  He's using add-ons, much like I am.

----------------
Now playing: [Crossfade - The Unknown](http://www.foxytunes.com/artist/crossfade/track/the+unknown)

---

### Post by asmoore82 on 2009-04-05
> **arapa said:**
> Ubuntu is using about 732 MB of memory on my set-up (with firefox running).

to get a more realistic idea of how much RAM the OS and programs are really using,
you should subtract the "cached" value from the "used" value as reported
by command line tools such as `free` and `top`

The graphical "System Monitor" app does this for you,
which is why it's "used" RAM amount will always show less than the command line tools.

I have 2 gigs of RAM total;
with firefox+noscript+downloadhelper+speeddial+6 tabs and rhythmbox open I'm only using ~508MB of RAM,
but with a whopping 1400 MB of data "Cached"

---

### Post by presence1960 on 2009-04-05
> **wolfen69 said:**
> something is definitely amiss with your setup. i have never seen more than 400mb used with firefox open on any machine. (40+ pc's)

true when I first open FF, but after open a while and with multiple tabs it goes up about 200 - 300 MB. If I close FF it goes back down. But with 4 GB RAM on 64 bit Ubuntu I ain't quabbling over that little slice.

---

