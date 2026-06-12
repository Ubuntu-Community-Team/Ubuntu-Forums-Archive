---
title: "2 Strange problem related to CD"
date: 2010-03-01
forum: New to Ubuntu
---

### Post by d2btoo on 2010-03-01
Hello,

I'm facing these strange issues:

#1) If I click on "eject", then the CD-tray opens and closes immediately, i.e. it doesn't stay open, so that I can remove the disc. How do I solve that?

#2) I'm unable to play any VCD, it always shows "Permission Error".
btw I can play DVD etc.
-- also I can play .dat(vcd) files from HDD in vlc, but default player totem hangs.


I'm completely new with ubuntu(or linux), just installed it last sunday.
thanks for any clue...

Ubuntu 8.10

---

### Post by d2btoo on 2010-03-03
Okay, I installed Totem(xine) and now I can watch VCD's, however it still shows an error (see the screen-shot please), when I insert the CD, but I can watch it from the player menu. :D

As for the #1, I did some search and found it too, on the release note page of ubuntu 8.10, there seems to be some kind of fix, but I don't understand what I would need to do :???:

---

### Post by alexandari on 2010-03-03
about #1

what happens if you write ```
 sudo eject 
``` in the terminal?

---

### Post by d2btoo on 2010-03-03
Thanks for responding.... :)

Same thing....the tray opens and closes immediatly.

---

### Post by d2btoo on 2010-03-11
Hello,
just for record...

For #1, I found [[COLOR="Blue"]_this_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6031341&postcount=27"), seems it working atm.

thanks.

---

### Post by 3rdalbum on 2010-03-11
> **d2btoo said:**
> Hello,
just for record...

For #1, I found [[COLOR="Blue"]_this_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=6031341&postcount=27"), seems it working atm.

thanks.

...you didn't really need to go to that trouble, just apply the pending updates for 8.10.

By the way, 8.10 goes End Of Life next month; you really should be using a more recent version of Ubuntu. I would suggest trying 9.10 or 10.04 (which is in alpha right now).

---

### Post by d2btoo on 2010-03-12
> **3rdalbum said:**
> ...you didn't really need to go to that trouble, just apply the pending updates for 8.10.

By the way, 8.10 goes End Of Life next month; you really should be using a more recent version of Ubuntu. I would suggest trying 9.10 or 10.04 (which is in alpha right now).

Yes, exactly I'm waiting for the 10.04 too..... :mrgreen:

The problem with 8.10's updates are that they are now really huge, right now it's say 357 updates available, so I'm just dodging it atm,(see me on limited bandwidth. :cry:)

9.10 breaks my sounds and internet, also it seems heavy on my system, so I don't think it's the right version for me.

---

### Post by 3rdalbum on 2010-03-12
> **d2btoo said:**
> Yes, exactly I'm waiting for the 10.04 too..... :mrgreen:

You don't need to wait. Alpha 3 has been released, and there are 'daily builds'. I'm currently running Ubuntu 10.04 on my netbook, it's great. The added advantage with running a development version of Ubuntu is that if you report a bug, there's still time to get it fixed.

> The problem with 8.10's updates are that they are now really huge, right now it's say 357 updates available, so I'm just dodging it atm,(see me on limited bandwidth. :cry:)

I understand. But Update Manager lets you apply only a selection of updates, if you want. If you just apply the HAL and udev updates, which should be relatively small, I think this fixes the issue.

---

### Post by d2btoo on 2010-03-12
> **3rdalbum said:**
> ...... The added advantage with running a development version of Ubuntu is that if you report a bug, there's still time to get it fixed.

although I never run alpha softwares, but that's not a bad point....let me see, maybe I can test it in VBox.


> **3rdalbum said:**
> 
I understand. But Update Manager lets you apply only a selection of updates, if you want. If you just apply the HAL and udev updates, which should be relatively small, I think this fixes the issue.

hmm! but how should I just update HAL and udev?.... meaning what should I pick from the list...(I've never done any update in linux, so I guess I'm little confused here.)

thanks...

---

