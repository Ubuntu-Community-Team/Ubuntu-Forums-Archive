---
title: "No sound on flash videos"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by VitaminBB on 2009-11-01
So I upgraded to 9.10 the other day and the sound was working fine but now it wont work with flash videos.

I have tried uninstalling flash and reinstalling, no good.

I have tried installing the nonfree version, no good

I have tried installing it through the ubuntu software center, no good

I have tried to locate a ALSA firefox plugin, no good

I have tried to figure out how to add other sound outputs, no good (see image below).

[IMG]http://i79.photobucket.com/albums/j121/ArghMonkey/Screenshot.png[/IMG]

Any ideas? cause this is killing me, why after decades of development, cant Linux ever get it right?

---

### Post by VitaminBB on 2009-11-01
Not sure what happened but in between installing and uninstalling flash and installing alsa mixer, the sound decided to die 100%.

Now I have no sound at all, not startup, not programs, nothing ...

*sigh* 

I should have just left version 9.04 installed ...

---

### Post by Waggdogg on 2009-11-01
I also upgraded to 9.10 and have no sound at all. I think my mute button was on when I down loaded Ubuntu 9.10. I also need help.

---

### Post by hansmex on 2009-11-14
After upgrading to 9.10 I also don't have sound in flash movies.
Very annoying, if I may say so.

---

### Post by quiet guy on 2009-11-15
I'm having similar problems too.

The sound in any online flash player is good for only about 30 sec. before it stops completely, even though the video will continue to play (badly).

Also, in Movie Player it will play, but only in a choppy and incoherent manner.
VLC has no sound at all.

Help?

Anybody?

---

### Post by Thelasko on 2009-11-15
Did you try installing the "flashplugin-nonfree-extrasound" package?

---

### Post by Windows Nerd on 2009-11-15
Sound is broken for a lot of people in Karmic at the moment. Your best solution would be to do a fresh install (I always do a fresh install when upgrading a distro) or wait a month until the devs fix the problem, like they usually do (they really do need to think over thier development cycle, because they never fix all the really annoying bugs that remain when they release the final version).

Scott

---

### Post by dalee on 2009-11-15
Hi,

Here's a good thread on sound problems you might want try before doing a fresh install. [here]("http://ubuntuforums.org/showthread.php?t=766683")

Though for me I ended up simply uninstalling PulseAudio to get my sound working.

---

### Post by sandyd on 2009-11-15
sigh....
pulseaudio seems to still be having a lot of compatability problems with flash. and some other applications it seems.](*,)

```

sudo apt-get remove pulseaudio pulseaudio-*

```and then restart and see if everything works (the system should automatically fall back to ALSA sound)
really dont know why they still have pulseaudio enabled by default in karmic after the problems with it in jaunty.

NOTE: after reading the posts in this thread, I have go give out this warning.
Some audio/video apps have a backend for pulse. This is a problem cause the backend depends on the pulseaudio packages, which the above command will remove...

In some cases, you will have to reinstall the application, but be sure NOT to install the pulseaudio backends. Just make sure the alsa backends are enabled and thats it.

---

### Post by Malibyte on 2009-11-19
Carlee, this has fixed the problem for me on three machines.  

I agree.  Pulseaudio is not ready for prime-time.  ALSA may not be bug-free but it's definitely the better of the two.

---

### Post by Azraele on 2009-12-04
> **carlee said:**
> sigh....
pulseaudio seems to still be having a lot of compatability problems with flash. and some other applications it seems.

```

sudo apt-get remove pulseaudio pulseaudio-*

```and then restart and see if everything works (the system should automatically fall back to ALSA sound)
dont know why they still have pulseaudio in karmic after the problems with it in jaunty.

thank you carlee, flash sound is perfect now..

Pulse audio is quite crappy, it already created issues when I installed a new ati video card, screwing up with HD sound support of the new card and the old sound card..

I suggest using the latest Alsa modules ;)

