---
title: "Lost audio"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by beswatcher on 2009-02-07
After going from 8.04.26.24-22 to 26.24-23, I have no audio. No CD audio, no streaming audio, nothing.
lspci shows a sound card;

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 02)

In the BIOS the audio is enabled. Any help at all would really be appreciated.

---

### Post by huam on 2009-02-07
I have the same problem with 2.6.27-11-generic. If I boot the previous one
2.6.27-9-generic then I can hear very soft sound.

Audio device: 
nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)

If I do a test getting :

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

No hardware problem because if I boot windows vista :( I have sound.

Grtz Huub.

---

### Post by billgoldberg on 2009-02-07
If you go to system -> preferences -> sound

and choose something else than the default and then press "test" does any of those produce audio?

If it does, pick that one.

If not, say so.

--

Also install asoundconf-gtk, open it and make sure your card is the default one.

---

### Post by sci50514 on 2009-02-07
> **huam said:**
> I have the same problem with 2.6.27-11-generic. If I boot the previous one
2.6.27-9-generic then I can hear very soft sound.

Audio device: 
nVidia Corporation Realtek ALC1200 8-Channel High Definition Audio Codec (rev a1)

If I do a test getting :

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

No hardware problem because if I boot windows vista :( I have sound.

Grtz Huub.

This works for me when I upgraded my Ubuntu and got this no audio device problem. Remove the .asound and related folders in your home directory.

---

### Post by beswatcher on 2009-02-07
To show everyone how much of a beginner I am, I can not find any .asound files. 

system -> preferences -> sound in every choice gives me

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Could not open audio device for playback.

(and I'm running a utube video at this time)

More confused than ever!

---

### Post by beswatcher on 2009-02-07
Sorry about the bump, but I just booted from an old Knoppix Live CD that the sound tested OK in. Now I have gone to ->applications -> other -> sound system here and the test sound comes through with no problem.

More confused!

---

### Post by huam on 2009-02-07
> **billgoldberg said:**
> If you go to system -> preferences -> sound

and choose something else than the default and then press "test" does any of those produce audio?

If it does, pick that one.

If not, say so.

--

Also install asoundconf-gtk, open it and make sure your card is the default one.
Thanks very much.
I installed the asoundconf-gtk and I create ,asound directory, and now I'm
listening to my music again :D.

I don't think creating .asound has to too with the solution, but anyway
Have to reboot the system.

Thanks again.

---

