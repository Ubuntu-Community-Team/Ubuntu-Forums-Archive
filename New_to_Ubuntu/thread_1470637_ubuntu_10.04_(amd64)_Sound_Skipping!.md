---
title: "ubuntu 10.04 (amd64) Sound Skipping!"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by bandersen on 2010-05-03
I get the occasional skip in sound, no matter what i'm doing and no matter what i'm playing.





:(

---

### Post by mbzn on 2010-05-03
What type of sound card do you have? Use lspci to check.

---

### Post by bandersen on 2010-05-03
02:08.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)

---

### Post by bandersen on 2010-05-03
bump

---

### Post by bandersen on 2010-05-03
Heard a rumor that Esound works really good, might just use that...

---

### Post by bandersen on 2010-05-04
esound didn't work BUMPPPP

---

### Post by bandersen on 2010-05-05
Nobody? I'm about to go back to 9.10 :(

---

### Post by scotland42 on 2010-05-09
I first noticed this myself when I installed the beta release canidate in late April.  I didn't worry too much about it at the time, but I just reinstalled the normal release and am getting skipping audio as well.  It doesn't matter what type of audio file it is, flac, mp3, wma, etc.  The audio also skips in video files, avi (divx and xvid), mkv, etc.  I'm not getting any errors in my logs.  Anybody have any ideas?

Thx

---

### Post by Marsonis on 2010-05-10
I am having the same issue.  Like the others, it does not matter what program is playing the sound.  

My audio device is: Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)

If it can't be fixed, I'm considering switching to the 32bit version as a solution.

Any ideas?

---

### Post by ghostborg on 2010-05-12
Well , this pretty much sucks.

---

### Post by Marsonis on 2010-05-15
Well, I just reinstalled to the 32bit version and I am having the same problem . . . anyone have any ideas?

I did not have the issue under 9.10. Please help.

---

### Post by s7726 on 2010-05-18
10.04
Intel 32bit
Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)

Same problem

---

### Post by sez11a on 2010-05-27
Same here, with files that I know worked in Kubuntu 9.10 (I switched to Ubuntu for this release, but if it's PulseAudio that's the problem, I may go back). 

00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)

---

### Post by lidex on 2010-05-27
Have a look here:
[http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html]("http://rightfootin.blogspot.com/2009/05/fixing-pulseaudio-stutters-pauses.html")

---

### Post by adam22 on 2010-05-28
Happens to me in 64 bit 10.04 with Banshee, haven't really tried anything else.

---

### Post by chefbodini on 2010-09-29
I found this in a bug report and added it to my wiki...

```

sudo add-apt-repository ppa:ubuntu-audio-dev/ppa
sudo apt-get update
sudo apt-get install linux-alsa-driver-modules-`uname -r`
```

Not sure if a reboot was required but I did an 'init 6' just for good measure...

---

