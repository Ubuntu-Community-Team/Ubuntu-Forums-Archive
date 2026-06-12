---
title: "Different driver for Intel Corporation 82801G"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by k33bz on 2009-09-15
When I first bought my laptop it was running vista, I had loaded Hardy to it (now running jaunty). The problem is when windoze was on it the sound was really loud. Now it is about half the volume (it was quieter with Hardy). So my question is, is there a different driver that I can install to get the sound back to what it was when windoze was on it?

And yes I have the volume all the way up in alsamixer.


Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller

---

### Post by k33bz on 2009-09-15
<bump>

---

### Post by Geoff918 on 2009-09-15
I think you're probably in the wrong forum. I can give you some ideas, but given your age and experience with Ubuntu you've probably already tried them.

Perhaps try a non-Beginner thread?

I mean, you could always try a reconfigure on the card. You could make sure there aren't different settings on your main control in GNOME. You could make sure that your individual applications aren't throttling your volume control. There are about 5 different places at least where volume controls come into play. Also, you could check your physical connection and make sure nothing has come loose causing signal loss. (Is it still working loudly on your Windows boot?) Maybe your speakers have aged and aren't capable of outputting the same volume? I have had that happen to me when I was a teenager blasting my stereo--eventually the speakers wouldn't go as loudly or as clearly. Probably a driver kicked one-too many times. :)

---

### Post by k33bz on 2009-09-15
> **Geoff918 said:**
> I think you're probably in the wrong forum. I can give you some ideas, but given your age and experience with Ubuntu you've probably already tried them.

Perhaps try a non-Beginner thread?

I mean, you could always try a reconfigure on the card. You could make sure there aren't different settings on your main control in GNOME. You could make sure that your individual applications aren't throttling your volume control. There are about 5 different places at least where volume controls come into play. Also, you could check your physical connection and make sure nothing has come loose causing signal loss. (Is it still working loudly on your Windows boot?) Maybe your speakers have aged and aren't capable of outputting the same volume? I have had that happen to me when I was a teenager blasting my stereo--eventually the speakers wouldn't go as loudly or as clearly. Probably a driver kicked one-too many times. :)

Considering this is my laptop and not my desktop, I have wiped out vista completely off of it. Alot of the stuff you have mentioned is well above my head. I dont know how to reconfigure my card. As far as I know no applications are throttling my sound. I will post this in a different thread.

Matter fact I dont know which one it would be in, nor do I like double posting, if a moderator can please move this thread to the right place it would be much appreciated.

Side note: As said it worked loud, very loud in vista. When I installed Hardy the sound was cut down to maybe a 1/4 at maxium. When upgraded to Jaunty the sound became louder, but still not as loud as it was with Vista.

---

### Post by Geoff918 on 2009-09-15
Please forgive me, I assumed too much. I will give you the following link, if this does not work I can walk you through deleting and re-establishing your sound card. I had done this a few times when I used to use openSUSE, perhaps not Ubuntu but I can get you through one way or another. There are some differences between the distros, but nothing too great.

Please see the link below:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

This may give you some starting points for where to begin configuring things. Granted, it starts with "no sound" and works up, but there's a lot there.

Some other possible links of use:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://ubuntuforums.org/showthread.php?t=235245](http://ubuntuforums.org/showthread.php?t=235245)

I hope this helps, and again I apologize for "going over your head". I meant nothing insulting by it, I just assumed you may be more experienced than perhaps you could get help with in a beginner forum. I post help here because I know I can help on most issues. The more advanced hardware forums and such I'm not knowledgeable or skilled enough to touch. So, I help where I can for the benefit of the community. I recognize that the Ubuntu community is what makes it the best distro and makes it palatable to those switching from Windows. It's my way of attempting to help out with Bug #1 (you know even with Mac being widespread and well known it only has about 7-8% market share?!?)

Sorry for the digression. I hope this all proves to be of help.

---

### Post by barnaclebill18 on 2009-09-15
I have the same problem.

I think it is the Intel drivers, you might check this out.



[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

---

### Post by k33bz on 2009-09-15
> **barnaclebill18 said:**
> I have the same problem.

I think it is the Intel drivers, you might check this out.



[http://ubuntuforums.org/showthread.php?t=1130582](http://ubuntuforums.org/showthread.php?t=1130582)

That would be for graphics, not sound. However I did use that thread to update my graphics driver, I used the safe configuration. Works real well.

> **Geoff918 said:**
> Please forgive me, I assumed too much. I will give you the following link, if this does not work I can walk you through deleting and re-establishing your sound card. I had done this a few times when I used to use openSUSE, perhaps not Ubuntu but I can get you through one way or another. There are some differences between the distros, but nothing too great.

Please see the link below:

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

This may give you some starting points for where to begin configuring things. Granted, it starts with "no sound" and works up, but there's a lot there.

Some other possible links of use:

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

[http://ubuntuforums.org/showthread.php?t=235245](http://ubuntuforums.org/showthread.php?t=235245)

I hope this helps, and again I apologize for "going over your head". I meant nothing insulting by it, I just assumed you may be more experienced than perhaps you could get help with in a beginner forum. I post help here because I know I can help on most issues. The more advanced hardware forums and such I'm not knowledgeable or skilled enough to touch. So, I help where I can for the benefit of the community. I recognize that the Ubuntu community is what makes it the best distro and makes it palatable to those switching from Windows. It's my way of attempting to help out with Bug #1 (you know even with Mac being widespread and well known it only has about 7-8% market share?!?)

Sorry for the digression. I hope this all proves to be of help.

I will be going over this tomorrow some time, and will let you know how it turns out.

---

### Post by barnaclebill18 on 2009-09-15
Even though I am a computer dummie, I knew that thead was for the graphics but I thought it might give some ideas.

---

### Post by k33bz on 2009-09-15
> **barnaclebill18 said:**
> Even though I am a computer dummie, I knew that thead was for the graphics but I thought it might give some ideas.

Didn't mean to offend you, it is where I got the idea to see if there was a work around for the sound card as well. :)

---

