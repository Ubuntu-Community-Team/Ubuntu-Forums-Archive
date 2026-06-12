---
title: "Wireless USB Adaptor"
date: 2007-06-05
forum: Networking &amp; Wireless
---

### Post by scott_g on 2007-06-05
Hi,

I just tried plugging in a DLINK WUA-1340 wireless adapter and was surprised when Feisty found it, and located my wireless network.  It immediately showed the network, with about 2/3 signal strength, so, I tried to connect; it disconnected the wired connection, and spend 30 seconds or so trying to connect to the wireless portion, yet failed and reverted to the wired.  Same result if I unplug the wired connection.  The wireless network is completely unprotected (I live in the country and you'd have to be sitting at my front door to use it, I think I'd kinda notice that...).  I don't believe it is a driver issue, as it found the network.

Does anyone know what I can do to connect wirelessly?

I can post anything you want, but am unsure what would apply.

I don't need the wireless specifically, but it would be nice to know that it works,

Thanks a lot,
Scott

---

### Post by dannyboy79 on 2007-06-07
it's becuase the native feisty rt73usb driver doesn't work, you need to either use ndiswrapper with the windows driver files OR you need to blacklist the provided rt73usb and compile per here: [http://ubuntuforums.org/showthread.php?t=270756&highlight=WUA-1340](http://ubuntuforums.org/showthread.php?t=270756&highlight=WUA-1340)

---

### Post by scott_g on 2007-06-07
Thanks  a lot, looks like it will be ndiswrapper for me then.  Now to find the windows drivers...  I have the install cd, but I guess I have to install them to get the program to unpack the files, unless someone knows of another way?

Thanks again,
Scott

---

### Post by dannyboy79 on 2007-06-07
why would you use the windows driver?????? If there's native linux drivers, those are always preferred just an FYI. Also, if you do want to use ndiswrapper and you don't have a windows computer to install the wireless cd onto, then install wine on your computer and follow the guide I linked as he shows you how to run the cd within wine.

---

### Post by scott_g on 2007-06-07
True, I could use native drivers, although the process looked long, in your previous link.  I was going to use windows drivers, as I have previously used ndiswrapper, but have little experience with compiling drivers; guess its time to learn something new!!!

I'll try compiling the drivers once my exams are done.

As another note, the drivers won't install through wine; the installer uses some fancy graphics, and it always fails.

Thanks again,
Scott

---

### Post by dannyboy79 on 2007-06-07
> **scott_g said:**
> True, I could use native drivers, although the process looked long, in your previous link.  I was going to use windows drivers, as I have previously used ndiswrapper, but have little experience with compiling drivers; guess its time to learn something new!!!

I'll try compiling the drivers once my exams are done.

As another note, the drivers won't install through wine; the installer uses some fancy graphics, and it always fails.

Thanks again,
Scott

and are you using the version of wine that he stated that should be used? i can't speak from experience, only what I read in the link I provided.

---

