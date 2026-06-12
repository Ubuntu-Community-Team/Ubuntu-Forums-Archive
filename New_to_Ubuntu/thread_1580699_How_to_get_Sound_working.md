---
title: "How to get Sound working"
date: 2010-09-23
forum: New to Ubuntu
---

### Post by corrytonapple on 2010-09-23
I had fully working sound, until recently I disable the alsa drivers as stated in a link from some Ubuntu documentation. What do I do to get sound and turn on the asla drivers? Thank you

---

### Post by lkjoel on 2010-09-23
> **corrytonapple said:**
> I had fully working sound, until recently I disable the alsa drivers as stated in a link from some Ubuntu documentation. What do I do to get sound and turn on the asla drivers? Thank you
Try Fix your sound! in my signature.
It will get your sound working, in a different way.

---

### Post by Kixtosh on 2010-09-23
Have you tried this procedure to update the ALSA drivers?

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

If you type in terminal, at the ~$ prompt:```
cat /proc/asound/version
```

You should get a result similar to this:```

Advanced Linux Sound Architecture Driver Version 1.0.21.
```

As you can see, my version is not completely up to date!

---

### Post by corrytonapple on 2010-09-27
> **lkjoel said:**
> Try Fix your sound! in my signature.
It will get your sound working, in a different way.
Sorry for the late reply. Lots of school work to do. But, I did try that link and I still get no sound. I am sure it is all plugged properly. In Sound Preferences, it does not see my Intel HR9. (Or whatever it is called, it ends in 9)
> **Kixtosh said:**
> Have you tried this procedure to update the ALSA drivers?

[http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04/)

If you type in terminal, at the ~$ prompt:```
cat /proc/asound/version
```You should get a result similar to this:```

Advanced Linux Sound Architecture Driver Version 1.0.21.
```As you can see, my version is not completely up to date!
I will not be able to check your method until I get alsa running. This is because I have tried the OSS.

---

### Post by andrewthomas on 2010-09-27
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by corrytonapple on 2010-10-09
> **andrewthomas said:**
> [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
When trying step four of "General Help", I got this message:
```

corrytonapple@toshiba-laptop:~$ sudo modprobe snd-
[sudo] password for corrytonapple: 
WARNING: All config files need .conf: /etc/modprobe.d/alsa-base, it will be ignored in a future release.
FATAL: Module snd_ not found.
corrytonapple@toshiba-laptop:~$

```
I tried redownloading the ALSA drivers from the help section called "[SIZE=2][SIZE=1]Getting the ALSA drivers from a *fresh* kernel[/SIZE]", [SIZE=1]and it did work, so when I went back to step four, I tried again and I got the same message. What do I do?[/SIZE]
[/SIZE]

---

### Post by corrytonapple on 2010-10-10
Nevermind the above post. The sound works, except if I try to adjust it on my laptop or keyboard, nothing happens. Also, the sound panel won't open, and the sound area on my top panel (the one with applications, system, ect) is not there. How do I get that back? How do I adjust my sound volume besides the GNOME ALSA Mixer?

---

### Post by corrytonapple on 2010-10-14
I am bumping this. All I want to do is have my laptop be able to control the sound from the wheel on the front. The sound panel is not on/in the top panel, and when I go to "Preferences", it says, "Waiting for sound system to respond". I wait but nothing happens. Help please!

---

### Post by lkjoel on 2010-10-16
> **corrytonapple said:**
> I am bumping this. All I want to do is have my laptop be able to control the sound from the wheel on the front. The sound panel is not on/in the top panel, and when I go to "Preferences", it says, "Waiting for sound system to respond". I wait but nothing happens. Help please!
Thats a problem with PulseAudio.
You can try removing PulseAudio, and then installing OSS.
The guide is in Fix your sound! in my signature.

---

### Post by corrytonapple on 2010-10-16
> **lkjoel said:**
> Thats a problem with PulseAudio.
You can try removing PulseAudio, and then installing OSS.
The guide is in Fix your sound! in my signature.
I have tried OSS, and had problems. Then if I do it again, I will not be able to get back to where I am without going through all of those guides again. So how do I get pulseaudio to work. I could use the nob on the front and it worked when I first installed Ubuntu.

---

### Post by lkjoel on 2010-10-17
What version of OSS?

---

### Post by corrytonapple on 2010-10-17
It is the version that was latest on the page. I am trying them again.
Edit: OK, so I tried it again, downloaded, restart, installed, restart, and it works! Some of the best sound I have ever heard. But, I now have an issue with being able to control the volume using the wheel on the front of my laptop. How do I make that work. Once that works, I am done!

---

### Post by corrytonapple on 2010-10-30
How do I get Pulseaudio to play nicely with OSS?
Thanks

---

### Post by lkjoel on 2010-11-01
> **corrytonapple said:**
> How do I get Pulseaudio to play nicely with OSS?
Not meaning to sound rude, but it seems you will tell me to install OSS and Remove ALSA, and when I do then I need help and you never respond. Are things OK?
Thanks
Sorry, I was not on UF for a long time.
You have to remove PulseAudio and ALSA for now.
Then once you have finished installing OSS, tell me.
I will show you how you can re-install them without corrupting OSS.

---

### Post by corrytonapple on 2010-11-01
I am still using OSS. Never switched back. So how Do I take care of PulseAudio? I will edit out the last part of my last post.
Thanks, I understand.

---

### Post by lkjoel on 2010-11-02
> **corrytonapple said:**
> I am still using OSS. Never switched back. So how Do I take care of PulseAudio? I will edit out the last part of my last post.
Thanks, I understand.
[http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#Pulseaudio]("http://www.opensound.com/wiki/index.php/Configuring_Applications_for_OSSv4#Pulseaudio")
That page also contains ways to use OSS with other applications.

---

