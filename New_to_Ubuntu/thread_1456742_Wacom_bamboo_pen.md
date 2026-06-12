---
title: "Wacom bamboo pen"
date: 2010-04-17
forum: New to Ubuntu
---

### Post by Hal1ow3en on 2010-04-17
I just installed ubuntu today and everything seems to work ok from the get go except from my bamboo tablet. Having looked at the forums it seems very confusing to me which if any guide I should follow to get it up and running.

If someone could direct me to one, or offer any advice that would be awesome :cool:
I'm not up to speed on the terminal yet but had a go and failed already :( HALP! :lolflag:

---

### Post by Favux on 2010-04-17
Hi Hal1ow3en,

Which release of Ubuntu are you using?  Karmic?   Is the model number CTL460?

---

### Post by Hal1ow3en on 2010-04-17
I'm using karmic and thats the tablet model

---

### Post by Favux on 2010-04-17
OK, as you've realized the default version of linuxwacom that comes with Karmic, 0.8.4-1, doesn't work for your Bamboo because it is so new.  So what you want to do is install the latest production version, which is now 0.8.6.  You could follow the [linuxwacom HOW TO]("http://ubuntuforums.org/showpost.php?p=6546012&postcount=1").  It may look a little daunting but the steps you follow in Section 1 actually aren't that many.  There's just a lot of explanations interwoven.  You can copy and paste the lines you plan to use in a text file, in order, before you copy and paste them into the terminal.  [Ayuthia's HOW TO]("http://ubuntuforums.org/showpost.php?p=8283168&postcount=1") is sort of like that and you might find it easier to follow.  Just change the version to 0.8.6.

---

### Post by Hal1ow3en on 2010-04-17
Thanks a lot for the help, I'll read through those tomorrow and hopefully have some joy.

---

### Post by Hal1ow3en on 2010-04-18
Well so far today I've worked my way through section one of the tutorial (linuxwacom HOW TO) and other than a few minor misunderstandings I think it went quite well, my only questions for now would be what have I done in section one and what will I be doing in the following two.

The guide is easy to follow but well a lot of it is over my head in terms of understanding, I notice when I plug my tablet in the pointer tracks with it so would guess the next sections get pressure and other pen features working? 

Thanks again to Favux for the help and work put into the HOW TO =D>

---

### Post by Favux on 2010-04-18
Hi Hal1ow3en,

Good!  No obvious error messages?  After you go through the HOW TO a couple of times it'll make more sense.

Section 2 b) tells you how to install the wacom .fdi.  Either the new-generic attached below or also see [post #384]("http://ubuntuforums.org/showpost.php?p=8165182&postcount=384") for the new-working .fdi and other info. on your tablet.

Once one of the .fdi's is installed you can use wacomcpl and Section 3 tells you how to set that up.

For pressure in Gimp etc. see near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

---

### Post by Hal1ow3en on 2010-04-18
Just finished going through section two and used the new working fdi, and its all gone fine other than a few misunderstandings again that were overcome after re reading a few times.

wacomcpl works fine so now all I need to do is the calibrations and make sure they store then I should be good to go, hopefully I'll get the time tomorrow then can start to explore other aspects of ubuntu rather than just the terminal :)

---

### Post by Favux on 2010-04-18
Outstanding!

Have fun!

---

### Post by Hal1ow3en on 2010-04-22
All up and running now, also installed Gimp Paint Studio and everything works brilliantly. It all looked a bit scary at first, but having played with the terminal a little more for other things it all becomes clearer. 

To anyone else starting out I'd suggest not trying to do everything at once and read up on other things like themes and program installation too, once you've done some of those things the terminal is less frighting.

---

### Post by Hal1ow3en on 2010-05-30
For some reason today my pc decided it would no longer recognise my tablet, I checked the input devices and it's not longer there.

Would the best thing to do be to go through the tutorial from the start, (I'd assume it would tell me most things are installed). 

or is there a way to easily solve this, (still not brilliant with the terminal) :confused:

---

### Post by Favux on 2010-05-30
Hi Hal1ow3en,

It sounds like you had a kernel update.  The new kernel has a new modules directory.  Remember you used the copy (cp) command to copy the compiled wacom.ko into the old kernel's modules directory.  So just like you did then you can try to copy the compiled wacom.ko into the new kernel's modules directory.  If that doesn't work then you'll have to recompile.

---

### Post by Hal1ow3en on 2010-06-16
Thanks again Favux, sorry for the late reply, still haven't had time to get the tablet working but I read through the tutorial again and I understand what I need to do.

---

