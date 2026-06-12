---
title: "Complete windows replacement"
date: 2009-05-21
forum: New to Ubuntu
---

### Post by sniperwire on 2009-05-21
I currently have 2 hdd's on my pc one for Vista and the other for Ubuntu. I keep this dual boot configuration because I keep running into road blocks with Ubuntu. What I am looking to do is completely use Ubuntu Linux 100% but seems like everytime I think I have it set up properly something goes wrong, things that I had working an hour ago sometimes no longer work ect. What I am looking to do is do a clean install of Ubuntu start off 100% fresh. What files should be installed ect in order for me to achieve almost windows like performance. It sort of frustrates me with Ubuntu I have experienced issues such as the desktop becoming almost non responsive I can get a few things open but others no, in 8.04 and when I tried 9.04 the computer would just lock up 100%.

Long story short I am going to do a clean install of either 8.04 or 9.04. I pref 9.04 but not if its going to cause me even more headaches. What files should I install in order to achieve a near windows like experience,watch dvd's, surf the web without constantly trying to get stuff to work such as java applets ect.

I would like to stay with Ubuntu but at this moment I'm considering trying another distribution because everytime I seem to get everything working and set up in Ubuntu the next day stuff doesn't work anymore. Does anyone have any ideas of what else I could try?  

I really appreciate everyone help and thank you in advance.

---

### Post by Cypher on 2009-05-21
First of all, what are the specs of your machine? Secondly, unless you're actively changing something, Ubuntu shouldn't change it's behavior from day to day. The only reason for breakage/change in behavior is because you did something, added something, removed something, installed a new application, etc.

If you do want to switch over to Linux 100%, there's no reason you HAVE to stick with Ubuntu. Do give distributions such as Fedora and OpenSuSE a shot since those are also very mature distributions that are well suited for people switching over from Windows..

---

### Post by rob2uk on 2009-05-21
I blame a lot of stuff on hardware issues (you'll realise that as I post more on here :P)

On your GRUB menu there should be a memtest option. Select that and let it run through, see if it picks up any faults

---

### Post by ChildOfMana on 2009-05-21
[quote="sniperwire"]watch dvd's, surf the web without constantly trying to get stuff to work such as java applets ect.[/quote]

If you do want to try another distribution you could try [Linux Mint]("http://www.linuxmint.com/"). Its based on Ubuntu and apparently - although someone feel free to correct me here - it provides support for DVD playback and Java/Flash etc 'out of the box'.

If you prefer to stick with Ubuntu try the script on [this]("http://savethegirhogs.blogspot.com/2009/01/few-things-to-do-post-installation.html") page (about half way down). Its for 8.10 (but I don't see any reason why it shouldn't work with 9.04) and it'll pull in support for restricted codecs, DVD playback, Flash Java etc all in one go.

Hope this helps.

I've been Windoze free for over a year now and never once looked back :)

---

### Post by archdlx on 2009-05-21
sniperwire....

I too, am new to Ubuntu. I have found that when I run into a problem, I look to see what was running at the time of the crash. Maybe you have a corrupt file or the wrong drivers?
IMHO, buying the DVD from the home site might be the best start for you and a clean install.

I have found that most users use different programs for the same/similar....what is the word I am looking for?......different means to the same end????

When I find that something doesn't work, flash, java, whatever, I go to the Synaptic package Manager. I search through it, and see what is recommended, (little Ubuntu emblem in front of program), try it, and if It works, and I like it, it stays. If I don't like it, or it doesn't quite do what I want, I start over.

As far as I am concered, that is the best way to learn how to use Ubuntu, or any distro, for that matter. Along with being a member here, and reading the great answers, of course!!!!

There will probably be better answers coming, but that's my .02 cents worth ;)

archdlx

---

### Post by rob2uk on 2009-05-21
> **ChildOfMana said:**
> If you do want to try another distribution you could try [Linux Mint]("http://www.linuxmint.com/"). Its based on Ubuntu and apparently - although someone feel free to correct me here - it provides support for DVD playback and Java/Flash etc 'out of the box'.

If you prefer to stick with Ubuntu try the script on [this]("http://savethegirhogs.blogspot.com/2009/01/few-things-to-do-post-installation.html") page (about half way down). Its for 8.10 (but I don't see any reason why it shouldn't work with 9.04) and it'll pull in support for restricted codecs, DVD playback, Flash Java etc all in one go.

Hope this helps.

I've been Windoze free for over a year now and never once looked back :)

I can confirm that this script works :)

