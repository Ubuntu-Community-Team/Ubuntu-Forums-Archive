---
title: "Question about Streaming Audio Files."
date: 2010-08-04
forum: New to Ubuntu
---

### Post by Kellemora on 2010-08-04
Hi Gang

I'm NOT talking about MUSIC or copyrighted material here.
Just my weekly lessons from a teacher, spoken lessen.

The teacher puts an audio copy of each weeks lesson on-line so we can listen to it again.  He uses Real Audio to do this and places two files, one done in an older Real Audio 2.0 and another done in Real Audio 5.0 since so many can't run the Real Audio 5.0 and hear anything.

When you click on the link to each weeks lesson, you get an option to OPEN it or SAVE it.  I've tried Saving it, and it only saves a LINK back to his web site, not the actual audio file.

He's made some very interesting lessons I would like to keep for later.

The problem is, he never keeps more than 6 lessons up, he deletes the oldest before putting up the newest one.

Is there a way to COPY streaming audio?

I don't know what questions to ask, so help me out here!

In the past I've simply used a Cassette Recorder and turned it on and taped the messages I wanted to keep using the Line Out port.

Digital Audio in a computer seems to have timers on them, like 1 minute or 3 minutes and then it shuts down (going back a few years here).....

Before he started placing the lessons on-line, we could get Cassettes from him, but he no longer uses that technology.

While I'm at it, is there an Audio Recorder for Ubuntu that I could make voice recordings with that don't time out in a couple of minutes?

EDITED to ADD:  I too cannot play Real Audio 5.0 files, only the 2.0 files!
Does that take a special player?????

TTUL
Gary

---

### Post by cj13579 on 2010-08-04
I don't know if it is the same sort of thing that you are after but there is this HOWTO:

[http://ubuntuforums.org/showthread.php?t=76658](http://ubuntuforums.org/showthread.php?t=76658)

---

### Post by marshmallow1304 on 2010-08-04
VLC can save streams to a file.

Media->Streaming
Go to the Network tab and put in the URL.
Click Stream.
Make sure your source is right, then click Next.
Make a new File destination by choosing File and clicking Add.
Put in your filename and path.
If you want to listen while recording, check "Display locally".
If you want it in a different format, check "Activate Transcoding" and select an appropriate audio Profile.
Click Stream and off you go.


It'd probably be good to check to make sure the stream plays regularly first.

---

### Post by andrew.46 on 2010-08-04
Hi Kellemora,

Can you give the address of one of these streams? If you can it should be a little easier to demonstrate how to save the stream offline.

Andrew

---

### Post by Kellemora on 2010-08-04
Thanks CJ and Marshmallow!

I was playing with it and found some instructions.

The problem with VLC is that it was written for some type of unknown monitor that is like 8 feet tall or something.
You cannot resize their selection boxes, nor do they have scroll bars, ergo you cannot get to the necessary buttons at the bottom to do anything.
It may be a good program, but IF you can't get to the buttons, it's as useless as you know what.  And if the programmers writing it don't realize this, well, what can I say?  Guess they used to work for Apple!

In any case, the teach told me all the lessons for each month are in a zipped folder that can be downloaded.  He just had to give me the name of the hidden folder to find it.  So I'm home free now, the easy way out.

TTUL
Gary

---

### Post by Kellemora on 2010-08-04
Hi CJ

I just thought of something.

I have 5 computers sitting here in front of me.

Wouldn't it be a whole lot easier just to take the Line-Out from the computer playing the stream and recording the audio via Line-In on another computer.

To do that I just need an audio recorder that doesn't have a 1 or 3 minute timer on it.  Will VLC record or do I need some other audio program?????

TTUL
Gary

---

### Post by Zimmer on 2010-08-04
OK, a bit of shed engineering might work so..

If you want an audio program, see Audacity.(simple to use) .. or Ardour (a bit more DAW) ..

And maybe (just maybe) you could direct the stream directly to it (maybe via JACK) on the SAME computer.

Also, have you done any searching for applications that might import the stream files and export them in a more convenient format such as ogg, mp3, wav etc ?

ok, I found you a promising link...
[http://labnol.blogspot.com/2007/01/how-to-record-save-bbc-radio-shows-as.html](http://labnol.blogspot.com/2007/01/how-to-record-save-bbc-radio-shows-as.html)

---

### Post by Kellemora on 2010-08-04
Thanks Zimmer

My OLDE Brain gets stuck a lot of times.

I loaded Audacity last year so I could READ my own talks and listen to them to see how dorky I sounded, hi hi.....
Helped me polish them up quite a bit too!

Thanks for reminding me!

TTUL
Gary

---

### Post by cj13579 on 2010-08-05
> **Kellemora said:**
> Hi CJ

I just thought of something.

I have 5 computers sitting here in front of me.

Wouldn't it be a whole lot easier just to take the Line-Out from the computer playing the stream and recording the audio via Line-In on another computer.

To do that I just need an audio recorder that doesn't have a 1 or 3 minute timer on it.  Will VLC record or do I need some other audio program?????

TTUL
Gary

I believe that the Audio Recorder that is shipped with Ubuntu is sufficent.

---

### Post by marshmallow1304 on 2010-08-05
If you hold Alt, you can click and drag anywhere in a non-maximized window to move it.  That might make VLC's interface easier to manage.

---

### Post by Kellemora on 2010-08-05
Thanks again Marshmallow

I jotted that down so I don't forget to try it.

On some programs, someone said grab the top edge and shrink it down.
That worked on a few pop-ups, but the rest of them just turn BLUE and won't let you resize them.  Like on GIMP.

I was looking at VLC again and today it's not doing that.  I have rebooted also messing with 10.04 so maybe that fixed whatever was causing it.

Thanks

TTUL
Gary

---

