---
title: "mencoder file size/time"
date: 2010-10-11
forum: New to Ubuntu
---

### Post by anewguy on 2010-10-11
I used mencoder to capture a video stream - worked great, have a valid AVI file that works great.  There is just one problem:  I recorded this from a VCR tape, and set mencoder's stop time at 1 hour 25 minutes, when indeed it stopped.  The file is under a gigabyte.  Yet when I try to record it to DVD, it says the file is larger than a DL DVD, and over 2 hours 25 minutes long!

Why this mismatch?  Is there a way to get around this so I can record the file (I want to do this with all my old VCR tapes) and still be able to make a DVD of it without going through compression (it seems to ruin the video)?

Any input is greatly appreciated!

Dave ;)

---

### Post by anewguy on 2010-10-13
A shameless bump......

---

### Post by anewguy on 2010-10-13
Can anyone help me with this, or recommend a forum to post this on to get the help?

Thanks
Dave ;)

---

### Post by anewguy on 2010-10-15
One last bump.

If an admin sees this, can they perhaps move the thread to another forum if they think I might get help there?

Thanks
Dave

---

### Post by anewguy on 2010-10-28
I'll try another bump.

I don't understand how a file less than 1 gig on my hard disk becomes a file way over the size of a DVD when trying to create a DVD from it.

At this point, *ANY* help or ideas would be greatly appreciated!

The capture worked better in Ubuntu because it wasn't be default also playing back the video (Windows did this, and the result was a very choppy video - probably a result of my hardware not being up to snuff).

So what I want to do is convert the file captured by mencoder as an AVI file to a DVD that plays in a regular DVD player.  I'm trying to convert my old VCR tapes to DVD - any suggestions would be appreciated!

Just so you know, I bought the cheapest USB capture device I could find off EBay.  It does work for the capture, though.

Thanks in advance!
Dave ;)

---

### Post by anewguy on 2010-10-30
Okay, I'm not beyond begging......

PLEASE OH PLEASE OH PLEASE CAN SOMEONE HELP ME (at least on this problem - I know I'm beyond help myself).  ;) ;) ;)

Dave ;)

---

### Post by llamabr on 2010-10-30
What app are you using to burn the disk?  Have you tried cdrecord from the cli?

Also, how are you verifying that the file is only 1 gig?

---

### Post by anewguy on 2010-10-30
The file is stored on a NTSF partition.  Both Ubuntu and Windows show the size as:


C:\daves_junk>cd video capture stuff

C:\daves_junk\video capture stuff>dir
 Volume in drive C has no label.
 Volume Serial Number is BCCC-23B1

 Directory of C:\daves_junk\video capture stuff

10/06/2010  03:25 PM    <DIR>          .
10/06/2010  03:25 PM    <DIR>          ..
10/06/2010  04:31 AM       852,397,066 amazon_women_on_the_moon.avi
               1 File(s)    852,397,066 bytes
               2 Dir(s)  34,732,593,152 bytes free

C:\daves_junk\video capture stuff>


I have tried several different burners in Ubuntu and Windows.  i've sticking to Brassero when I can in Ubuntu because quite simply I've never had any problems with it.  Everything I've tried, be it Ubuntu or Windows, says the resulting file, after conversion to a DVD, is too big for a 4.7gig so I put in a dual-layer.  Some programs claim it is STILL too big, while others, like Brassero, try to start the conversion but run into some sort of restriction.  For Brassero in particular, it says I have too little disk free space.  Now I know I only allocated about 20 gig or so to Ubuntu, but I would have *thought* that should be enough for conversion.

Dave ;)

---

### Post by anewguy on 2010-11-01
Okay, let's try this again.

Does anyone know how much disk space Brassero requires to convert an AVI file to DVD?  I've already posted the file size, plus for some reason everything, be it in Ubuntu or in Windows, thinks this video is way way way over 2 hours, when I only recorded for about 1 hour 12 minutes (can't remember the exact elapsed time that I told mencoder to stop at, and I'm in Windows right now).

Perhaps someone can tell me why everything thinks the elasped time of this AVI is way beyond double of what it really is, and why the converted file (from AVI to DVD) is over the size of a DL DVD?

(Shameless begging..........)

