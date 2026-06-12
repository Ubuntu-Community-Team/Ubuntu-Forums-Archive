---
title: "start up sound only"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Knowle on 2009-05-17
I've installed Ubuntu 9.04 using Wubi. I thought it was working, I got the (drum?) sound at the login screen but I can't get any sound after I've logged in. I'm not sure what may have changed(as far as audio is concerned) since the last time I tried Ubuntu(back in '06 I think) other than PulseAudio being added in now.

In my volume control it was set to Audigy 2 ZS [SB0350] (Alsa Mixer). When I right click on the sound icon and go to preferences it was set to Intel ICH5(Alsa Mixer). So I changed it to match what was shown in volume control. Still no go. 

I went through part A here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)  no luck. 
```
knowle@ubuntu:~$ $ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
bash: $: command not found

```


What else can I do to get sound working after I've logged in?

---

### Post by kpkeerthi on 2009-05-17
Go to System -> Preferences -> Sound. Change everything to Pulse Audio and click on the Test button to see if you hear any sound. 

If it still sounds muted, open a terminal and enter **alsamixer**. Make sure the channels are not muted (especially the Master and PCM) and volume levels are raised to a reasonable level.

Press 'Esc' to quit alsamixer
Use your arrow keys to change the channels.
If a channel is muted it should be displayed a 'M', otherwise 'OO'. Press the 'm' key to toggle mute.

---

### Post by natirips on 2009-05-17
> **Knowle said:**
> I've installed Ubuntu 9.04 using Wubi. I thought it was working, I got the (drum?) sound at the login screen but I can't get any sound after I've logged in. I'm not sure what may have changed(as far as audio is concerned) since the last time I tried Ubuntu(back in '06 I think) other than PulseAudio being added in now.

In my volume control it was set to Audigy 2 ZS [SB0350] (Alsa Mixer). When I right click on the sound icon and go to preferences it was set to Intel ICH5(Alsa Mixer). So I changed it to match what was shown in volume control. Still no go. 

I went through part A here: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)  no luck. 
```
knowle@ubuntu:~$ $ sudo apt-get install libasound2-plugins padevchooser libsdl1.2debian-pulseaudio
bash: $: command not found

```


What else can I do to get sound working after I've logged in?

Apropos "command not find", notice the two $ signs, there should be only one. In tutorials the leading $ sign only denotes it should be $, not a # sign. So you don't have to copy-paste / type the $ sign.

A $ sign means you are doing something as a user.
A # sign means you are doing something as a root (default system administrator).

---

