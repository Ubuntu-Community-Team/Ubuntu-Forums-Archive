---
title: "Troubles with Ndiswrapper on desktop"
date: 2008-03-26
forum: Networking &amp; Wireless
---

### Post by JeffoOfMetal on 2008-03-26
Okay, please help me out here, guys. Now, I've got a laptop that works great with madwifi, and a desktop that I was using ndiswrapper with. I used Xubuntu on the desktop though, and just Yesterday, I installed Ubuntu 8.04 BETA on it, because I really loved how it worked in Virtualbox, and wanted to try it out. Now, I do truly love it, mostly because it fixed my widescreen problem. I used a small high definition TV as a monitor, but it would only work fullscreen, with the sides chopped off. Now, that works, and I am extremely grateful, but after installing the ndiswrapper and ndisgtk .deb's, I get sluggish wireless speeds around 3 kilobits/sec.

Can someone tell me what the problem might be? I installed the only .deb's I could find, those being version .42 or somewhere around there.

Thank you.

---

### Post by JeffoOfMetal on 2008-03-26
Please! Somebody!

---

### Post by bajun on 2008-03-26
You can test one solution, that works for me. Hopefully this will work for your wlan card too.
Please check my post on this page: [http://ubuntuforums.org/showthread.php?t=734003&page=3](http://ubuntuforums.org/showthread.php?t=734003&page=3)

---

### Post by JeffoOfMetal on 2008-03-27
Nope, I did everything it said to do there, but to no avail. My internet speed was still at 90's modem speeds. Is this something to do with Hardy? I reinstalled Windows Wireless Drivers from the Add/Remove tool, with my snail's pace internet connection, but that did nothing. I'm so distressed! :(

---

### Post by uberlube on 2008-03-27
Maybe give up on Hardy until it is an official release and not in development, and go for gutsy.

---

### Post by JeffoOfMetal on 2008-03-29
Yes, I guess Hardy just isn't ready for Ndiswrapper... I'll lose my widescreen, but if it's only until Hardy's release, I can deal with that.

---

### Post by benste on 2008-03-29
same problem as min - install the 2.6.22 kernel and all will work fine (already a bug on launchpad for 2.6.24 kerenl which can't work with ndiswrapper - )

---

### Post by JeffoOfMetal on 2008-03-30
So how would one replace the kernel? What's the procedure?

---

### Post by adult swim on 2008-03-31
if you have the hardy beta, ndiswrapper should work for you.
EDIT:  the newest version of ndiswrapper is versrion 1.52
that may be your problem.

---

### Post by benste on 2008-03-31
Mh, I'll test it,

finally the update from 7.10 to 9.04 didn't delete the 2.6.22 kernel so thats why she can use it.

I'll try the newest version and will give a feedback asap

---

### Post by kevdog on 2008-03-31
Install ndiswrapper from source -- that is where I would start

---

### Post by benste on 2008-03-31
Can you give me a short tutorial for this?
I normally use Synaptics :-)

---

### Post by kevdog on 2008-03-31
Its a tutorial but its not short -- just walk through it one step at a time -- confirm each step as you go -- and you should be set!!

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

Once you download the source files and install kernel headers and build-essential package, I would actually uninstall your old ndiswrapper package first prior to installing the version from source.

---

### Post by benste on 2008-03-31
Seems to be nice I'l try it at home - (I'm currently at school)

---

