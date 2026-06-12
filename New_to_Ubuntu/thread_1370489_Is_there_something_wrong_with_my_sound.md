---
title: "Is there something wrong with my sound?"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by Daremo_06 on 2010-01-02
I have noticed that if I have something like rythmbox open (in this case its not even playing anything right) and if I am using another application that also uses sound such as an online java game (runescape), the online game doesnt play sound.  I just went to Youtube and it plays sound correctly.

I must have something configured wrong somewhere right?

I am running 9.10, latest flash and java, firefox 3.5.3.

Any suggestions on where to start looking?

---

### Post by duanedesign on 2010-01-04
On the lowest level, only one application can use the sound card at a time. To enable multiple applications to use the sound card simultaneously, you need a sound server, and most Ubuntu editions use PulseAudio as sound server. However, if an application manages to grab the sound card before PulseAudio does, sound will not work. 

**Diagnosis**
In the volume control applet, PulseAudio lists a dummy/null sink.

Open a terminal and enter this command: 

```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

If you see something else than "pulseaudio" in the rightmost column, such as "slmodemd" or "timidity", you're affected. 

The workaround depends on what process you saw blocking the sound card. 

**slmodemd**

The slmodemd is a daemon related to your modem, which is known to sometimes block audio. You can get rid of this problem permanently by doing one of these things:

    * Uninstall the sl-modem-daemon package (if you don't use the modem).
    * Use the PulseAudio package available in the Ubuntu audio dev PPA
    * Upgrade to Lucid (if you know what it means to run a development version of Ubuntu). 

Otherwise; follow the instructions below. 

**timidity**

Timidity is a MIDI file player. You can reconfigure it to use the esound protocol (which pulseaudio implements) by editing the file /etc/default/timidity (you'll have to be root to do that). Find the row saying 'TIM_ALSASEQPARAMS="-Os"' and change it to: 

```
TIM_ALSASEQPARAMS="-Oe"
```

Then restart timidity: 

```
sudo /etc/init.d/timidity force-reload
```

**others**

Kill the application locking the soundcard using the killall command. For example: 

```
killall slmodemd
```

...if it was "slmodemd" that was locking the sound card. Ensure that the problem was fixed by retrying the "sudo fuser -v /dev/dsp* /dev/snd/*" command.

Then restart PulseAudio with the following command:

```
killall pulseaudio
```

PulseAudio will then autospawn (restart itself).

Depending on what process you just killed, you might have to take different measures to make sure it does not try to start it again, or reconfigure it not to grab the sound card exclusively. 

[Comprehensive Sound Soloution Guide]("http://ubuntuforums.org/showthread.php?t=205449")

[Debugging Sound Problems/Karmic]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")

---

### Post by Daremo_06 on 2010-01-11
Ok I figured out whats causing this.  I am occasionally running a Java script to a online game website.  If I start the java ap before starting something else with sound, then it takes over the sound card.

here are the results of running 

```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

are this.

> /dev/dsp:            rob        2081 F.... java
/dev/snd/controlC0:  rob        1845 F.... pulseaudio


So if I quit the java ap and then open something else (avi, rhythmbox, ect) then it works fine.  

How can I fix this permanently?

Thanks!

---

### Post by Lekensteyn on 2010-01-16
I'm having the same problem.
When I start RuneScape (Java), it blocks the sound card.
```
$ sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
                     GEBRUIKER   PID SOORT PROGRAMMA
/dev/dsp:            user         3493 F.... java_vm
/dev/snd/controlC0:  user         1689 F.... knotify4
                     user         1721 F.... kmix

```

Is there a way to alter Java's configuration, so it'll use the sound server?

---

### Post by Lekensteyn on 2010-01-16
Bump!

I want to hear sound while an applet is running.

---

### Post by Lekensteyn on 2010-01-17
Bump.

---

### Post by Lekensteyn on 2010-01-18
Bump.

---

### Post by ibuclaw on 2010-01-18
You must enjoying bumping threads. ;)

For both of you, your problem seems to be that you have multiple applications controlling multiple sound devices.

