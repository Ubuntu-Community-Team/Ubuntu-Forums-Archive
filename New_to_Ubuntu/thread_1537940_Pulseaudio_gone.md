---
title: "Pulseaudio gone"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by matyasfalvi on 2010-07-24
Hi All!

I use Kubuntu 10.04. I have recently updated my ALSA using this:  [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137)  how to. Everything was fine. I kept getting the messages at system start up that some devices were not used and I was asked: 

```
...  do you want to permanently forget about these devices ...
```

I accidentally clicked yes. Since then my sound is horror. Probably what has happened is that it forgot about pulseaudio cause I can't seem to find it anymore under Compuer -> System Settigns -> Multimedia.

The strange thing is that I keep getting messages that some sound devices do not work but when I go test them they do. for e.g:
Phonon tells me ```
  the audio playback device HDA Intel etc. does not work. 
``` When I go to multimedia to test it this is the only one working. I cannot seem to find any useful thread as to how to get pulseaudio back to work again I only seem to find threads telling how to remove it. 

The situation now is that my system sound works fine, everything else e.g.: Amarok, flash etc. just works for a few minutes then it shuts down. This is really frustrating.

Any help would be much appreciated.
Thanx

---

### Post by ankspo71 on 2010-07-24
> I cannot seem to find any useful thread as to how to get pulseaudio back to work again I only seem to find threads telling how to remove it. 

Hi, here is the link that I used to install pulseaudio in Kubuntu Lucid. [http://kubuntuguide.org/Lucid#PulseAudio](http://kubuntuguide.org/Lucid#PulseAudio). Be sure that your username is still added to the groups listed in the link above. This probably won't help the ALSA problem, but I hope it helps.

---

### Post by matyasfalvi on 2010-07-29
Hi! 
Thanx a lot for your response. I have installed pulseaudio using the [link]("http://kubuntuguide.org/Lucid#PulseAudio") you have provided.

During the installation phase. I didn't find the group: > pulse-rt.

After the installation. On reboot, the opening sound was gone, flash, skype doesn't work. Amarok does work properly. 

What I'm still missing is: In Kmenu -> Computer -> System Settings -> Multimedia. At the > Output Device Preference I do not see pulseaudio i.e. I cannot prefer it. The last fully working system configuration was when at the Output Device Preference list pulseaudio was at the top of the list.

Any ideas as how to get the pulseaudio option to be displayed in the Output Device list?

Once again thank you for your help. i really appreciate it.

---

### Post by ankspo71 on 2010-07-29
Hi,
I think the group "pulse-rt" is the same group as the group "rtkit" I added my name to that group and it was working for me as expected. Try adding your username to that group to see if pulseaudio will appear in the Output Device Preference list.

I'm using Kubuntu Maverick alpha2 at the moment and I don't see the Output Device Preference option. I'm going to boot into my Kubuntu Lucid Live cd and look in there. 

Edit: Nevermind lol.I found it, and it was right there in front of me. I don't see anything mentioning pulseaudio either. I think the device they are referring to is the actual sound card. The screenshot below is how my list appears. (you might see some differences in our Kubuntu versions though)

Hope this helps.

---

### Post by ankspo71 on 2010-07-29
Hi Again,
I'm back. I couldn't install pulseaudio in the Kubuntu Live CD so I had to install Kubuntu Lucid in virtualbox, then install pulseaudio.

Before I installed pulseaudio in Kubuntu Lucid, the was no mention of pulseaudio in "Output Device Preference". I looked there just to be sure.

After installing pulseaudio, a mention of pulseaudio became available in the "Output Device Preference".

(However, in Kubuntu Maverick, pulseaudio is already installed and there still is no mention of pulseaudio in "Output Device Preference")

I installed pulseaudio in Kubuntu Lucid using the same guide I mentioned before [http://kubuntuguide.org/Lucid#PulseAudio](http://kubuntuguide.org/Lucid#PulseAudio)
The groups I added my username to was: 
audio, pulse, pulse-access, rtkit (which I believe is the same as pulse-rt)
Then I rebooted.

So hopefully, adding your name to the group "rtkit", will bring back  pulseaudio to the "Output Device Preference" I'm attaching another screenshot to show the diffence between the previous screenshot. (Maverick versus Lucid, both with pulseaudio)

---

### Post by matyasfalvi on 2010-08-02
Hi there!

Thanx a lot for your respons and your help. After adding my username to "rtkit" things have improved a whole lot. Everything works now: amarok, skype, flash etc. So I'm very happy about that. Still some things are missing. I still can't find pulseaudio under "Output Device Preference" list. Flash and amarok conflict. (Which btw was working before the ominous update that many people talk about here on the forum). Also the opening sound is missing.  

Once again this is a configuration I can live with, for now, cause after all everything is working, one by one. So I'm very happy and I really appreciate the help you have given me. Thank you again. Nonetheless my sound configuration is still not 100% that is a fact and personal experience tells me that with such an instable configuration it doesn't take too much time for everything to go pear shaped again. 

Take care!

---

### Post by matyasfalvi on 2010-08-02
Here is the screen shot of my Device Preference list:

---

### Post by matyasfalvi on 2010-08-02
sorry here it is:

---

### Post by matyasfalvi on 2010-09-14
Hello Everybody,

Well just as I have expected. My sound crashes within 10 min. intervals, again and again. So I think that what I need to figure out in the first place, is the one thing that I have started this thread. Namely the message I was getting at system start up: that some devices were not in use anymore:
```
...  do you want to permanently forget about these devices ...
```

Could anyone help me figure out what this does? 

I'm thinking that once I have figured what this does, then may be reversing this could repair my audio.

Any help is much appreciated. 

Thank you very much.

Take care.

---

### Post by a_flj_ on 2010-12-14
Oddly enough, I have just about the same problem as you - on kubuntu lucid. After updating alsa as described in [http://ubuntuforums.org/showthread.php?t=1046137](http://ubuntuforums.org/showthread.php?t=1046137), I got a continuous beep in my speakers, so I had to remove the updated version. Since then, I have no more pulse. I tried:
```
apt-get purge pulseaudio
```
then rebooted, then
```
apt-get install pulseaudio
```
But nothingn seems to help - I don't get the pulse-audio device back into the list of audio devices phonon recognizes.
Anybody any idea?

---

