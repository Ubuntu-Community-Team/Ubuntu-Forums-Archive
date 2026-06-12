---
title: "Totem DVD playback"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by da burger on 2009-12-25
I am trying to play a dvd in totem with the GStreamer backend and it will not let me. It keeps on saying I do not have permission to open the file. Any help would be great.

I have already tried installing the ubuntu restricted extras package and the ugly plugins.

Thanks in advance
Angus

---

### Post by mgmiller on 2009-12-25
There is currently a bug in totem which prevents it from playing optical media.  This means no DVD's or CD's.  The easiest workaround currently is to install vlc from synaptic and use that for DVD playback.

Rhythmbox works well for CD's.

On the other hand, Totem seems to do a really good job on almost all kinds of avi, wmv, etc. now.  Even real media seems to work well, just no optical disks.

---

### Post by mc4man on 2009-12-25
Try adding libdvdcss2 if not already installed 

```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

---

### Post by mgmiller on 2009-12-25
libdvdcss2 is in the medibuntu repository.  True, OP does need that to play commercial DVD's, but even with it installed, Totem will not play it if he is using Karmic (9.10).

Adding the medibuntu repositories should be done anyway, to add the libdvdcss2 as well as the corefonts package and the w32codecs or w64 codecs depending on your version of Ubuntu (32 bit vs 64 bit).

Just go here and follow the instructions for some quick copy and paste:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Here is a quick cheater if you don't want to read the site:

Do the "Adding the repository" part first.
```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update
```Then select the packages to install.  For example, assuming 32 OS, you would do:
```
sudo apt-get install w32codecs
```If it's 64 bit OS, then do:
```

sudo apt-get install w64codecs
```For the DVD's do:
```
sudo apt-get install libdvdcss2
```Read the site and have fun.

---

### Post by da burger on 2009-12-25
Thanks a lot. I will just install vlc and use that.
Angus

---

### Post by mc4man on 2009-12-25
> Totem will not play it if he is using Karmic (9.10).

Not that I'm a fan or user of totem at all but it plays dvd's ok here in karmic with some limitations that may not matter to some (poor language/subtitle control

If there is a bug that you think may apply here than post link to it

---

### Post by mgmiller on 2009-12-25
Here is a link to the bug:

[https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/469603](https://bugs.launchpad.net/ubuntu/+source/gstreamer0.10/+bug/469603)

I have not been able to get totem to play DVD's on 3 clean installs of Karmic.  One is 32 bit and the other 2 are 64 bit.  

What did you do to get it working?

---

### Post by mc4man on 2009-12-25
> What did you do to get it working?

I think it always has but...

On the laptop I'm on now I haven't updated totem past the karmic release version (2.28.1). The reason for that is that version of totem-common allows a fully working totem-xine to be installed in place of the karmic dummy (local files and dvd's

I'll go ahead later and update and ck., keeping totem-xine alive is basically a lost cause anyway. (personally i intend to dump karmic for lucid as soon as practicable

I'm also using the new ugly plug-in (0.10.13-2), but I don't think that has any impact on dvd playback

Glancing at the various reports they seem to be either lack of libdcdcss2 (not your issue) or failure to read the VIDEO_TS.IFO properly

Do you have any particular titles that don't work?, I have a lot of dvd's, maybe I have the same here to ck.

---

### Post by mgmiller on 2009-12-25
I think the answer here is totem-xine.  Totem-gstreamer has the bug.  As you have noted, xine is a dead issue, so I didn't even try to get it working.

---

### Post by mc4man on 2009-12-25
> I think the answer here is totem-xine. Totem-gstreamer has the bug.

no, the player as shown above is totem (gstreamer), but at the end of the day [I]totem is not nearly as good a player for dvd's as vlc is.
[/I]
(totem-xine does work better than totem-gstreamer as far as language selection from dvd's, but both work.

On a test machine that has a straight up karmic install and current totem, again playback of a couple a dvds picked at random is fine. It's possible though that if the title has certain structure protections that possibly totem could have an issue.


Edit:
Now while I think totem is a crappy dvd player, considering some wish to use... A little further testing shows that while it can playback dvd's ok it does have playback issues with 1 structure protected disk I tried (a current ripguard variation) and definitely with some disks that aren't in pristine condition.

With disks with some minor scuffing, ect. that don't affect other players, totem will become choppy or freeze or lose audio for a period of time. Interesting that it seems to have a problem with the ecc that takes place in the drive while other players are unaffected.

---

