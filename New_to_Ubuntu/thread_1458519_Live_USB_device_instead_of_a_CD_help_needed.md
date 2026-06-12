---
title: "Live USB device instead of a CD help needed"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by Peterfc on 2010-04-20
Hi All

I often have access to other peoples computers but would rather use Ubuntu linux and a Live Usb device would allow me to do this.

Where do i start to do this, i can find how to create a live CD.

Peter

---

### Post by lotharmat on 2010-04-20
[Unetbootin]("http://unetbootin.sourceforge.net/") is probably one of the best.

If you need a persistent partition to save files - or keep installed apps; go for [pendrivelinux]("http://www.pendrivelinux.com/")

Both are fantastic apps!

---

### Post by r-senior on 2010-04-20
There's a menu option in Karmic that pretty much walks you through the process. System -> Admin -> USB Startup Disk.

You need to have a suitable ISO image downloaded (as you would have for burning a CD), plus a blank USB stick. You can store settings and files on a USB disk, but don't make swap space on it because apparently that reduces its life if it gets used.

Some older computers won't boot off a USB stick, others need you to intercept the boot process by pressing a key (watch out for messages on screen in th eearly stages of the boot) and selecting a boot device.

---

### Post by VeeDubb on 2010-04-20
> **r-senior said:**
> There's a menu option in Karmic that pretty much walks you through the process. System -> Admin -> USB Startup Disk.


Just to add to this, I've found that installing from USB drive is also mind bogglingly fast.  Boot to fully installed system was about 10-15 minutes tops.

With a CD, I've found it's anywhere between 20 and 40, which is still amazingly fast compared to windows.

---

### Post by lotharmat on 2010-04-20
I'm planning on installing Lucid from a USB stick!

Windows 7 installed from USB in just shy of 8 minutes! - That was quick!

---

### Post by P4man on 2010-04-20
> **r-senior said:**
> There's a menu option in Karmic that pretty much walks you through the process. System -> Admin -> USB Startup Disk.


In my experience its buggy as hell (the stick formatting part). Its also in desperate need of some changes that will prevent the user from accidentally formatting the wrong USB drive (yes, i killed a 1TB external USB drive, just one click, no confirmation prompt, and gone was my data).

I vote for unetbootin until the gnome utility becomes more mature.

---

### Post by r-senior on 2010-04-20
Aye, it's true. The formatting part is awkward but once you figure out how to get past the formatting stage, it works OK. Well, I've found it OK anyway. I had Lucid Alpha running on one until I needed it for something else.

---

### Post by rogerpittman on 2010-04-20
I keep a 16 GB USB drive on me at all times with Ubuntu 9.04 installed on it - very useful for working with other people's laptops. One buddy of mine was agape at the fact that I got access to his 'password protected' laptop and retrieved data from it with no effort at all.

---

### Post by LewRockwell on 2010-04-20
> **rogerpittman said:**
> I keep a 16 GB USB drive on me at all times with Ubuntu 9.04 installed on it - very useful for working with other people's laptops. One buddy of mine was agape at the fact that I got access to his 'password protected' laptop and retrieved data from it with no effort at all.

Most people have absolutely NO clue about security issues of any sort, just click, click, click...go, go, go...yes, yes, yes...

[http://en.wikipedia.org/wiki/Internet_security](http://en.wikipedia.org/wiki/Internet_security)

Because...like...ya know...I'm sure...hahaha!

[sarcasm]Everyone just KNOWS you need nine toolbars cluttering up your browser space[/sarcasm]

[http://en.wikipedia.org/wiki/Bloatware](http://en.wikipedia.org/wiki/Bloatware)

.

---