Mine looks like this:
```

sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
                     USER PID ACCESS COMMAND
/dev/snd/controlC0:  jstdio     2974 F.... pulseaudio
/dev/snd/pcmC0D0p:   jstdio     2974 F...m pulseaudio

```
And when running that, I had Rhythmbox, Youtube, LastFM, Alien Arena and Empathy  (and technically firefox with all it's click button effects) making noises all at the same time.

edit:
But I must admit that Java is not included in that list (infact - I don't think I even have Java installed).

Regards
Iain

---

### Post by Pikestaff on 2010-01-18
Lekensteyn - While it may not be the answer you want to hear, I struggled with this for a while (I could only ever get one application to play sound at a time) before discovering that it appears to be a bug in Kubuntu Karmic: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/447844](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/447844)

My solution is that, for now, I am using Gnome.  Sound now works as it should.  It saddens me because I really do prefer KDE, but I like having sound more, (and it was between that and a downgrade, and I'm lazy.)

So if all else fails try a sudo aptitude install ubuntu-desktop and try logging as as Gnome and seeing if that fixes your problem.

---

### Post by Lekensteyn on 2010-01-19
> **Pikestaff said:**
> Lekensteyn - While it may not be the answer you want to hear, I struggled with this for a while (I could only ever get one application to play sound at a time) before discovering that it appears to be a bug in Kubuntu Karmic: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/447844](https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/447844)

My solution is that, for now, I am using Gnome.  Sound now works as it should.  It saddens me because I really do prefer KDE, but I like having sound more, (and it was between that and a downgrade, and I'm lazy.)

So if all else fails try a sudo aptitude install ubuntu-desktop and try logging as as Gnome and seeing if that fixes your problem.
That sounds like a drastically change.
Can I just install ubuntu-desktop, and uninstall it afterwards without problems?

I don't know if it matters, but from PulseAudio, I've only *libpulse0* installed (not pulseaudio).
From Alsa, I've installed: alsa-base, alsa-utils, libasound2, libasound2-plugins, linux-sound-base.

How do I set up a system, so everything use alsa? (or other things recommended)
By the way, this is my output for *fuser -v /dev/dsp* /dev/snd/* /dev/seq**
```
                     USER   PID ACCESS COMMAND
/dev/snd/controlC0:  user         1645 F.... knotify4
                     user         1680 F.... kmix

```

---

### Post by Pikestaff on 2010-01-19
> **Lekensteyn said:**
> That sounds like a drastically change.
Can I just install ubuntu-desktop, and uninstall it afterwards without problems?

If it doesn't fix your issue and/or you don't like it, you can type in **sudo aptitude uninstall ubuntu-desktop** in the terminal and you'll go back to normal KDE, as far as I'm aware.  And if that doesn't work, then [this should]("http://psychocats.net/ubuntu/purekde").

---

### Post by Daremo_06 on 2010-03-05
> **Daremo_06 said:**
> Ok I figured out whats causing this.  I am occasionally running a Java script to a online game website.  If I start the java ap before starting something else with sound, then it takes over the sound card.

here are the results of running 

```
sudo fuser -v /dev/dsp* /dev/snd/* /dev/seq*
```

are this.



So if I quit the java ap and then open something else (avi, rhythmbox, ect) then it works fine.  

How can I fix this permanently?

Thanks!

Is there any solution to this issue?  Reading a couple different threads, and saw various things to install, but I really dont want to install anything till i know for certain what its going to do.  I just wiped my system out and started with a fresh install of 9.10 and would prefer not to bork it up at least for a week or so :)

---

### Post by MindFusion on 2010-03-06
This really pisses me off about the Ubuntu community sometimes.. on all internet fora, they claim to have the best user support and the most active forum community, but when i post a topic like this one in General Help (with thesame problem) I only get half-assed replies from members who just give me some vague links to other topics where the answer *might* be in somewhere. 

What happened to the user support hm ?

[http://ubuntuforums.org/showthread.php?t=1415503](http://ubuntuforums.org/showthread.php?t=1415503)

Try solving this.

---

### Post by Daremo_06 on 2010-03-11
This solved it.

[http://www.mixedsoup.com/how-to-fix-sound-issues-in-ubuntu-9-10/](http://www.mixedsoup.com/how-to-fix-sound-issues-in-ubuntu-9-10/)

I put the link in another post with a better title to make it easier to find.

---

