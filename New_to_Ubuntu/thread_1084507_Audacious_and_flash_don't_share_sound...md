---
title: "Audacious and flash don't share sound..??"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by kramer65 on 2009-03-02
Hello,


Sometimes sounds don't work with flash video's, and sometimes they don't work with audacious. I now found out that when I start ubuntu I can start flash video's and the audio will work, but audacious doesn't. I need to restart ubuntu to get audacious to play some sounds again, but this leaves flash video's without any sounds.

As you may understand this is pretty frustrating. Does anybody know what the problem and solution could be?

---

### Post by Sirron on 2009-03-02
The problem is that traditionally, linux audio has been a real mess. Many applications chose to simply try to take complete control of the sound card rather than share it with other apps.

As part of an ongoing push to solve the problem, ubuntu now ships with Pulse Audio, which uses all kinds of tricks to make audio enabled apps play fair with eachother.

Unfortunately it's not compatible with all applications; particularly the Flash 9 plugin and audacious. Even if you've got flash 10 (which I encourage you to get if not), audacious may still be trying to get at your sound card without going through Pulse Audio, depending on how you've got it configured.

Check out [_this_]("http://www.pulseaudio.org/wiki/PerfectSetup#Audacious") solution.

---

### Post by kramer65 on 2009-03-02
Hi Sirron,


I deinstalled flash 9, downloaded flash 10 and installed it, and made sure that audacious uses the PulseAudio Output plugin.

I tried both ways of sharing; first starting audacious and then a flash movie, and first a flash and then audacious, but both ways don't work.

Do you know anything else which I could try?

---

### Post by Sirron on 2009-03-02
Well, in the terminal you could try

```
pasuspender audacious
```

"pasuspender" suspends pulse audio and launches the application you specify. Of course, that will mean that only that application can play audio while it runs, but it may help you track down the cause of the problem.

---

### Post by kramer65 on 2009-03-02
Well, that indeed helps to take the sound from the one application back to the other without restarting gnome again. I still can't play both audacious and a youtube vid however. I had it working before and it suddenly stopped working (don't know when or why anymore)..

Can't I use alsa or something for one of the applications? The thing is that this is really making the use of ubuntu so annoying that I even consider going back to windows. It just makes me crazy..

---

### Post by gandaran on 2009-03-02
fix pulseaudio, [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by kramer65 on 2009-03-02
Allright!! I found a solution!!

I simply selected the ALSA thing for audacious and for vlc player, and I can now simultaneously play audacious mp3's vlc video's AND flash youtube movies all with sound!

---

### Post by kramer65 on 2009-03-02
There is one strange thing. When I change the volume in audacious I also influence the volume in the flash movie. So I can't separately change the volume of the flash movie and the mp3 I'm playing in audacious..

But hey. I'm a lot further now..

---

### Post by Sirron on 2009-03-02
Per-application volume controls is one of the advantages of pulse audio. Clearly, to solve your problems once and for all you need to repair pulse audio.

One avenue of investigation might be to "finish" setting it up. By default, the ubuntu desktop obscures pulse audio so most people don't even realise they're running it, but in fact there are a number of front ends to manage some of its more advanced features. I believe the most useful ones are pavucontrol and pavumeter, try searching for them in Synpatic. Sorry, I'm not at an ubuntu workstation right now so I can't check for sure.

---

### Post by markbuntu on 2009-03-02
Try this

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

---

