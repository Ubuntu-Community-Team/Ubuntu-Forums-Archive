---
title: "handbrake can't find dvd source"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by Captain_Glen on 2009-04-09
Hi,

I am trying to rip some dvds.  When I use hand brake and select my dvd drive it says scanning... and then shows no source

---

### Post by o.besner on 2009-04-09
Have you installed libdvdcss ? It is the package that enables Handbrake to crack the DVD CSS protection.

---

### Post by Captain_Glen on 2009-04-09
I have tried too.  Probably not.  How do I do that?  I can't play dvds either so I don't think I have installed it.

---

### Post by Yoshis88 on 2009-04-09
If you are using Intrepid Ibex ([8.10), it should be noted that playing DVD's is broken.  Some of the sadness is documented in the relevant [Launchpad bug report]("https://bugs.launchpad.net/ubuntu/+source/gst-plugins-bad0.10/+bug/260765").

I will discuss what I have done to fix DVD playing in Intrepid.  Whether this will help your DVD ripping issue, I'm not 100% sure.  But I do believe this will help you get closer to where you want to be.

The libdvdcss2 library must be installed, and the repository provided version will work.
```
sudo apt-get install libdvdread3
sudo /usr/share/doc/libdvdread3/install-css.sh
```

However, the gstreamer package is what "provides" the broken functionality.  Let's remove it before we put a nicer version in.
```
sudo apt-get remove gstreamer0.10-plugins-bad
```

Now!  Follow [this link]("http://mirror.linux.org.mt/ubuntu/pool/universe/g/gst-plugins-bad0.10/") to a mirror of .debs for the package of interest.  We are looking for an older version for "gstreamer0.10-plugins-bad".  The reason why a newer one will not suit us so much is because then a whole bunch of other dependencies also need updated, so the process is a fair bit hairy-er.  DVDs worked in Hardy, so why not [choose that version]("http://packages.ubuntu.com/search?keywords=gstreamer0.10-plugins-bad&searchon=names&exact=1&suite=all&section=all")?  I selected this deb to download:
```
gstreamer0.10-plugins-bad_0.10.6-5ubuntu0.1_ARCH.deb
```
where ARCH is "i386" for 32-bit platforms and "amd64" for 64-bit platforms.

Upon finishing download, simply install the package.  Graphically, this can be achieved by simply double-clicking the .deb, and you'll see a nice big honking button for you to install it (can't miss it!).  Me, I prefer the terminal, and would do it with "dpkg -i abc123.deb", of course saying yes to any silly requests it asks.  Upon completing install of the package, I find DVD playback is restored!

A nice annoying icon then appears which "informs" you that the gstreamer package you just installed is outdated, and offers you a new version (the version you had, the broken one :P).  I like to squelch this annoyance by simply going to
```
System > Administration > Search for "gstreamer0.10-plugins-bad"
Then, select it with a single click, go to
Package > Lock version
Clicking Reload should remove the annoyance
```
I think I know how to do it in the command line, but I haven't tried, so I won't post it.

Please post back if this helps your situation :)

------

EDIT:  I forgot to mention, if you read the links I gave you, you'll see they definitely wanted to make sure DVD's weren't broken in Jaunty, which is officially released in 14 days.  And there should be other goodies associated with the upgrade :P

---

### Post by billgoldberg on 2009-04-09
I've written a "guide" on ripping DVD's in Ubuntu.

I just used K9copy, but if you need help with figuring out the app (it's drop dead easy to use), check it here:

[http://linuxowns.wordpress.com/2008/10/07/how-to-rip-a-dvd-in-ubuntu-to-avi-the-easy-way/](http://linuxowns.wordpress.com/2008/10/07/how-to-rip-a-dvd-in-ubuntu-to-avi-the-easy-way/)

---

### Post by Captain_Glen on 2009-04-09
I can now play dvds.  Handbrake is working for some of my dvds but not all of them.  For some dvds it only finds one or two files when I know there are 4 files.  Also some times  it crashes and closes.

---

### Post by Yoshis88 on 2009-04-09
Well, I'm not sure what to say now.  I expected you'd be able to play DVDs now.  I didn't know what this would mean in terms of ripping.

It actually is fate enough that I reformatted my computer :P.  I decided to put my little tutorial to the test and it does work for getting DVD's to play, using totem-xine as the preferred backend, everything is pretty seamless.

I installed the newest Handbrake (0.9.3) from the .deb downloadable from their site.  So new, it has a GUI! (Back when I first used Handbrake, it didn't have a gui).  But it appears to work for me, granted, I only had the time to test it on one DVD (Serenity -- oh sweet Firefly *sigh*).

Sadly, this means I'm out of ideas besides "wait for Jaunty" :/  Anybody else got their two cents?

---

