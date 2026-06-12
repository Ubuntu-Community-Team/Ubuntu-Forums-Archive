---
title: "Ubuntu 9.1 + Skype problem"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by cozski on 2010-01-01
I realise this problem has consistently arisen but I have not yet found a resolution specific to my set up.

I have Skype (Beta) 2.1.0.47 installed on Ubuntu 9.1. When I use my mic/headset I can hear people on the other end no problem but they cannot hear me. I have tried a variety of configurations related to the sound from various posts/blogs where other people have experienced the same problem. 

Below are the screenshots for my current configuration for the Skype set-up, Ubuntu Sound Preferences and Pulse Audio Applet Volume Control.

[IMG]http://i48.tinypic.com/xf6c8i.png[/IMG]

[IMG]http://i48.tinypic.com/25gqous.png[/IMG]

[IMG]http://i49.tinypic.com/vfe72g.png[/IMG]

[IMG]http://i49.tinypic.com/33ml9tz.png[/IMG]

[IMG]http://i47.tinypic.com/rhu910.png[/IMG]

[IMG]http://i47.tinypic.com/f3dsgx.png[/IMG]

[IMG]http://i46.tinypic.com/29zpls0.png[/IMG]

[IMG]http://i50.tinypic.com/ncnv5k.png[/IMG]

... remaining 2 caps in next post...

---

### Post by cozski on 2010-01-01
[IMG]http://i50.tinypic.com/2zp5mrm.png[/IMG]

[IMG]http://i48.tinypic.com/2njkgt4.jpg[/IMG]


I've been struggling with this for over a week now and as a fee paying skype user it's compromising my capacity to stay with Ubuntu. Any help/advice/sign posting will be hugely appreciated. Going out on the piss tonight so I wont be responding to anything until tomorrow.

Thanks

---

### Post by lasleym on 2010-01-01
Have you tried alternate Skype versions through Medibuntu?  See a thread [here]("http://ubuntuforums.org/showthread.php?p=8307045#post8307045").

Can you specify what you've tried?

---

### Post by Methuselah on 2010-01-01
Do you know if any other sound recording works or is it just skype?
Also, what kind of microphone are you using?
Have you used it before and know it works?

The above aside, type **alsamixer** in a terminal, press enter and then and then hit the F4 key when the interface appears.
If you can, post an image of what is displayed.

Thanks.

---

### Post by fibercode on 2010-01-01
In your Sound Preferences -> Input, you only have the "Internal Audio Analog Stereo" option available. That means that you are only using the built in microphone of you computer.

If you have a mic on your headset it should show up in that list and you will have a radio button to select it.

Here is how my webcam with built in microphone shows up:

[IMG]http://i47.tinypic.com/351bs08.png[/IMG]


Also, as Methuselah suggested, run alsamixer.

ALSA by default has the mic levels muted. Increase the microphone input levels.

---

### Post by Zzl1xndd on 2010-01-01
You may also want to disable the "Allow Skype to Automatically adjust my Mixer levels". For me this kept turning down the the Mic volume and people couldn't hear me.

---

### Post by cozski on 2010-01-02
> **Methuselah said:**
> Do you know if any other sound recording works or is it just skype?
Also, what kind of microphone are you using?
Have you used it before and know it works?

The above aside, type **alsamixer** in a terminal, press enter and then and then hit the F4 key when the interface appears.
If you can, post an image of what is displayed.

Thanks.

Hey, below is the cap from alsamixer:

[IMG]http://i48.tinypic.com/2sb28aq.png[/IMG]

I had been using the mic/headset with my laptop and netbook on XP and no problems at all. The sound through my headset is fine too. It's juts the mic. I dont know what make it is but there's a pic below:

[IMG]http://i48.tinypic.com/wip7s.jpg[/IMG]

As a heads up, my webcam (Phillips 315NC) doesn't work with skype either but I thought I'd get the sound issue resolved first as the cam is less of a priority.

Thanks

---

### Post by cozski on 2010-01-02
> **fibercode said:**
> In your Sound Preferences -> Input, you only have the "Internal Audio Analog Stereo" option available. That means that you are only using the built in microphone of you computer.

If you have a mic on your headset it should show up in that list and you will have a radio button to select it.

Here is how my webcam with built in microphone shows up:

[IMG]http://i47.tinypic.com/351bs08.png[/IMG]


Also, as Methuselah suggested, run alsamixer.

ALSA by default has the mic levels muted. Increase the microphone input levels.


The mic/headset is not showing up in the list as you suggested... I also noticed from the alsamixer grab i posted there doesn't appear to be mic connected :confused:

Thanks for help everyone, appreciated!

---

### Post by cozski on 2010-01-02
> **tweakedenigma said:**
> You may also want to disable the "Allow Skype to Automatically adjust my Mixer levels". For me this kept turning down the the Mic volume and people couldn't hear me.


I also applied that setting but it has had no impact... but thanks for the advice!

---

### Post by cozski on 2010-01-02
> **lasleym said:**
> Have you tried alternate Skype versions through Medibuntu?  See a thread [here]("http://ubuntuforums.org/showthread.php?p=8307045#post8307045").

Can you specify what you've tried?

Hey, I haven't actually tried any of the other versions through Medibuntu but after reading the thread you sign-posted it's looking like it's definitely worth a try if no-one else comes up with a solution that negates the need for a new version installation. Cheers man!

---

### Post by polt on 2010-01-07
Have you tried switching to Microphone 2 under your Sound Preferences -> Input, Connector: ?  I was having the exact same problem and this fixed it.  So there should be hope for you! ;)

---

### Post by fibercode on 2010-01-08
> **cozski said:**
> Hey, below is the cap from alsamixer:

[IMG]http://i48.tinypic.com/2sb28aq.png[/IMG]

I had been using the mic/headset with my laptop and netbook on XP and no problems at all. The sound through my headset is fine too. It's juts the mic. I dont know what make it is but there's a pic below:

[IMG]http://i48.tinypic.com/wip7s.jpg[/IMG]

As a heads up, my webcam (Phillips 315NC) doesn't work with skype either but I thought I'd get the sound issue resolved first as the cam is less of a priority.

Thanks

Looking at your set up with the head set connected I can see that you are using the line in. I thought initially that your headset was USB.

All you have to do is chose "Line-In" from the dropdown on Sound Preferences -> Input.

That should solve all your problems.

---

### Post by cozski on 2010-01-11
I'm not quite sure how I resolved it but I know  that i have to have Mic 2 selected... it hears nothing with mic 1. I will post the caps so people can see the confiuration. Also, there is no Line-in to select... Still no webcam though - just jumbled transmission :(

---

