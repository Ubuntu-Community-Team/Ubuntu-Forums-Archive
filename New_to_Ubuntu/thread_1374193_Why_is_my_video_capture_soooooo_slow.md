---
title: "Why is my video capture soooooo slow?"
date: 2010-01-06
forum: New to Ubuntu
---

### Post by Stovey on 2010-01-06
Would somebody please help me configure Ubuntu to work with my Webcam?

Video capture is very very slow, about 1 frame per 5 seconds.  Or something.

Here's what it looks like:

[http://www.youtube.com/watch?v=0cV4IOPz4Qc](http://www.youtube.com/watch?v=0cV4IOPz4Qc)

This is on an Acer Aspire One with Ubuntu 9.10.  Thanks!

---

### Post by Muttley99 on 2010-01-06
Your not giving us much to go by! what program are you using? did you try Kdenlive or handbrake?

---

### Post by Stovey on 2010-01-06
Oh, it's a USB webcam so I'm using Cheese.

---

### Post by Muttley99 on 2010-01-06
640x480?

try 320x240

also try camorama. try kdenlive. If your getting the same slow performance, try removing and re-installing video4linux.

---

### Post by Stovey on 2010-01-06
Cheese works OK at 320 x 240 but not at 640 x 480.  But c'mon, 320x240 is totally unacceptable!

I know my machine does better, have a look at this video I filmed of a bum with Windows Moviemaker on the same machine:

[http://www.youtube.com/watch?v=Edj8GVqyxJc](http://www.youtube.com/watch?v=Edj8GVqyxJc)
[LEFT]
[/LEFT]
Camorama won't install on my machine.  It isn't in the "repository" and when I tried to install from the website I got an error.

Kdenlive captures video from an external cam (Logitech pro 9000).  And it seems to capture video at a better rate, even though it's about 2 seconds behind.  And then the program freezes and crashes.

In addition to crashing, Kdenlive does not work with my built in "Crystal Eyecam".  I get this error: cannot read from device /dev/video0 Please check drivers and access rights.

---

### Post by Muttley99 on 2010-01-07
To address your issue with Kdenlive, try;

[HTML]sudo chmod 777 /dev/video0[/HTML]

If it works, change permissions to something like 660.

;) I wasn't suggesting you lived with 320! Just wanted to know if it was due to read/write speed. What fps have you set? I think the default is 15 for 640x480.

This link may have the answer for cheese = [http://ubuntuforums.org/showthread.php?t=802000](http://ubuntuforums.org/showthread.php?t=802000)

---

### Post by Stovey on 2010-01-07
> **Muttley99 said:**
> ...;) I wasn't suggesting you lived with 320! Just wanted to know if it was due to read/write speed...

Ha.  Whew!  :)  So since it works at 320 but not 640 it means read/write speed is the issue?

Ok, bear with me, I'm on my way to work but will have a chance to go through these posts / changes later in the day.

Muttley, many thanks for your assistance and patience.  I really need to get this camera working.

---

### Post by Muttley99 on 2010-01-07
Stovey, Have a look at the link I posted. TBH, Ubuntu and webcams don't play nice together right now! Some webcams do not work at all and others with limited functionality.

---

### Post by Stovey on 2010-01-07
OK, so webcams are a problem.  Fair enough.

Kdenlive recognizes my camera now, but I just don't have the settings right I guess.  It keeps crashing.  Plus it seems pretty complex and not easy to set-up.

But guvcview (as recommended in your link) seemed to work OK - probably good enough I guess.  I'll maybe fool with that one a bit more.

Thanks!

---

### Post by Stovey on 2010-01-07
> **Stovey said:**
> ...But guvcview (as recommended in your link) seemed to work OK - probably good enough I guess...

I take that back, the audio is not synced with the video.  And I tried Camorama and it didn't recognize my device.

I've spent hours on this, it's getting kind of frustrating.

---

### Post by Muttley99 on 2010-01-08
Kdenlive uses dvgrab to capture video! This means using dvgrab from the command line;
Install mplayer

[HTML]sudo apt-get install mplayer[/HTML]

try;

[HTML]dvgrab --format qt foo; mplayer foo0001.mov[/HTML]

I have two webcams and neither will work with Karmic! :( BUT, you have the advantage of a working driver!

---

### Post by Stovey on 2010-01-08
Hey man, I'm sorry your webcams don't work.  I know how you feel.

I did some looking into this and it seems there are two issues with Ubuntu 9.10!  First there is something maybe wrong with Pulse Audio.  And second there is something wrong with SDL.  I tried to fix the SDL first, but I am a complete newbie to Linux.  So I can't even add the PPA!  And I'm not sure I want to fool with Pulse Audio since everything else works for sound.  In other words I think I'm screwed.

[http://www.kdenlive.org/forum/help-ubuntu-910-fresh-install-ffplay-and-melt-crash](http://www.kdenlive.org/forum/help-ubuntu-910-fresh-install-ffplay-and-melt-crash)

This explains why Kdenlive was crashing.  I don't know if it explains why my webcam is terribly slow.

---

### Post by Muttley99 on 2010-01-09
Its easy to add! just follow this guide;

[http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages](http://kdenlive.org/user-manual/downloading-and-installing-kdenlive/pre-compiled-packages/ubuntu-packages) 

Kdenlive is excellent. Unfortunately, for some, it crashes.

Your webcam issue: If you have a working driver, you have a very good chance of getting it to work.

---

