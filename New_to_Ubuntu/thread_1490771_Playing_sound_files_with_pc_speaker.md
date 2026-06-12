---
title: "Playing sound files with pc speaker?"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by tankjer on 2010-05-22
Hello, it's my first post, as I couldn't find any anwser for that question on Google or other forums.
I'm not sure if I'm posting in the right forum, but as I'm quite new with Ubuntu, I post there.

So someday ago when I still used mainly Windows XP, I saw an application for it that could beep with PC Speaker. I liked that idea and found out that my friend did a similar program in C++. He gave me his source code for it and I quickly started to do some music with it, or more precisely, I was just playing around with it.
Then I have installed Xubuntu on my pendrive. I wanted to play some music on PC Speaker just for the fun. I have tried 'beep' program to check if Xubuntu even recognized the PC Speaker, but there was no sound coming out from the speaker. I thought that it could be a cause of bad output. I checked /dev/ but there's no pcspeaker in it. Then I found on Google that you would need to add driver for PC Speaker to kernel and then recompile it, but I didn't like that idea. Anyway that driver was from 1997 and there must have been a lot of changes in the kernel since then.

And now, I would to ask you, if you know a way to play sound files on a PC Speaker in Ubuntu? Do I need to recompile kernel? If yes then how to do this when I use version 2.6.32 of it? Or maybe the required drivers already compiled into it?
 I have a ASUS A7v880 motherboard.
(Though I use Xubuntu, I choose prefix 'All variants' because as I understand, there are no differences between Ubuntu and Xubuntu except that Xubuntu has only XFCE instead of GNOME and it doesn't have Openoffice)

---

### Post by cariboo on 2010-05-23
The snd_pcsp is blacklisted in /etc/modprobe.d/blacklist.conf, so the driver won't load. All you have to do is comment out the line in blacklist.conf and the driver should load on the next reboot.

To comment out the line in the file just place a # at the beginning of the line. To edit the file you need to be root, so press Alt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

once you have commented out the snd_pcsp line it should look like this:

```
# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
# blacklist snd_pcsp
```

If you don't want to reboot to load the driver, just open a terminal and type:

```
sudo modprobe snd_pcsp
```

after the module is loaded, you should be able to make squeaks and beeps. :)

---

### Post by tankjer on 2010-05-23
> **cariboo907 said:**
> The snd_pcsp is blacklisted in /etc/modprobe.d/blacklist.conf, so the driver won't load. All you have to do is comment out the line in blacklist.conf and the driver should load on the next reboot.
Big thanks! I can now use 'beep' with my PC Speaker, and now I know that the location of it is /dev/tty10. Now about how to play sound files in PC Speaker, right now I'm trying to get it work with VLC.

---

### Post by tankjer on 2010-05-23
I googled about that further, and I found out that 'vplay' could play wav files on pc speaker, but I cannot find it anywhere. I have tried to modify alsa-base.conf so that pc speaker would be primary sound device (index=0, while my soundcard has index=1) and I get this when trying to run alsa force-reload as sudo:
> tankjer@tankjer-desktop:/dev$ sudo alsa force-reload
Terminating processes: 5476.
Unloading ALSA sound driver modules: snd-pcm snd-timer snd-page-alloc (*failed: modules still loaded: snd-pcm snd-timer snd-page-alloc*).
Loading ALSA sound driver modules: snd-pcm snd-timer snd-page-alloc.
Now there's no sound at all. I have also tried running *sudo play test.flac /dev/tty10* before changing alsa-base.conf but it freeze. When I now try to run that command it freezes too, but when I use *play test.flac* it looks like it works but I don't hear a thing out of pc speaker.
I'll try to restart Xubuntu to see if it will work.

---

### Post by tankjer on 2010-06-03
I have installed Ubuntu and I could set pc speaker as output in GNOME audio mixer. It works good enough, though even when there should be nothing played, there are some silent beeps.

---

### Post by Joe Casadonte on 2010-06-14
> **cariboo907 said:**
> ```
sudo modprobe snd_pcsp
```after the module is loaded, you should be able to make squeaks and beeps. :)

I got an error trying that:

```
FATAL: Error inserting snd_pcsp (/lib/modules/2.6.32-22-generic-pae/kernel/sound/drivers/pcsp/snd-pcsp.ko): Device or resource busy
```

I get system beeps in the terminal window but not Emacs...

---

### Post by stsp on 2011-02-27
> **tankjer said:**
> I have installed Ubuntu and I could set pc speaker as output in GNOME audio mixer. It works good enough, though even when there should be nothing played, there are some silent beeps.
Removing pulseaudio will fix this. :)

---

### Post by stsp on 2011-02-27
> **Joe Casadonte said:**
> I got an error trying that:

```
FATAL: Error inserting snd_pcsp (/lib/modules/2.6.32-22-generic-pae/kernel/sound/drivers/pcsp/snd-pcsp.ko): Device or resource busy
```I get system beeps in the terminal window but not Emacs...
Removing pcspkr first, will fix this:
rmmod pcspkr
modprobe snd-pcsp
These 2 drivers just do not like each other.

---

