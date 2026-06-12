---
title: "can't play video in ubuntu 9.10"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by Suranjandeo on 2010-08-15
Brothers and sisters,
Regards.

I have Ubuntu 9.10 Just now i have updated it.

I can play audio which is on HDD and also if i put audio mp3 CD in DVD
drive then i can play it with movie player.

But when i put any video CD in the drive and try to play it with
movieplayer then error message comes-----

"An error occurred
No URL handler implemented for VCD."

I went in the properties of the file and it was written there==-

"Name- avseq01.dat

Type- dat document (application/x-extension-dat)"

IT was not playing video before updating also. I thought when i will
download all updates then video will play. But still not playing. I
have movie player which comes with live CD of ubuntu 9.10

I don't know all coedecs are installed or not related with video. I
just downloaded all updates. If i have to download something else then
pls guide me.

waiting...
suranjan

---

### Post by diablo75 on 2010-08-15
First, add in the Medibuntu repositories to your software sources and the associated codecs.  While you're at it, install Ubuntu Restricted Extras.  Here, I put it all together into one long command for ya (actually, it's a series of commands that run in order):

Applications>Accessories>Terminal

Type in:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install ubuntu-restricted-extras libdvdcss2 w32codecs
```

If you're using a 64-bit operating system, replace the "w32codecs" on the end with "w64codecs".

More info about medibuntu available here:

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

Run Update Manager after all this for good measure ;)

---

### Post by Suranjandeo on 2010-08-15
> **diablo75 said:**
> First, add in the Medibuntu repositories to your software sources and the associated codecs.  While you're at it, install Ubuntu Restricted Extras.  Here, I put it all together into one long command for ya (actually, it's a series of commands that run in order):

Applications>Accessories>Terminal

Type in:

```
sudo wget --output-document=/etc/apt/sources.list.d/medibuntu.list http://www.medibuntu.org/sources.list.d/$(lsb_release -cs).list && sudo apt-get --quiet update && sudo apt-get --yes --quiet --allow-unauthenticated install medibuntu-keyring && sudo apt-get --quiet update && sudo apt-get install ubuntu-restricted-extras libdvdcss2 w32codecs
```

If you're using a 64-bit operating system, replace the "w32codecs" on the end with "w64codecs".

More info about medibuntu available here:

[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

Run Update Manager after all this for good measure ;)

Okay, I will run all commands you have suggested in terminal and will inform you. I am using 32 bit operating system. 

One question is that you have given one link  in your letter by telling that more info about medibuntu. But when i clicked on it. I reached in my this letter. Actually this is link for my letter. It seems to me...====
[http://ubuntuforums.org/forumdisplay.php?f=326](http://ubuntuforums.org/forumdisplay.php?f=326)

---

### Post by diablo75 on 2010-08-15
Crap, sorry about that.

I meant to paste this:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by Suranjandeo on 2010-08-15
Regards,
I ran in terminal all commands you suggested. It installed all w32coedecs nicely. then i tried playing CD but same message came what i have mentioned in my first letter. 
Then i restarted computer and then tried but same thing happened. When I play Video Cd then error message come- "URL handler is not implemented" and when i try to play DVD then no message come.

Problem persists.....
waiting for help

---

### Post by Suranjandeo on 2010-08-15
> **Suranjandeo said:**
> Regards,
I ran in terminal all commands you suggested. It installed all w32coedecs nicely. then i tried playing CD but same message came what i have mentioned in my first letter. 
Then i restarted computer and then tried but same thing happened. When I play Video Cd then error message come- "URL handler is not implemented" and when i try to play DVD then no message come.

Problem persists.....
waiting for help

Any help from anyone. Or should i think this problem is not curable ?
regards
suranjan

---

