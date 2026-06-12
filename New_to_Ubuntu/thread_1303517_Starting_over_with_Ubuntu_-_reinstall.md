---
title: "Starting over with Ubuntu - reinstall?"
date: 2009-10-28
forum: New to Ubuntu
---

### Post by JoeMontibello on 2009-10-28
Hi,
 
I have a lousy old computer. A few years ago, I installed Ubuntu (I think it was 5.10) from an image that I downloaded. I played around, but the computer didn't really have the memory to support the distro, so I stopped using. It sat in the cellar.
 
I recently got a bit more memory for it, so I thought I'd try again. But of course, I don't know my old login and password. What I'd like to do is start from scratch with another install of Ubuntu (or another Linux if I have to, but I need something relatively friendly). 
 
Anyway, I've tried a newer livecd version of Ubuntu. When I try to install it (or even run it from the CD), the X server fails and I get to a command prompt. That's not going to work for me.
 
I also tried burning an image of Damn Small Linux to a CD, but that wouldn't install either.
 
Any ideas? This is an old HP Pavilion, 256MB Ram and a lousy processor, and I really don't have any money to put into it. I have a bunch of blank CD's, so I can try to install from a CD, but I'm not sure why that isn't working with the distros I've already tried.
 
Any help at all would be greatly appreciated. Thanks.
Joe

---

### Post by Mighty_Joe on 2009-10-28
> **JoeMontibello said:**
>  
I also tried burning an image of Damn Small Linux to a CD, but that wouldn't install either.


Try [Puppy Linux]("http://www.puppylinux.org/").  It's more forgiving of old hardware than Ubuntu.  
Are you sure the hardware is still functional?  Can you install an old version of Windows to make sure?

---

### Post by laidback on 2009-10-28
I would suggest that you have a look at Xubuntu, a release specifically designed for lower powered machines, it needs a minimum of 192Mb of Ram (v9.04) so will probably run on your old PC.

Google for it and you get access to the downloads. 

[http://www.xubuntu.org/get](http://www.xubuntu.org/get)

---

### Post by JoeMontibello on 2009-10-29
Ok, I downloaded Puppy and Xubuntu.  With Puppy, it seemed to hang up during installation with a weird "x" shaped cursor that I could move, on a black background, nothing else.
 
With Xubuntu, it hung up on a screen where you have to choose your time zone by location.  I could see the map of the world, and click around all I wanted, and it was slow but it would update the little pulldown menus with the regions I was clicking.  But, next and back were both greyed out, and even quit wouldn't work...it responded to my clicking the buttons but didn't go anywhere, even after clicking quit multiple times.
 
I'm trying Puppy again now...wish me luck.

---

### Post by humphreybc on 2009-10-29
Are you using the alternate CD for Xubuntu?

---

### Post by ranch hand on 2009-10-29
I would try a minimal Ubuntu install (strictly CLI) and then;
```

 apt-get install lxde lxde-common lxde-core lxde-setings-daemon

```
I also believe that you can up that ram to 512 (max).  I have a HP pavilion xt993 running Intrepid and it had 128ram.  I got 2 brand new sticks, 256Mb, for $10.00 on ebay.  With the lxde it should run real well.

---

### Post by earthpigg on 2009-10-29
hi,

one thing you may want to consider since this computer has been sitting in a corner somewhere: open it up and clean the dust out! i have seen non-trivial performance improvements as a result of just doing that.

i wouldn't bother with xubuntu. the performence difference between xubuntu and ubuntu is negligible.

here's three options ill throw out there, sticking in the ubuntu family:

-Crunchbang - tried and true, very popular.
-Spri - lighter than the other two. lightest graphical ubuntu derivative i am aware of.
-Masonux - i am biased, though, since Masonux is mine :D

---

### Post by coolbrook on 2009-10-29
I agree with Ranch Hand, but if you really like Puppy then you may have to download and install a "retro" version to get it running.  It's not as old as the name implies.

---

### Post by earthpigg on 2009-10-30
> **ranch hand said:**
> I would try a minimal Ubuntu install (strictly CLI) and then;
```

 apt-get install lxde lxde-common lxde-core lxde-setings-daemon

```

will not work, i've tried it :D

lxde will install gdm, which is a semi-broken package at the moment. yay new gnome super-integration and complete non-modularity. 

also, iirc lxde will install lxde-common and lxde-core and lxde-settings-daemon.

---

### Post by ranch hand on 2009-10-30
I have to get my HDDs in order so that I can play with new stuff.  Sorry about that, it works for installing WITH gnome.

---

### Post by paynek716 on 2009-10-30
> **Mighty_Joe said:**
> Are you sure the hardware is still functional?  Can you install an old version of Windows to make sure?

Joe

I'm no expert on Ubuntu but have over 20 years experience troubleshooting radios on aircraft. From a troubleshooting perspective you have a lot of unknown variables happening at the same time.

You may want to make sure the hardware is working before going any further. This can take some time but may save considerable time and frustration in the long run. It will also give you a known state from which you can add changes incrementally. In good troubleshooting, unless you are confident of the root cause of the problem, you only change one variable at a time.

Will the computer start with original OS? If not I would probably reload the original OS as a starting point. You may even want to reformat the hard drive, then reload original OS. I assume data loss is not a concern.

If you don't want to install or run the original OS, you may want to format the drive then try loading a particular Linux flavor. This will at least give you a known state as a starting point.

---

### Post by admelfo on 2009-10-31
I'm running Ubuntu Hardy LTS on a 10-yr-old Compaq Armada M300 laptop which had been sitting unused for about 3-4 years and was sloated for the trash, but I got curious and gave Ubuntu a try.

Initially, I had the same lag during install with the time/date config utility. I'm no expert, but I'd guess that it's b/c you're installing offline -- and Ubuntu is looking for a connection to update the system date/time, because I only ran into this when I was booting up offline. Keep your ethernet plugged in while it's going through the installation and see if that helps.

My battery was shot, so anytime I needed to move the box and plug it in at another location, I got the error again. Try resetting your time in your BIOS. In my case, Compaq had some proprietary BIOS utility that ran under Windows, which was of course gone now. If that doesn't take, check your sys battery -- it's a little round thing, along the lines of a watch battery, that keeps your system date and time current when it's shutdown. Mine was apparently dead, but I was able to find a new one on eBay for about ten bucks -- replaced it, and it's been fine ever since.

---

