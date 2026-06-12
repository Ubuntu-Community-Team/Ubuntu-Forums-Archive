---
title: "Video dell inspiron 600m"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by fattyz on 2010-07-07
Most everything is working.  Some small things like water effect in Compiz and some random reboots, Animated wallpaper, transparent desktop cube, cairo dock with open gl etc all work.  

I was wondering if there was an upgraded video driver but, it ain't really broke, so I am not really in a rush to fix it.

Anyone know anything about this?

FattyZ

---

### Post by fattyz on 2010-07-08
Well, I might as well add this on the video topic.  After my third re-install of 10.04 I really DON'T think it's a great idea to run compiz and cairo dock together.  (at least not on my rig)  I can't be sure but my experience leads me to think that one tweak to many with everything 3D in the world running makes the system have a fatal crash.  (today I lost my networking and the computer just kept rebooting itself unless I started in gnome restricted)  I suppose I could have removed cairo dock in that mode but I don't even remember if it was there, because I was getting two compiz Icons as well along with a bunch of other burps and hiccups.  Oh well, live and learn.

Time to put humpty dumpty back together again.

FattyZ

---

### Post by fattyz on 2010-07-10
you know, I think i'm on the point of revising my glowing reviews of this distro.  after reinstalling it the third time, and trying to remember everything you have to do to get it working, it's not for the faint hearted and really shouldn't have been released in this state, full of *** ache bugs, which is what microsoft was forever guilty of.

I just spent an hour (again) digging through piles of rubbish to find out how to get the vaunted Ubuntu 10.04 to allow me to watch a dvd in my own dvd drive,  Ha ha what a pain in the ***.  My wife is mad as hell that I've been sitting in front of the computer for weeks and I think the investment in a new laptop to run windows would almost pay me the hourly rate I earn at work for sitting in front of this thing making it work.

Big deal, I know how to work Ubuntu.  That and 2.50 will buy you a cup of coffee, and I'm hardly out of the woods at that.  There are still plenty of things I have not tried yet that I'm sure will take even more time that "would just work" If you had windows or a mac.  sigh.

Time being money, I'd hardly call linux "free".

FattyZ

---

### Post by fattyz on 2010-07-15
Another neat trick included by the developers is the way small updates via synaptic or software center make things vanish.  Granted, I'm pushing the OS to do the things it is touted to do, like 3d desktop and animated wallpaper.  Still, having the sound stop working or the network icon or the max min buttons in firefox vanish requires an in depth knowledge of the ubuntu forums to repair without re installing the OS.  Congratulations!

Still and all, it's way more advanced and very much superior to anything windows has ever done, which also deserves congratulations.

FattyZ

---

### Post by fattyz on 2010-07-16
I am screwing around with compiz and this (or maybe just multiple reboots) makes the system lose my sound card.  The little speaker appears with a ---
and none of the sliders make it work.  Luckily, I found this under "soundtroubleshooting" in the ubuntu documentation. sudo aptitude --purge reinstall linux-sound-base alsa-base alsa-utils linux-image-`uname -r` linux-ubuntu-modules-`uname -r` libasound2.

After a couple cold boots, the sound comes back.  Why is it doing this?

Yours, fattyz

As an aside, I am looking into remote desktop and other third party software to save myself the trouble of trying to get the LAN to work at home.  Quite impossible.  Same with windows.  When I tried to network this laptop running xp wireless to the windows 7 box.

We still have a long way to go.

---

### Post by fattyz on 2010-07-22
In a new twist on the 10.04 networking debacle, I got the bright idea today to fire up wubi on the windows 7 machine and check the network.

Sure enough, there was the laptop running 10.04, all shares available, right out of the box.  Going back to check access to the laptop it is still unable to access the remote box, even with 9.04 running, and behaves the same was as if it were running Win 7.

This is really a problem and I hope a bug fix is released soon that'll make networking as simple as it was in 9.04 (which I think had no problems seeing my win7 machine).

The laptop is incapable of even running XP acceptably Both distros of ubuntu run great on it) so there is no option to dual boot back into windows and besides, trying to network XP and Win7 was just as much of a nightmare though I finally got it working.

Am I missing something in trying to see the 9.04 box from the laptop?  Do I have to do a new search or something like that?  The 10.04 laptop is looking for windows shares on the other box so maybe there is a tweak I can do to make it see 9.04.

Any help would be greatly appreciated.  

Ubuntu Novice
FattyZ

---

### Post by fattyz on 2010-07-28
Everything sees the two computers and is able to connect except windows 7 and ubuntu 10.04.

dual booting into 9.04 on the windows box lets me connect to the 10.04 box but not the reverse

third party file share programs work no problem (teamviewer)

Printing from 10.04 to the printer on the win 7 box works no problem

10.04 seems to connect to the windows box but either asks for a password (under computer/win7 box) or shows a blank screen (network/windows 7/mshome/blankscreen)

9.04 just worked.

any help appreciated.

FattyZ

---

### Post by fattyz on 2010-08-06
I didn't solve the network issue, and I probably won't have to now until it gets easy enough.  I found the cloud computing Icon and set up a free account.  Now I don't need to have the computers hook up, though it'd be nice to "make it work".  The cloud will do for simple file transfer, and it's easier than USB drives.

The only reason I'd want a REAL network is gaming anyway and this laptop is not able to run anything (except maybe DOOM or maybe QUAKE 3,) worth playing anyway.  And file transfer.

I think it's to bad it's such a pain in the butt to make it work but, other than that I'm pretty much loving it.  Been running all kinds of wallpapers and compiz (most effects work, due to the old video card, not everything)  Everyone is amazed at the cube and 3d desktop and all, and open office is great so it's pretty hard to see how you can lose.

Most of the time I invested in it I wanted to anyway, even though I like to complain, but it's great to have become part of the counter culture and unplug myself from the matrix.

FattyZ

---

### Post by fattyz on 2010-08-06
I didn't solve the network issue, and I probably won't have to now until it gets easy enough.  I found the cloud computing Icon and set up a free account.  Now I don't need to have the computers hook up, though it'd be nice to "make it work".  The cloud will do for simple file transfer, and it's easier than USB drives.

The only reason I'd want a REAL network is gaming anyway and this laptop is not able to run anything (except maybe DOOM or QUAKE 3,) worth playing anyway.  And file transfer.

I think it's to bad it's such a pain in the butt to make networking function when it worked fine in the last version but I'm sure they'll fix it eventually. Other than that I'm pretty much loving it.  Been running all kinds of wallpapers and compiz (most effects work, due to the old video card, not everything)  Everyone is amazed at the cube and 3d desktop and all, and open office is great so it's pretty hard to see how you can lose.

Most of the time I invested in it I wanted to anyway, even though I like to complain, but it's great to have become part of the counter culture and unplug myself from the matrix.

FattyZ

---

### Post by fattyz on 2010-09-01
So after considerable success with my laptop I decided to take my old xp desktop and convert it to ubuntu, WOW was I in for a shock.

First of all, no matter what I couldn't get the cd to boot, even thought other cd's would.  Secondly, the machine is to old to boot from a usb, though the choices in the bios make it look like it should.

Well, I've been at it about 3 weeks and if I don't get it this time, the thing is going in the trash.  (where it probably belongs anyway)  At the time I built it it was a high end gaming machine so i figured what the hell, ubuntu will run great on it.

Once I finally did get a "real" install, not WUBI after endless searching, the screen was flashing so bad you couldn't use it.  Well, I read up on that now and I think I can get it going, but I've been thinking that all along!  Ha Ha.

FattyZ

---

