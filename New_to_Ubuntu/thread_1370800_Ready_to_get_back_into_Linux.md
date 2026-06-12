---
title: "Ready to get back into Linux"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by LA Snow on 2010-01-02
Hello all.  I used Slackware Linux back in 1999 with Windowmaker for a little bit.  Was cool, but the command prompt seemed to be a little much for a casual user like me who listens to music, plays video games and looks at web pages.

Now 11 years later, it's obvious the scene has changed.  You can actually do things with the GUI and it seems easier to manage.

After a lot of research, I've decided on Ubuntu or an Ubuntu derivative, just wondering which one.  I'm real big on aesthetics, and I loved how the GUIs like Afterstep looked.

So here are my questions.  I'm into aesthetics and have decent system specs, so I'm looking for a sweet looking GUI.  Also looking for ease of use and do not need anything like server administration or video editing.  Just wireless connectivity for a laptop and the ability to do day-to-day tasks.  Also, I'd like to put a 64 bit version on my desktop since it has 8 gigs of ram.  Going to start out with a laptop.  Both machines currently run Windows 7.

Which derivative if any do you recommend?  I'm going to read the pocket guide all the way through.  What's the difference between KDE and Gnome?  Is that the major choice to make on which Ubuntu to get?

Sorry for the remedial questions and I hope to get back into Linux and be a part of the community.  Thanks!

---

### Post by thatguruguy on 2010-01-02
A lot of people think that KDE is prettier.  I personally prefer gnome, because I think it's a little easier.  If you go with gnome, make sure to get compiz set up to enable all the bells and whistles.

You can always install the kubuntu desktop after installing ubuntu, and then select from both at boot-up so you can decide which you like better.  Enjoy!

---

### Post by LA Snow on 2010-01-02
So the best way to install is to burn the ISO to a disc and do it that way and partition during setup, correct?  I want to avoid those Wubi woes I've heard about.

---

### Post by Thelasko on 2010-01-02
> **LA Snow said:**
> So the best way to install is to burn the ISO to a disc and do it that way and partition during setup, correct?  I want to avoid those Wubi woes I've heard about.

Yeah, [Here's some help with ISO files if you haven't used them before.]("https://help.ubuntu.com/community/BurningIsoHowto")

---

### Post by LA Snow on 2010-01-02
When it says I can boot from a USB, that's not the same thing as Wubi is it?  Can I do that and get just as clean as an install as a disc?

---

### Post by ssulaco on 2010-01-02
I would recommend running the ISO "live" to see how you like it,I have a pile of Linux distros on cd,also you will be able to tell if your hardware likes it also,Then you can pick the distro you like
take a look at [http://distrowatch.com/](http://distrowatch.com/)   for different distros
here is a guide on using a live cd:
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)

---

### Post by theozzlives on 2010-01-02
You can create an install just like the CD from USB, providing your system boots from USB. You're right, Linux has matured a lot over the years.

---

### Post by mechro on 2010-01-02
> **LA Snow said:**
> When it says I can boot from a USB, that's not the same thing as Wubi is it?  Can I do that and get just as clean as an install as a disc?

Generally the USB option refers to running a copy of a Ubuntu LiveCD installed on a USB stick.

---

### Post by ssulaco on 2010-01-02
> **LA Snow said:**
> When it says I can boot from a USB, that's not the same thing as Wubi is it?  Can I do that and get just as clean as an install as a disc?
No....here is Wubi install:
[http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi)

Yes..usb install:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Paqman on 2010-01-02
> **LA Snow said:**
> 
Which derivative if any do you recommend?


The default is Ubuntu, i'd start there.


> What's the difference between KDE and Gnome? 

A different crop of default apps, different menus and config tools. But otherwise not much. You can run KDE apps on Gnome and vice versa.

In fact, you can easily switch between KDE, Gnome, and XFCE. The meta-packages ubuntu-desktop, kubuntu-desktop and xubuntu-desktop will install the whole desktop environment, and you can pick which one you want when you log in.

