---
title: "Flash"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by blur xc on 2009-06-07
Well, been searching around and it seems that Ubuntu isn't in any danger of having a shortage of flash issues...  so- here's mine.

Mostly, it works o-k...  But there are a few quirks.  You tube works well enough, except in hq mode.  Total dud.  Flash websites don't seem to play automatically.  I have a big grey play button thing, that once I click, the website loads normally (as far as I can tell anyway).  Teagames- not so good.  It'll load, but the refresh/fram rate stinks, and not all the graphics are displayed.  For example, on tg motocross 3, I can see the motorcycle, but not the ground...hard to play the game that way...  I'm using the nvidia driver version 180.44, if that matters.

My pc has plenty of horsepower for 3d graphic effects, so that's not an issue.

Thanks,
BM

---

### Post by kansasnoob on 2009-06-07
I really need to know what version of Ubuntu you're using. 8.04, 8.10, 9.04? Ubuntu, Xubuntu, Kubuntu?

---

### Post by presence1960 on 2009-06-07
if you use 64 bit ubuntu uninstall all instances of flash. Then go here to our forum x86-64bit User section to get Adobe Flash [http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

A lot of people will tell you to go to Adobe's site directly, but this is Adobe Flash and is a one click install. It has worked flawlessly for me on Hardy, Intrepid & Jaunty. 

I went to that site and the red bike is awesome.

P.S. if you have any instances of swfdec uninstall it, it is bolderdash!

---

### Post by blur xc on 2009-06-07
Sorry- 32bit Ubuntu 9.04, been using it for a few days now.

I'll get rid of swfdec asap...what is it anyway?

BM

---

### Post by presence1960 on 2009-06-07
open synaptic package manager- System > Administration > Synaptic Package Manager. In search type swfdec and hit enter. If the search shows swfdec-mozilla or swfdec-gnome with a filled in box it is installed.  Click the box and mark it for complete removal. Click apply at the top and it will be removed. I don't know how you installed Flash, you can run this in terminal ```
sudo apt-get install flashplugin-nonfree
``` You want to have medibuntu enabled first. Or you can go to Adobe's site and download the deb for the newest Flash.

---

### Post by jerome1232 on 2009-06-07
That really, really, really looks like an addon for firefox I once had that automatically blocked flash content. It put a grey box like that with a play button so you can manually start any flash content on the page without having it all autoplay.

I think the addon was called flashblock? Do you happen to have that installed?

---

### Post by blur xc on 2009-06-08
Ok, I don't know what medibuntu is, so how do I know if it's enabled or not, and if not, how do I enable it?  I canned the swfdec-mozilla package- and the grey play button appears to have vanished...

But Teagames still doesn't work (or works worse)...  So, I checked my firefox add-ons, and I've got two Shockwave flash add-ons- a 10.0 r22 and a 9.0 r999.  What are those and do I need them?

Some time ago I installed the real Adobe Flash plugin...

thanks,
BM

---

### Post by Fully216 on 2009-06-08
Medibuntu (Multimedia, Entertainment & Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc).

Some of these packages include the libdvdcss package from VideoLAN and the external binary codecs package (commonly known as w32codecs) used by MPlayer and xine.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by presence1960 on 2009-06-08
> **fully216 said:**
> medibuntu (multimedia, entertainment & distractions in ubuntu) is a repository of packages that cannot be included into the ubuntu distribution for legal reasons (copyright, license, patent, etc).

Some of these packages include the libdvdcss package from videolan and the external binary codecs package (commonly known as w32codecs) used by mplayer and xine.

[https://help.ubuntu.com/community/medibuntu](https://help.ubuntu.com/community/medibuntu)

+1

---

