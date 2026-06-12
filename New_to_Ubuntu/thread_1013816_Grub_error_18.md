---
title: "Grub error 18"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by Jdmisra81 on 2008-12-17
So I just got Xubuntu (it is 8.04, I used an alternate install disc) running..I would say just the way I like it ..And today out of the blue I can't get things going...

I keep geting this message 'Grub Error 18'. And then everything just stops.

I did some searching but most of the suggestions I found were pretty confusing for me at this point, stuff about rearranging partitions and stuff...is there an easy fix or do I have to reinstall everything (again)?

Also when I could get to the Grub, I noticed my old version of Ubuntu is still listed..Is there a way to get rid of that? 

I used to not have to stop at any Grub menu and it was very nice....I would be really happy if it would go straight to the login screen without that stop along the way.

Any  help much appreciated!! (I'm online using an old linux CD , running it  live)

---

### Post by Michael.Godawski on 2008-12-17
hi Jdmisra81, 
> Also when I could get to the Grub, I noticed my old version of Ubuntu is still listed..Is there a way to get rid of that? 
What do you mean by old version? It is perhaps a older kernel version? If yes try to boot into it. There was perhaps a kernel update which conflicts now with your system.  The older might still work. 

If not... I would try the latest 8.10 version of Xubuntu.In any case make a back-up of your files.

---

### Post by lovelyvik293 on 2008-12-17
Hi check this out it may help you:-
[http://www.linuxquestions.org/questions/linux-hardware-18/grub-loading-please-wait......error-18-343280/](http://www.linuxquestions.org/questions/linux-hardware-18/grub-loading-please-wait......error-18-343280/)

---

### Post by Jdmisra81 on 2008-12-17
Sorry if I wasn't very clear, I mean to say that for some reason one of the menu items in the grub is Ubuntu 6.10..which I thought was long gone.

It doesn't work either., same problem.

How do I go about backing up my files before reinstalling (if I can't get myself intot he desktop)

thanks,

---

### Post by lovelyvik293 on 2008-12-17
For Backup just run the LIVE CD of the UBUNTU and copy your files to external HDD.

---

### Post by Michael.Godawski on 2008-12-17
For back up have a look at:

[LIST]
[*][http://godawski.oxyhost.com/accesshd.html](http://godawski.oxyhost.com/accesshd.html)
[/LIST]

---

### Post by caljohnsmith on 2008-12-17
A Grub error 18 typically occurs when you have an older BIOS that can't access anything on the HDD past either 8.4 GB or 137 GB, depending on how old the BIOS is. If your Ubuntu boot files are outside of that range on the HDD, then Grub gives you an error 18 because Grub can't access the boot files. Usually the best solution is to create a ~200 MB boot partition at the beginning of the HDD, and then when you install Xubuntu, set the mount point on the boot partition as "/boot" so that all of Xubuntu's boot files will go there. If all goes well, then you won't get the Grub error 18 any more. How about giving that a shot and let us know how it goes.

---