You'll find there's a world of difference between Ubuntu and 1999 Slackware, btw ;)

---

### Post by ST3ALTHPSYCH0 on 2010-01-02
With a decent system and the desire for A lot of polish out of the box, I recommend [Ultimate Edition 64 bit]("http://sourceforge.net/projects/ue-distro/files/UE-2.5/ultimate-edition-2.5-x64.iso/download"). You'll need a minimum of 15 Gb for your system partition, but it come with tons of themes installed and the ability to select between Gnome, KDE, and Xfce every session right out of the box. It's not officially Ubuntu, but it's built thereon. Also, you'll need a DVD or a 4 Gb USB to put the iso on. To make a live USB from the iso download [unetbootin](http://sourceforge.net/projects/unetbootin/files/UNetbootin/377/unetbootin-windows-377.exe/download).

---

### Post by tilixibr on 2010-01-02
> **LA Snow said:**
> So the best way to install is to burn the ISO to a disc and do it that way and partition during setup, correct?  I want to avoid those Wubi woes I've heard about.

I agree, I had a problem with wubi when I first installed Ubuntu, I always got a message saying that the filesystem failed to mount. Wubi doesn't actually create a partition, it creates a virtual disk, kind of like the one that is used with VMWare. I strongly suggest burning a live CD.

---

### Post by anewguy on 2010-01-03
I also used Slackware back about 1995 or so.  As an ex-systems programmer and ex-systems administrator (in those days I was still working) I found it fun in those days to dig into stuff as much as I could.  Now, in my older age, I only dig into the things really important to me, and installing Linux like the old days was/is not one of them.  My suggestions?

(1) Just go with the standard Ubuntu LiveCd, give it a try, and if you like it select the install option. 

(2) Before you actually install, do a little home work in the following areas:
[LIST=1]
[*]Find your video chipset type and check the forums (even make a post if you'd like) for potential problems with it and what driver you need - download the driver ahead of time.
[*]If you are using wireless on the laptop, check the chipset on it and then search the forum (make a post if you'd like to) for potential problems with it and download a driver ahead of time if needed.
[*]For now, and this is *JUST* me, stay away from 64-bit.  I had it installed for a while, but there were somethings I wanted that just wouldn't work in the 64-bit.  Also, if you end up needing to use something like ndiswrapper and/or ndisgtk in order to get wireless working, I *think* it only works with 32-bit drivers, and I'm not sure how that works with a 64-bit OS.  At a minimum do a little checking first.
[/LIST]

At least for me, "regular" Ubuntu offers the easiest installation.  Go with the default Gnome desktop until you get your feet wet, then try the other desktops.  I personally use about a 50/50 split of Gnome or KDE.  Having been "weened" in Gnome, somethings are just easier there for me, while KDE is able by default to provide a more Windows-like desktop - the menus can be made to automatically open the level, but it isn't the default.

Good luck!!  Please feel free to post ANY questions, and let use know how your experience goes!

Dave :)

---

### Post by andrew.46 on 2010-01-22
Hi LA Snow,

> **LA Snow said:**
> I used Slackware Linux back in 1999 with Windowmaker for a little bit.  Was cool, but the command prompt seemed to be a little much for a casual user like me who listens to music, plays video games and looks at web pages.

Slackware has changed more than a little since then as well and although commandline work is still required there is a very solid presence of kde and xfce. So for someone who listens to music, plays video games and browses the Internet it is a real choice...

All the best,

Andrew

---

### Post by muteXe on 2010-01-22
I agree with andrew.46.
I'm running 8.04 on my desktop and laptop. However also on my desktop is slackware 13, and I love it. I'm running fluxbox as my desktop manager though.

Personally i'm a bigger fan of gnome or xfce on ubuntu. Seems more stable to me that kde, but that just might be for me :)

---