Thanks in advance
Dave ;)

---

### Post by NightwishFan on 2010-11-01
Try the program Devede to convert a video file to a DVD iso.

---

### Post by anewguy on 2010-11-01
Thanks for the reply!  Already tried it amongst the Ubuntu attempts - it claims the video is over twice as long in time as it is, and says I don't have enough free disk space to convert it, and says the output file will be larger than a DL DVD.

Dave ;)

---

### Post by NightwishFan on 2010-11-01
I know most programs store their local data in /tmp. Why not use ffmpeg to copy the data straight from thw source to dvd format (I will use NTSC-DVD as an example) like so:
ffmpeg -i **source** -target ntsc-dvd **output.vob**

Then use Devede to make an iso. I think there is a checkbox to have devede not convert an already made .vob file, and just add it to a dvd tree and turn into an iso.

---

### Post by anewguy on 2010-11-01
> **NightwishFan said:**
> I know most programs store their local data in /tmp. Why not use ffmpeg to copy the data straight from thw source to dvd format (I will use NTSC-DVD as an example) like so:
ffmpeg -i **source** -target ntsc-dvd **output.vob**

Then use Devede to make an iso. I think there is a checkbox to have devede not convert an already made .vob file, and just add it to a dvd tree and turn into an iso.

Uuuuuuuuuuuu - Isengard - I better be careful!! ;) ;)  You avatar bares an uncanny resemblence to - no wait....

Thanks for the reply - I'll give that a try later tonight.  I'm going to back things up and install 10.10 and give it more disk space so if needed it will be available.

Can the source to ffmpeg be an AVI file and it will directly convert it without using addition "work" space on disk?  If so, that could be my solution!  Also - does this do a good job of keeping sync between video and audio?  I can't remember what it was I was doing a few years ago, but I do remember that devede and at least one more of the tools didn't keep sync then, and the longer the video, the more out of sync it got.

Thanks again!

Dave ;)

---

### Post by NightwishFan on 2010-11-01
Devede uses mencoder, which if it keeps sync depends on the input file. A malformed input file will always go out of sync. I find ffmpeg to be more reliable sometimes so that is why I recommended it. No it will convert and leave both the old and the new files.

---

### Post by anewguy on 2010-11-01
> **NightwishFan said:**
> Devede uses mencoder, which if it keeps sync depends on the input file. A malformed input file will always go out of sync. I find ffmpeg to be more reliable sometimes so that is why I recommended it. No it will convert and leave both the old and the new files.

Thanks so much for your help!  I just finished a nightmare - I resized my Windows partition to make more room for Linux, then removed the old Linux partitions and installed 10.10.  The install of 10.10 went beautifully - no problems there!  I *may* have made some sort of mistake on my Windows partition - I defrag'd it a couple of times before the shrink, but upon boot it kept running chkdsk for 5 or 6 reboots until it finally got past the errors it thought were on the disk.  First time I've ever had it run chkdsk after a shrink and find errors.  I'm waiting to see if something comes back to bite me in Windows now.  But...at least the 10.10 install went GREAT, and I now have the extra disk space, so I'll be booting to ubuntu in a few minutes and trying your suggestion.  Wanted to get on with Windows, do some mail, etc., to see if it would at least be stable now.

Thanks again!  BTW - I really did like the sig and avatar!

Dave ;)

---

### Post by NightwishFan on 2010-11-02
Thanks! Have fun. :)

---

### Post by anewguy on 2010-11-02
Yippieeeeeeeee!  Thanks so much - that worked great and the size is now down to a reasonable 2.5 gig like it should be.  Burned a DVD from the ISO and it works great!

Now the only thing I have to do is learn what all the video and sound options are and what the heck they all mean (I know *squat* about any of that) for mencoder so I can try to make the sound better.  There's a lot of background hiss (kind of like turning something up because the sound is too low only hear the background hiss) and some occasional pops.  Hopefully I can figure that out somehow, and (knocks on wood quite hard ;) ) that it's not a result of my cheapo USB capture device ;)

Anyway, thanks again!  Problem solved!!

Dave ;)

---

### Post by NightwishFan on 2010-11-02
The manpage for mplayer/mencoder is huge but it is comprehensive:
```
man mencoder
```

---

