---
title: "Ati 3d rage iic agp"
date: 2009-09-01
forum: New to Ubuntu
---

### Post by djginormousdrew on 2009-09-01
I am relatively new to Ubuntu.  If there's an obvious and easy answer to my question, feel free to tell me that, but then post the obvious and easy answer so I can benefit from your experience.

I am attempting to get an old Dell Power Edge box to run Ubuntu in 1024x768 mode.  I've been able to do this in Windows easily as the graphics card is natively supported in Windows.

How can I force 1024x768 resolution with this box in Ubuntu 9.04?  Here's my video card info:

andy@andy-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc 3D Rage IIC AGP (rev 7a)
andy@andy-desktop:~$ 

Thanks, 

Andy, an absolute noob in Linux drivers.

---

### Post by khelben1979 on 2009-09-01
Attach this file: xorg.conf from /etc/X11/ to this thread so we can have a look at it. Make sure not to add anything in it before making a backup of the file, otherwise it can stop working and you have no working graphics at all. The screen resolution 1024x768 needs to get added.

The graphics driver support is inside the Linux kernel.

I have a powerbook with ATi Rage with 8MB of video memory and it's able to do 1024x768 with no problems. Have never tested Ubuntu on it.

---

### Post by djginormousdrew on 2009-09-01
It's attached below.  Thanks.

---

### Post by djginormousdrew on 2009-09-08
I saved my xorg.conf file to this thread a few days ago - so far no reply, but a lot of reads.  Am I out of luck with my old dinosaur computer?

Thanks, 

Andy

---

### Post by khelben1979 on 2009-09-09
> **djginormousdrew said:**
> I saved my xorg.conf file to this thread a few days ago - so far no reply, but a lot of reads.  Am I out of luck with my old dinosaur computer?

Thanks, 

Andy

I think not. The best thing you can do is to build a new xorg.conf file using xorgconfig. Look [here]("http://www.cyberciti.biz/tips/create-a-xorgconf-file.html") for more information.

It's not wise to edit the /etc/X11/xorg.conf manually unless you know exactly what you're doing, it can get corrupted. So, use the tool above and make sure you answer the questions correctly.
[URL="http://linux.die.net/man/5/xorg.conf"]
xorg.conf man page[/URL].

---

### Post by djginormousdrew on 2009-09-09
I appreciate your good intentions, but you posted a link to a page describing the utility xorgconfig - but there was no link to get the utility, and it doesn't appear to be included in Ubuntu.

---

### Post by Sunflower1970 on 2009-09-09
I don't know if this will help, but I found this old thread that may have some good advice: [http://ubuntuforums.org/showthread.php?p=2214167#post2214167](http://ubuntuforums.org/showthread.php?p=2214167#post2214167)

Now that there's a new Xorg where one doesn't have to edit the file any more, I've forgotten what to do. Wish I had kept one of my old xorgs for reference...

I used to have one of those ATI cards on my old Compaq, but when I was setting it up a few years ago, I was able to switch it out with an nVidia card instead...

Did a google search, and although it's from a few years ago, it might help out:
[http://forums.debian.net/viewtopic.php?t=6593](http://forums.debian.net/viewtopic.php?t=6593)

---

### Post by khelben1979 on 2009-09-10
> **djginormousdrew said:**
> I appreciate your good intentions, but you posted a link to a page describing the utility xorgconfig - but there was no link to get the utility, and it doesn't appear to be included in Ubuntu.

Have you tried dexconf? (search for it in Synaptic if it's not installed, I know Debian has had it and Ubuntu is based on Debian so it might be included as well)

[dexconf man page]("https://www.cs.drexel.edu/cgi-bin/manServer.pl/usr/share/man/man1/dexconf.1").

---

### Post by manolomanolo on 2010-07-31
Hi. I have the same video card but videos from youtube are not fluent.
I have been trying with Ubuntu 10.04, gOS, gNewSense and PUPPY but the problem persists.

[LIST=1]
[*]Is it a hardware problem?
[*]How can I be sure the video card is running with the correct drivers?
[*]Is there any BIOS setting I should modify to make it work better?
[/LIST]

Thanks.

---

### Post by Mark Phelps on 2010-07-31
> **manolomanolo said:**
> ...Is it a hardware problem?
Basically ... yes.  That hardware is so old that there are no ATI drivers that will work with it anymore.
> How can I be sure the video card is running with the correct drivers?
That's easy ... if you're seeing a graphical desktop, you are already running the ONLY drivers available -- the open source drivers.
> Is there any BIOS setting I should modify to make it work better?
No, there aren't.

---

### Post by manolomanolo on 2010-08-01
Mark Phelps, thanks for your reply.

Wow! A 3d card that is not able to play youtube videos on Gnu/Linux?!?

Is it the same with Windows?

---