---

### Post by mustard greens on 2009-12-04
someone should mark this one solved

---

### Post by Simulation Brain on 2009-12-24
Just wanted to share how I fixed my new install of Karmic:

"PCM" volume on KMix had been automagically turned all the way off at some point- with it on, everything works!

---

### Post by khopek on 2010-01-07
I have the exact problem, however installing the nonfree plugin seemed to work...temporarily...meaning it works until my computer sits all day while i'm at work.I come back home, and have no audio in flash objects.

Then after installing the FIX/WORKAROUND on the ubuntu wiki thing, audio is completely gone.

---

### Post by bobbyo23 on 2010-01-21
> **carlee said:**
> sigh....
pulseaudio seems to still be having a lot of compatability problems with flash. and some other applications it seems.

```

sudo apt-get remove pulseaudio pulseaudio-*

```and then restart and see if everything works (the system should automatically fall back to ALSA sound)
dont know why they still have pulseaudio in karmic after the problems with it in jaunty.

this worked great...boot up sound, hulu, everything. but the only problem im having now is the only way i can control the sound is through the window im viewing that show or whatever in...hulu for example. even when its all the way up its not loud at all....

Any help is much appreciated.

---

### Post by bobbyo23 on 2010-01-21
oh and also when i try and open sounds via system/control center/sounds it says Waiting for sound system to respond''

---

### Post by NoonienSoong97 on 2010-02-06
When I tried using sudo apt-get remove pulseaudio pulseaudio-*. It did work for me. However my video card driver reset on me, and I had to reinstall it. Plus I noticed a few other audio files from other programs were deleted. I haven't check them out yet. Also I noticed that vlc was deleted not sure why the whole program was since I only deleted the audio files. I would really like to run vlc to watch dvd isos of my dvd collection.

Plus only time will tell. I have had audio for Hulu Desktop at first when I tried to install audio. However in the past when I restart the OS. The audio would not properly load up, and I would have no sound for Hulu Desktop, or any flash based video.

---

### Post by sandyd on 2010-02-06
> **NoonienSoong97 said:**
> When I tried using sudo apt-get remove pulseaudio pulseaudio-*. It did work for me. However my video card driver reset on me, and I had to reinstall it. Plus I noticed a few other audio files from other programs were deleted. I haven't check them out yet. Also I noticed that vlc was deleted not sure why the whole program was since I only deleted the audio files. I would really like to run vlc to watch dvd isos of my dvd collection.

Plus only time will tell. I have had audio for Hulu Desktop at first when I tried to install audio. However in the past when I restart the OS. The audio would not properly load up, and I would have no sound for Hulu Desktop, or any flash based video.
updated my post to make it a bit clearer

---

### Post by ratcheer on 2010-02-06
I had a thread about two weeks ago and I got my problem fixed. My problem, and maybe yours too, is that I have two sound cards and PulseAudio (and my speakers) was using the second one. However, it seems that Flash does not use PA, at all, and it only outputs through the first ALSA soundcard.

So, to fix it, I had to edit the ALSA configuration to force the sound card I don't use to be second instead of first. Now, PA, ALSA, and Flash all output to the "correct" sound card and everything works.

PA is not the problem, it just hides the problem, which is the ALSA configuration.

Tim

---

### Post by Thelasko on 2010-02-06
> **ratcheer said:**
> However, it seems that Flash does not use PA, at all, and it only outputs through the first ALSA soundcard.


Flash does not use Pulseaudio by default.  You must install "flashplugin-nonfree-extrasound" to make it work.  You may also have to install "libasound2-plugins" to get some programs to use pulseaudio.

---

### Post by NoonienSoong97 on 2010-02-07
I did install flash-plugin-nonfree-extrasound file awhile back. When I had it installed I would get sounds off of flash based files from time to time. An example would be when I did have it availible, and I would have to restart the OS for some reason after that I wouldn't get any sound from any flash file.

---