Also, as a side note for forums, blogs, etc - don't just copy and paste from ANY website, be it a shady-looking blog or the official Ubuntu forums without making sure that you know what the commands do.

Ask for clarification on the Ubuntu forums if needs be, if it's potentially harmful somebody will give you a heads up :)

---

### Post by rob2uk on 2009-05-21
before I begin, sorry - I hate double-posting, but that site makes a good suggestion that I'd never thought of...

```
sudo lshw -html > pcspecs.html
```

to make a list of the hardware in your PC - makes finding drivers easy, even if you ever have to reinstall Windows or another OS

---

### Post by snowpine on 2009-05-21
There is no reason NOT to keep Windows as a dual boot. It's not going to slow down Ubuntu or make it any less stable. Dual booting can be a good crutch as you are learning more about Linux. It sounds like you still have a few issues to work out before Ubuntu is totally reliable for you. I always dual boot (Windows/Linux or Linux/Linux) on my computers so that I am guaranteed to have a working system when I need it.

---

### Post by rob2uk on 2009-05-21
> **snowpine said:**
> There is no reason NOT to keep Windows as a dual boot. It's not going to slow down Ubuntu or make it any less stable. Dual booting can be a good crutch as you are learning more about Linux. It sounds like you still have a few issues to work out before Ubuntu is totally reliable for you. I always dual boot (Windows/Linux or Linux/Linux) on my computers so that I am guaranteed to have a working system when I need it.

Agreed, to an extent. Some users may wish to ditch one OS or the other because of a lack of disk space

---

### Post by QIII on 2009-05-21
A couple of things:

1.  It will be difficult to get a "Windows-like" experience out of the box just because of the simple fact that there are so many possible combinations of available applications to do many things.  Most of us have tried many and discarded them in favor of those we like most.  Ubuntu (because it is based on Debian) generally makes that easy for you because of the Package Manager.  That is part of what endears many of us to the Linux experience.  Instead of being force-fed gruel from Redmond, we can tailor our experience to our tastes.  As you learn to use the console, you can even do more fine-grained tuning.  A few words of advice about using the console:  Don't put anything you might want later on your Ubuntu disk unless you back it up.  If you screw up in the console, you may find yourself reinstalling.  Keep a notebook with very detailed notes of what you have done.  It will help later if you have previously installed something you liked from the console and later have to reinstall.  I still have my notebook with old MSDOS and Unix notes.  Somewhere, I believe I still have notes from the way old days of punch cards, acoustical coupling devices and telephone handsets. 

2.  I wouldn't get rid of Windows entirely (even though I curse Redmond several times a day) because the reality is that it is the de-facto standard (hack, cough, spit).

If you really want to dual boot, there are a lot of tutorials out there.  Some of those are here in the Ubuntu forums.  I'm glad to hear you are doing it on separate disks, because that is the easiest way to go.

One thing I would suggest that I don't ever see in any of the tutorials is this:  Open your case and label your drives with a labeler.  Call one Windows and the other Linux, or whatever you want.  That way you can physically tell them apart.

Before you install Ubuntu, temporarily disconnect your Windows drive.  Do this at the DRIVE side, to avoid pulling a header off of your MOBO.  Put the cable aside.  If you have a cable for your Ubuntu drive already installed on a header, unplug it for a moment -- AT THE DRIVE END.  Take a look at your MOBO.  Find the LOWEST numbered header you have a hard drive cable attached to (don't take off the CD/DVD drive cable if you have your BIOS set up to boot from CD first).  Make sure your Linux drive is attached to that.  Start your machine and install Ubuntu.  Leaving the Windows disk unplugged will save you the heartache of the possibility of borking the Windows bootloader if you ever want to use that disk on another machine.  You will also avoid accidentally installing Ubuntu over your Windows drive.  (If you should encounter a problem with your startup and get a BIOS error message indicating it can't find a drive, you may have to fiddle around with which header you connect to.  Have a couple of extra SATA cables ready.  SATA headers have a nasty habit of pulling off the MOBO -- and if the pins bend you are sunk.  So I just don't ever disconnect 
SATA cables from the headers.  Leaving them there doesn't hurt anything.  Also, if, after you reboot, you find that your machine goes straight to Windows, you can just switch the cables -- AT THE DRIVE END!)

When you have Ubuntu installed, shut down.  Rehook your Windows drive.

Start back up and edit your menu.lst file (you can find tutorials about that, too).  It may take some fiddling with your menu.lst to get it all sorted out.

Just a little added advice beyond what you will likely find in tutorials.

---

