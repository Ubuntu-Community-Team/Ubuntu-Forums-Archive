---
title: "Skype sound troubles"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by arpeggi on 2009-07-30
Hello all,

I'm having a bit of trouble with getting Skype working on my Dell Vostro 1500 laptop.  I'm fairly new to Ubuntu.  

I'm having trouble getting the audio set up for Skype. In the sound devices panel in options I have no sound with HDA Intel and when i try to use pulse I am finding a huge lag (up to 10 seconds). The microphone I am using is an onboard mic built into my laptop.

This is the error I am getting when trying to use HDA Intel.
[IMG]http://i39.tinypic.com/2rnzbds.png[/IMG]

Not really sure how to solve this problem but it's fairly urgent  - on Sunday I am moving from the UK to Finland away from my parents and all my friends and was planning on using Skype to keep in touch.  

Hope someone can help me - I'll do anything to get this fixed!

Thanks!

---

### Post by nwadams on 2009-07-30
are u using ubuntu 9.04?

in the sound options set all three of the devices to pulse. I am using it without any lag. Try to use the skype version from the medibuntu repository if you aren't already.

EDIT: i'm not 100% sure about my skype set up so i'm willing to help test them. Send me a message or email and I will give you my skype username.

---

### Post by credobyte on 2009-07-30
Setting all devices to pulse should do the trick. Haven't tried official versions ( from Skype website ), but the one from Mediabuntu works just fine :)

---

### Post by arpeggi on 2009-07-30
ok i've installed the medibuntu version of skype and have set everything to pulse. i can hear the test sound but when making the test call i can't hear anything coming back to me.

is there a way to test my microphone in ubuntu without using skype?

---

### Post by credobyte on 2009-07-30
Try *Sound Recorder* ( under Apps / Sound & Video ) :D

---

### Post by nmaster on 2009-07-30
pulse sometimes will cause a CPU leak.  perhaps try post #42: [http://ubuntuforums.org/showthread.php?t=1127056&highlight=skype+cpu&page=5](http://ubuntuforums.org/showthread.php?t=1127056&highlight=skype+cpu&page=5)

---

### Post by arpeggi on 2009-07-30
hmm another problem. when i record myself (i can see the microphone picking something up very slightly) i stop and try to play it back to myself i get this error.

"Internal GStreamer error: state change failed.  Please file a bug at http://bugzilla.gnome.org/enter_bug.cgi?product=GStreamer."

:confused:

---

### Post by nwadams on 2009-07-30
ok do this:

```
 sudo apt-get install gnome-volume-control-pulse 
```

then remove the volume icon in your tray and log out

when you log in right click on the new volume icon and go sound preferences. max the volume on the input tab. then it should record at a better volume level. 

as for the internal GStreamer error, i've no idea what to do.

---

### Post by Katalog on 2009-07-30
PulseAudio seems to be somewhat broken in Ubuntu. For some reason, it doesn't seem to be completely configured correctly in 9.04 (even though it is installed), so you might try fixing Pulse before configuring Skype and see if that doesn't help at all. Here's a couple of links that might help:
[URL="http://ubuntuforums.org/showthread.php?t=789578"]
**HOWTO: PulseAudio Fixes & System-Wide Equalizer Support**[/URL]                

[PulseAudio: The Perfect Setup]("http://www.pulseaudio.org/wiki/PerfectSetup")

I know they helped me get some issues straightened out when I was having trouble with Ekiga.

---

### Post by arpeggi on 2009-07-30
> **neal.m.master said:**
> pulse sometimes will cause a CPU leak.  perhaps try post #42: [http://ubuntuforums.org/showthread.php?t=1127056&highlight=skype+cpu&page=5](http://ubuntuforums.org/showthread.php?t=1127056&highlight=skype+cpu&page=5)

well i have attempted this and it seems to have worked. does this mean i have now installed pulse completely? my microphone is still way too quiet and I am not yet able to test for lag - any suggestions?

my skype username is laurie.humphrey is anyone is interested in helping me test it.

---

### Post by nwadams on 2009-07-30
it means you have removed pulse completely. my previous post woudl have fixed the volume but i've no idea what it will do without pulse installed.

---

### Post by nmaster on 2009-07-30
> **arpeggi said:**
> well i have attempted this and it seems to have worked. does this mean i have now installed pulse completely? my microphone is still way too quiet and I am not yet able to test for lag - any suggestions?

my skype username is laurie.humphrey is anyone is interested in helping me test it.

if you followed my post, then you actually uninstalled pulseaudio and downgraded to esound.  you might just have to fiddle with your sound options to fix the mic issue.  test using the skype test call.  you can find it in the options menu.  at the moment, i'm not really sure: im at work and using XP.  in a few hours ill be at home and might have better advice.

---

### Post by arpeggi on 2009-07-30
thanks for the help. sorry nwadams i had a go at neal.m.master's advice before i read yours.

it seems to have fixed the problem now though. i just called my cell phone from skype and there seemed to be little delay however it is still very quiet. oh well at least this has narrowed down the problem somewhat!

---

### Post by nmaster on 2009-07-30
> **arpeggi said:**
> thanks for the help. sorry nwadams i had a go at neal.m.master's advice before i read yours.

it seems to have fixed the problem now though. i just called my cell phone from skype and there seemed to be little delay however it is still very quiet. oh well at least this has narrowed down the problem somewhat!

i think you might be able to fix this with a change in sound setting.  ill let you know what i think when i get home.

---

### Post by arpeggi on 2009-07-30
success. had a little look around inside of the volume settings and found the digital recording level was only set at halfway. did a test call and now i sound beautiful and loud.

gosh my mother will be pleased that she can talk to me when i move away :D

---

### Post by nmaster on 2009-07-30
> **arpeggi said:**
> success. had a little look around inside of the volume settings and found the digital recording level was only set at halfway. did a test call and now i sound beautiful and loud.

gosh my mother will be pleased that she can talk to me when i move away :D

SWEET! that's what i thought it was, but without personal laptop i couldn't be sure. :)

---

