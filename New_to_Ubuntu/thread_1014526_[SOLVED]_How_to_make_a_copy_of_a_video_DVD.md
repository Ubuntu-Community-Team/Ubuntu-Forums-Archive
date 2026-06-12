---
title: "[SOLVED] How to make a copy of a video DVD?"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by bhold on 2008-12-17
I thought this would be simple, wrong again...

My wife has a video recorded at a friend's party, on DVD-R. It plays just fine on Ubuntu Desktop 8.10 with Totem movie player (I think I installed xine instead of gstreamer in case it mattters, although I have no idea what the difference is.)

OK, she asked me to make a copy of the DVD, I said no problem. Used Brasero to create a .iso, then burned it to a new DVD. When I try to play the new DVD I get a message something like... "The media appears to be encrypted, have you installed libdvdcss?" Huh??? How did the copy become encrypted? Or is this a bogus message?

Any EASY way past this? My knowledge of video HW, SW, and configuration is limited and I have observed that some of thesee video threads become quite technical. I'm willing to experiment and learn, but currently time is limited also. (I have created a number of "coasters" now, this trial and error mode could get costly.)

Thanks   -- Bob

---

### Post by mikewhatever on 2008-12-17
Try installing the suggested package and see what happens.
[https://help.ubuntu.com/community/Medibuntu#With%20individual%20packages](https://help.ubuntu.com/community/Medibuntu#With%20individual%20packages)

---

### Post by cariboo on 2008-12-17
Give k9copy a try, it is available in the repositories. You can use Add/Remove Programs, Synaptic Package Manager and of course the command line to install it.

Jim

---

### Post by Kellemora on 2008-12-18
Hi Bob

This may be a dumb response and I might be wrong too.

Did I read that you tried to burn a Video as an .iso?????

Doesn't .iso mean it's a bootable PROGRAM file?

I've copied tons of video's in the past just using duplicate original on a Backpack DVD burner.  I never knew about burning .iso's until I wanted to install Linux and needed to learn how.

It's an entirely different setting, available only on some of my DVD drive writing software.

That could be why you can't play it?
It thinks it's a computer program that needs to boot-up?

TTUL
Gary

---

### Post by bhold on 2008-12-18
Thank you all for your replies.

Here is what I did and it worked.

1. Installed the packages suggested by mikewhatever.
2. Tried again using brasero to burn a new dvd from the .iso, same problem, created another coaster.
3. Installed gnomebaker software.
4. Created a .iso file from the original dvd using gnomebaker.
5. Burned a new dvd from the .iso file using gnomebaker. This new dvd works just fine.

Brasero bug 444497 looks like a possible suspect, but I am out of time so will close this thread as solved.

---

### Post by SuperSonic4 on 2008-12-18
> **Kellemora said:**
> Hi Bob

This may be a dumb response and I might be wrong too.

Did I read that you tried to burn a Video as an .iso?????

Doesn't .iso mean it's a bootable PROGRAM file?

I've copied tons of video's in the past just using duplicate original on a Backpack DVD burner.  I never knew about burning .iso's until I wanted to install Linux and needed to learn how.

It's an entirely different setting, available only on some of my DVD drive writing software.

That could be why you can't play it?
It thinks it's a computer program that needs to boot-up?

TTUL
Gary

An ISO file is a disc image, it can be of anything from a bootable live cd to a collection of files. They're used when it is impractical to host a large number of single files for download and are easily burnt to a cd/dvd.

Also +1 for k9copy even if it is too late xD

---

