---
title: "VLC player starts then sound stops"
date: 2010-09-12
forum: New to Ubuntu
---

### Post by beew on 2010-09-12
Hi, 

I have vlc player 1.1.4 on lucid. It has been working fine except when it started a file the sound can get a bit choppy. I reset the audio output setting from "default" to Alsa and the choppy start up problem was fixed. But today I encounter a new problem which I don't think existed before. After leaving Vlc on for a while (playing audio files) it will start   playing a file and then the sound will stop even though it is still running according to the status bar. This always happens in the begining of a file, it plays a few seconds and then the sound dies. If I jump ahead for a few tracks and press play it will start and play normally again. After a few songs the problem will occur again. I changed the output setting back to default but the problem persists. 

My thanks in advance for any help.

---

### Post by beew on 2010-09-12
Ok, just run vlc in the terminal and get these error messages

> VLC media player 1.1.4 The Luggage (revision exported)
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")
Blocked: call to sigaction(17, 0xb68010d4, 0xb6801048)
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Warning: call to srand(1284013449)
Warning: call to rand()
Blocked: call to setlocale(6, "")

(process:25261): Gtk-WARNING **: Locale not supported by C library.
    Using the fallback 'C' locale.
Warning: call to signal(13, 0x1)
Warning: call to signal(13, 0x1)
Blocked: call to setlocale(6, "")

---

### Post by jtarin on 2010-09-12
And you had this identical problem before you upgraded?

---

### Post by beew on 2010-09-12
No, it just started today but I have upgraded long time ago. When it plays audio files it always starts a new file with a sound like a hicup. I tried to fix that by changing the output setting from "default" to ALSA  and this might have been the cause. I have just reinstalled vlc and changed the setting back to default and see what's going to happen.

---

### Post by beew on 2010-09-12
After reinstalling and changing the output module I let VlC run for a whole night and it didn't stop so this problem is solved, but the hicup sound has returned. It only happens in the beginning of the songs but it is still annoying, please help!

---

### Post by sadaruwan12 on 2010-09-12
Are you still using the 1.1.4 or the legacy version that comes in the Ubuntu repository?

If the chopping problem is there remove the 1.1.4 version and install the 1.0.6 from the repository and see whether the problem still persist.

---

### Post by beew on 2010-09-12
The chopping is/was present in both 1.0.6 and 1.1.4 (it has been like that since I installed vlc in day one, long before I upgraded to 1.1.4) and now I am still using 1.1.4

---

### Post by mc4man on 2010-09-12
Don't have that issue but a few things to try
If you don't have a surround sound setup and using alsa was eliminating the issue than use alsa but first search vlc in synaptic and uninstall the vlc pulseaudio plugin
Then see it it works better.

Otherwise you could try upping the buffer in tools - preferences - all - see screen

---

### Post by beew on 2010-09-12
mcman

Thanks for the response, tried your suggestion, it didn't work. This is the situation. If I use default output setting then there would be annoying cracking and popping sounds when a new song starts up; if I switch to Alsa then those hiccups disappear but after a while there would be no sound at all even though vlc is still working and if I wait some more sound will come back intermittently (I tried OSS and Pulse audio for output modules as well but it was the same, either vlc became quiet after a while or it hiccupped on start or both )

I installed other media players to test it. Amarok,  Banshee and Audacious all have no problem. This is peculiar to vlc.

---

### Post by jtarin on 2010-09-13
Are you using Compiz? If yes try turning off and see if it persists.

---

### Post by beew on 2010-09-14
Hi, jtarin,

Thanks for the reply. Well I disabled Campiz but the problem persists.  If I changed the output to ALSA then not only do I eliminate the hiccups (actually a "popping" sound) in the begining of some audio files but in general the sound appears to be richer and smoother, but then the sound would stop  or become intermittant after a few songs. With output set to "default" this doesn't happen, but I get the popping sound.

---

### Post by jtarin on 2010-09-14
Start your player from the commandline, in a terminal and watch for any unusual messages when this behavior starts.

---

### Post by jtarin on 2010-09-14
Some links to look at and methods to try...let us know if you get something working.
[http://ubuntuforums.org/showthread.php?t=524147](http://ubuntuforums.org/showthread.php?t=524147)
[http://www.linuxjournal.com/node/1000262](http://www.linuxjournal.com/node/1000262)

---

### Post by beew on 2010-10-17
I just discovered that VLC no longer starts with that annoying hiccup sound in Maverick,--it has that problem on two or three Lucid installations I tried on different machines. I wonder how it is fixed in Maverick and whether somehow I can use the "fix" in Lucid..

---

### Post by wackenedgar on 2012-02-02
I have ubuntu 10.10 with vlc 1.1.4
What should I try

---

