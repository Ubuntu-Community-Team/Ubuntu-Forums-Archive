---
title: "What is a good application to record sound on Firefox (Ubuntu - Hardy)"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by mal_conductor on 2009-02-16
What is a good application to record sound on Firefox (Ubuntu - Hardy)

---

### Post by Don1500 on 2009-02-16
> **mal_conductor said:**
> What is a good application to record sound on Firefox (Ubuntu - Hardy)

You'll hear about a few, Audacity and others, but NONE OF THEM WORK! If you can find one let me know. :frown:

---

### Post by click4851 on 2009-02-16
I've had good luck with audacity....:)

---

### Post by mal_conductor on 2009-02-16
> **mal_conductor said:**
> What is a good application to record sound on Firefox (Ubuntu - Hardy)

No luck with this.  The show I wanted to record has started.  Maybe I will look into this later.

---

### Post by sandyd on 2009-02-16
try
```

gnome-sound-recorder

```
its included in gnome :)

---

### Post by Bright_View on 2009-02-16
Don1500 must be having some specific issues, because I have used Audacity many times for recording all sorts of stuff.  It is intuitive and easy to use, which is why I like it.  You install it from the repositories.  If you want something that is top-notch then you can try out Ardour.

Don1500, what have you been trying to do that you're unable to?

---

### Post by punx45 on 2009-02-17
audacity is definitely useful in this situation as it lets you capture the internal sound stream, or whatever the proper name is for it.   i used it to grab some songs off of myspace once, heh.  im disappointed i cant grab that as a source on OSX though, but thats another story.

---

### Post by Don1500 on 2009-02-22
> **Bright_View said:**
> 

Don1500, what have you been trying to do that you're unable to?

I have been trying to record any sound off the net. I get nothing with any recorder. I can use just about anything in windows and I get good results. In Ubuntu I get nada. I have tried just about every set up I can. I can hear sounds in every application so I know the sound is getting into the computer correctly, but nothing records. And I can load a file into Audacity and it plays fine, have all the control I want, but no record.

I do believe I found the problem, but I don't know how to fix it. In the Volume control gui I set all the capture switches "ON" but only the Microphone shows in record. Maybe I have something set wrong in the sound preferences. This may go al the way back to the installation, I had many sound problems then.

I'm going to put this in a new thread.

---

### Post by Bright_View on 2009-02-23
I may be wrong, but I don't think it's necessary (or possible) to record sound off the internet with Audacity in the way you're hoping to.  With a suitable download manager, you should be able to download the sound files directly in their original format.  This would be much easier and faster.  I use the Firefox plugin FlashGot for this.  It allows you to download any media available on a webpage (pics, movies, songs, etc.) with a click of your mouse.  You can then open any sound files in Audacity to add tracks or edit it if you wish.  

If you give me an example of a sound file that you are trying to record, I can check to see if FlashGot will work for you before you go to the trouble of installing it.  Just let me know.

---

### Post by cjv8888 on 2009-02-23
try vsound sox and lame as in this [How To]("http://ubuntuforums.org/showthread.php?t=169278")

---

### Post by Kellemora on 2009-02-24
Hi BV

Can you try it with a RealPlayer2.0 file, that would be .ram

Every time I've tried it, I get only a link back to the website when I hit play.  If I unplug the LAN then I get ZIP, so even though it showed that the file downloaded and was saved to the disc, it won't play unless you are online.  So apparently only the link is what is saved in the file.

TTUL
Gary

---

### Post by neu2buntu on 2009-02-24
this can definately be done with audacity as long as it is rigged through jack the gui being "qjackctl" and jack is chosen in audacity preferences.  also another way of recording and playing anything is to rig pulseaudio through jack, it takes a bit of setting up > goto this link and look for pulseaudio and jack......[http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack](http://ubuntuforums.org/showthread.php?t=843012&highlight=markbuntu+pulseaudio+alsa+jack)

---

### Post by Don1500 on 2009-03-06
> **cjv8888 said:**
> try vsound sox and lame as in this [How To]("http://ubuntuforums.org/showthread.php?t=169278")

I have just read the "How To" on ripping audio streams off the net. Boy, that is not an elegant solution. In fact, compared to how easy it is done in windows I think I will keep doing it that way. But given the information on how to do it I may try to use this as a first try in programming a Linux app.  It looks like there may be a need for this, so I may try to fill that need.

---

### Post by mal_conductor on 2009-07-26
Many thanks to cjv8888 for providing a how to on vsound sox.

I agree with Don1500.
- I have not been able to make Audacity work.  I spent a lot of time fiddling with the set up and I am done with Audacity.  If it is possible, it is beyond my technical ability.

- Other solutions I have found don't work. At least for me.

- The how to on vsound sox is involved.  I will try it if absolutely necessary to record on my Ubuntu box.

- For now I will continue to capture sound on my Windows box with a free application called freecorder.  Simple, easy to install and works great.

Thanks for all the replies.  I await for something practical and afficient from the Linux community.

---

### Post by Liolikas on 2009-07-26
Freecoder has cnet community rating 1 start from 5. :D

---

### Post by oldos2er on 2009-07-26
Audacity works well here, running it under 9.04, kernel 2.28.30.x. Both Exaile and Vlc have a record function to save streams, if that's what you're looking for.

---

