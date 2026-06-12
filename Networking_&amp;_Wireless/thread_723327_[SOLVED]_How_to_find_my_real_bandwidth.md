---
title: "[SOLVED] How to find my real bandwidth?"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by Udibuntu on 2008-03-13
Hi Guys,

I just upgraded my Internet bandwidth but didn't see any significant change.

What's the best tool I can use to find my actual bandwidth while using Ubuntu Feisty?

Cheers,

Udi

---

### Post by dorkdork777 on 2008-03-13
I don't know of a dedicated tool, but [www.speedtest.net](www.speedtest.net) usually does the trick.

---

### Post by .nedberg on 2008-03-13
I use:
```
time wget ftp://ftp.uninett.no/linux/ubuntu-iso/7.10/ubuntu-7.10-desktop-i386.iso
``` and calculate the speed myself

Remember to use a mirror close to you...

---

### Post by mrsteveman1 on 2008-03-13
There is a script available called ibmonitor that should grab the relevant info from the kernel and display it in realtime.

[http://sourceforge.net/project/showfiles.php?group_id=80146]("http://sourceforge.net/project/showfiles.php?group_id=80146")

---

### Post by Udibuntu on 2008-03-13
Hi.

Thanks, I tried Speedtest but nothing happens...I press "test again" after saving the parameters and nothing happens.

All boxes are N/A though my IP and ISP are stated.

Help...

Udi

---

### Post by Udibuntu on 2008-03-13
Hi .nedberg,

Sorry mate, too techie for me...I love open source and Ubuntu for the spirit of them, not for my deep knowledge of their insides...

I'd appreciate a more layman oriented approach.

Thanks for your help though,

Udi

---

### Post by Udibuntu on 2008-03-13
Hi Steve, thanks for the link.

I thought I needed a Deb file, not a tar.gz....:confused:

I'm starting to feel the water level reaching my neck...

Oh wizards of the ancient Ubuntu clan, help me out here :)

Udi

---

### Post by mrsteveman1 on 2008-03-13
It's just an archive like zip or rar, download it and double click the file, then drag ibmonitor out onto your desktop. After that you can run it in a terminal by double clicking the ibmonitor file and clicking "run in terminal" when gnome asks.

What ibmonitor does is show you how fast the speed is on your network connection at the moment, so you can download a file and see exactly what the box is getting, regardless of what you use to test it wtih.

---

### Post by Udibuntu on 2008-03-14
OK, Steve, thanks, I'll do it.

I'll also try and send around some multi mega PPT to see what I get.

Cheers all, I will close this thread as solved.

Udi

---

