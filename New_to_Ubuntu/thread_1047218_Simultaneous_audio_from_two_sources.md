---
title: "Simultaneous audio from two sources"
date: 2009-01-22
forum: New to Ubuntu
---

### Post by guavas on 2009-01-22
Hi,

I am using Ubuntu 8.04 LTS. Everything is working just fine, except this one little issue: my laptop will only play one audio at a time. For example, if I am logged in to Skype (without even having a conversation open) and try to play a song at the same time (with any player) then the I won't be able to listen to the song. Whichever application started first would have complete control over the audio output. Replace Skype by YouTube, and the problem remains the same. I don't even have to be playing the YouTube video, it just has to be open in a tab.. and VLC won't be able to produce any audio output.

I have tried to play around with the settings in Skype as well as in VLC etc., with no results. I'd appreciate any help that you can give me.

Let me know if you need me to post the output of some command etc.

---

### Post by linux_tech on 2009-01-22
First make sure you have esound and alsa-oss installed-
```
sudo apt-get install esound
```
```
sudo apt-get install alsa-oss
```

reboot

Then you can try disabling pulseaudio-
```
killall pulseaudio
```

If this resolves the issues then you will need to look at ways resolve the pulseaudio issue 

ref [https://help.ubuntu.com/community/alsa-oss](https://help.ubuntu.com/community/alsa-oss)

---

### Post by guavas on 2009-01-25
Thanks linux_tech,

I managed to do it by killing pulseaudio. And diabled the software sound mixing by going to System/Preferences/Sound.

Thanks once again!

---

