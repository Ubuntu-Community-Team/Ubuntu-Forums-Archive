---
title: "Guide to sound layers"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by Jonas thomas on 2009-01-19
Hello,  My audio was basically working fine until I installed Hardy 8.04.  My understanding is that most of these issues are straightened out with Intrepid, but I'm reticent to update to that, because I had huge issues just getting my video configured. What I have at the moment works for me and I'm not in the mood to move from a LTS version.

My little one has been to playing Linux games with me, so It would be kind of nice to get the sound working.

I've seen the massive amounts of threads going on Pulse Audio and the  I've followed haven't worked for me.

So..In order to preserve my sanity as well as my generally positive attitude towards Linux/Ubuntu, I've decided to try a different tact. I'm choosing to look at this as a learning challenge.  I would like to understand how sound works from the chip level up to pulse-audio-> Alsa-> SDl  etc....

Are there any guides that someone recommend and point me to, that I can work/test through the various layers to understand and hopefully fix what's wrong with my system? I suppose if I google enough I'll run across something sooner or later..  I just thought someone here may know of "the" link[s] to check out first.

JT

---

### Post by ussndmac on 2009-01-19
Hi,

I've been digging into sound over the last few weeks.

After lots of messing around with forum threads I've found some references.

This link has some pretty good info and a graphic which shows it pretty well:

[http://www.jackaudio.org/documentation](http://www.jackaudio.org/documentation)

The presentation there is good, though some of it is specific to those who want to actually write clients for Jack.

There are also a couple of threads in the forum that are particularly info rich, this is good start:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Regards,
Mac

---

### Post by Jonas thomas on 2009-01-19
> **ussndmac said:**
> Hi,

I've been digging into sound over the last few weeks.

After lots of messing around with forum threads I've found some references.

This link has some pretty good info and a graphic which shows it pretty well:

[http://www.jackaudio.org/documentation](http://www.jackaudio.org/documentation)

The presentation there is good, though some of it is specific to those who want to actually write clients for Jack.

There are also a couple of threads in the forum that are particularly info rich, this is good start:

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

Regards,
Mac
Which section where you referring to the graphic?

Thanks for the links... I going to try working the forum link you gave and see if I get anywhere. I did some googling on search terms "Linux Sound Layers" and ran across some interesting stuff.
This I thought was worth noting:[http://blogs.adobe.com/penguin.swf/linuxaudio.png]("http://blogs.adobe.com/penguin.swf/linuxaudio.png")

I anyone has something better to explain how this stuff is interconnected please post.

I was reading through some of the blog posts from those search terms and it what struck me was the level of rudeness on some of these blogs.. What's up with that?

I wondering if a good strategy is to start with the layers closest to the sound chip and work my way up to SDL?


JT

---

### Post by ussndmac on 2009-01-19
Hmm...the link at penguin appears to me to someone trying to be complicated.

In fact, the details of how it's hooked up internally, are not as important in day to day use, as how the data flows.

For example, take a sound source, say a mic plugged into the mic in on a sound card.

- the sound is picked up by the mic
- the sound is digitized by the sound board
- the digitized sound is presented to alsa
- alsa presents it to whatever processes have stated they want input from the mic.
- if jack knows about the alsa sound source, then jack shows it as a source of sound.
- if one or more apps has told jack that they want input from this source then jack routes it to them.

Those same apps that have told jack they want input from the mic, in theory, could have told alsa instead.

But alsa and pulse are not necessarily designed for multi-path routing, jack is specifically designed for it.

Now this whole thing gets more complicated when you add a signal processing app that has a to and from, between jack and the final recipient.

---

### Post by Jonas thomas on 2009-02-06
I still haven't gotten my darn sound to work. (Life has been getting in the way)...
But... I did run an interesting wiring diagram of how this stuff is supposed to work... In theory anyway ;)
[IMG]http://upload.wikimedia.org/wikipedia/commons/1/14/Pulseaudio-diagram.png[/IMG]

---

