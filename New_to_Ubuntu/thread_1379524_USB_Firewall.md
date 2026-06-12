---
title: "USB Firewall???"
date: 2010-01-12
forum: New to Ubuntu
---

### Post by pathfindermwd on 2010-01-12
Hi All.  I have been doing some reading up on security at Ubuntu documentation.  I have been trying to work on a firewall and antivirus for my Live USB 9.10 4 gig persistent.  Having just recently done a (botched) installation og Ubuntu, I realised that there were differences between an installed version and a USB version.  Namely a login, and a requirement to enter a password when trying to install the Wireless driver on the installed version.  I havnt come accross a document that discusses security on a Live USB, vs an install

I want to make sure it doesnt look as if I don't want to install Ubuntu.  I just initially got interested in the live USB as a way of  not only having a ultra portable computer/browser, but also as a physical layer of protection/separation for all my files on the hard drive (yes currently in windows).  

What concerns should I have for using the Live USB with no firewall?

Thanks!

---

### Post by marshmallow1304 on 2010-01-12
Why do you need firewall and AV?


To enable the firewall, open a terminal and issue
```
sudo ufw enable
```

---

### Post by pathfindermwd on 2010-01-12
> **marshmallow1304 said:**
> Why do you need firewall and AV?


To enable the firewall, open a terminal and issue
```
sudo ufw enable
```

Lol, I don't know.  I mean not only do I not know, but for all the good reasons which exist that I am not aware of.

I did do that, and a screen flashed for a second, so fast I couldn't read it, so I did it again but nothing.  I also tried to install it by clicking on the link but got an error message.   I guess I'm concerned that there is no firewall option In system administration.

And no asking for passwords for anything.

---

### Post by marshmallow1304 on 2010-01-12
OK.  Perhaps you will be more comfortable with [gufw]("apt://gufw"), as it is graphical.  I believe it shows up in System->Administration.

> **pathfindermwd said:**
> And no asking for passwords for anything.
That's a convenience of the live environment.

---

### Post by pathfindermwd on 2010-01-12
> **marshmallow1304 said:**
> OK.  Perhaps you will be more comfortable with [gufw]("apt://gufw"), as it is graphical.  I believe it shows up in System->Administration.


Yeah, I know.  But it isn't there.  Apparently because this isn't really an install?  I did enable it in a terminal, but is it really working, is it even installed?  How do I find out?

I set up passwords too but it doesn't ask me for them when I boot?

---

### Post by marshmallow1304 on 2010-01-12
> **pathfindermwd said:**
> Yeah, I know.  But it isn't there.  Apparently because this isn't really an install?  I did enable it in a terminal, but is it really working, is it even installed?  How do I find out?

ufw is installed by default, but it is not a graphical program, so it will not show up in System->Administration.  gufw is a graphical version, but it is not installed by default.  To install it, click on the link I provided or use Synaptic (or Software Center).


As for the passwords, maybe check System->Administration->Login Screen.  I've never tried passwords in a live environment, so I don't know if it's possible anyway.

---

### Post by pathfindermwd on 2010-01-12
> **marshmallow1304 said:**
> ufw is installed by default, but it is not a graphical program, so it will not show up in System->Administration.  gufw is a graphical version, but it is not installed by default.  To install it, click on the link I provided or use Synaptic (or Software Center).


As for the passwords, maybe check System->Administration->Login Screen.  I've never tried passwords in a live environment, so I don't know if it's possible anyway.



Thanks marshmallow, I appreciate your assistance.  I wasnt very clear, I have previously followed the link for the gufw on the documentation page here:[https://help.ubuntu.com/9.10/keeping-safe/C/firewall.html#id2774297](https://help.ubuntu.com/9.10/keeping-safe/C/firewall.html#id2774297) choosing apturl to open with (only choice), and it says it couldnt find GUFW.  It also gave me that message at the link you provided.  I also tried to download it using the software center under Applications but it told me says "not available in current data".  It gives me this message for all firewall programs listed there.

I think It isn't available in live formats do you still think I shouldn't worry about it?

---

### Post by bodhi.zazen on 2010-01-12
A default installation of Ubuntu has no significant servers listening by default and so in your situation I do not feel you gain much of anything by enabling your firewall.

Also, as you have discovered, there are multiple ways of installing to USB. 

One way is similar to booting a CD and your changes are not saved. If you go this route, you most certainly do not need a firewall.

The other is using USB creator, or similar, and in that event you may want to look at a firewall. With this method your changes are saved between sessions.

To install GUFW you need to enable the "universe' repository, then update, then install.

sudo apt-get update
sudo apt-get install gufw

[InstallingSoftware - Community Ubuntu Documentation]("https://help.ubuntu.com/community/InstallingSoftware")

---

### Post by pathfindermwd on 2010-01-12
Thanks very much bodhi.zazen.  

I am going to try that right after dinner.

I did originally plan to use the live cd but needed the add-on of a password manager, and some data storing.  Plus, I couldn't resist trying a USB O.S., very cool, and much faster than cd!

Lol, when I went up to Best Buy to get a big thumbdrive i asked the kid there about USB's that have a physical switch knowing I might be venerable. He sent out the geeksquad guy who asked about my application.  He didn't believe an OS could be put on a USB, lol, I still have to get back up there and show it to him, though I couldn't find one with a switch.

I have not run across an explenation of the differences in the various size persistent installations.  Do you know where a newbie could read about that?  I'd like to know what 4 gigs does vs 2.

---

### Post by bodhi.zazen on 2010-01-12
I am no certain, but basically my understanding is

The 4 Gb size is more of a standard installation and one then simply boots to USB.

The 2 Gb version uses casper to compress the installation.

---

### Post by pathfindermwd on 2010-01-12
> **bodhi.zazen said:**
> I am no certain, but basically my understanding is

The 4 Gb size is more of a standard installation and one then simply boots to USB.

The 2 Gb version uses casper to compress the installation.
Thanks again, I now have a firewall, very easy!

Care to chime in about the password program that is set up but still doesnt offer a login at bootup?

---

