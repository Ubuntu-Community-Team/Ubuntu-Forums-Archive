---
title: "jumpy sound"
date: 2009-06-18
forum: New to Ubuntu
---

### Post by philipballew on 2009-06-18
whenever i try to play a game the sound is jumpy almost like its playing it but parts are missing from the sound. like it plays only a fourth of a second every second. say maina drive or my 64 emulator it will be jumpy and not work. the sound is jumpy. i have been trying to fix it so i did the pulse audio switch [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384) doing everything it says there. that didn't help and i want to get some oppinions.

---

### Post by baruch60610 on 2009-06-18
I'm not certain what the problem is, but it could be that your CPU is being kept busy to the extent that it can't adequately play the sound continually.  That is, for a fraction of a second, it needs to be busy doing something (such as displaying your graphics), and puts the sound on "hold", so to speak.

Try to play some sound when you're not playing any games, when you have very little going on in your system - no games, no programs running, just playing the sound.  If you get good sound then, try adding some programs.  At some point, if my idea is accurate, you'll get to a point where the sound wil skip again.

The only "cure" I know for this is to try to keep the number of running processes to a minimum.  You can check what processes are running by using either gnome-system-monitor or the process monitor for KDE (forgot the name; sorry).  That should give you an idea of what's running, and how much of your resources each process is taking.

You may find that the system automatically runs things you don't care about.  For example, often it will run a program that scans through your entire filesystem, getting the name and location of each file. This takes up lots of resources.  There are others that may also be running in the background.  See what's happening.  There is a good chance you can stop those processes, or schedule them for a time when you're not using the computer.

---

### Post by philipballew on 2009-06-18
that might be because my prossesor does shoot up to 100 percent whenever i open games. i shoind say im running a 32 bit ubuntu when my possessor is a amd64

---

### Post by philipballew on 2009-06-18
i oppend up probable 30 internet browsers  opened pictures and opend up 30 ubuntu help pages and 2 videos and banshee olaying music.the sound on the videos and music was fine.

---

### Post by philipballew on 2009-06-19
whenever i try to play a game the sound is jumpy almost like its playing it but parts are missing from the sound. like it plays only a fourth of a second every second. say maina drive or my 64 emulator it will be jumpy and not work. the sound is jumpy. i have been trying to fix it so i did the pulse audio switch [http://ubuntuforums.org/showthread.php?t=1130384](http://ubuntuforums.org/showthread.php?t=1130384) doing everything it says there. that didn't help and i want to get some oppinions.

---

### Post by RichLouth on 2009-06-23
Hi all. I had a problem with my sound where it was being jumpy/skipping every few seconds. It took me ages to track down the problem until eventually thought of the right Google search:)

It turns out it was an issue with the amount of buffer ALSA uses and it may be related to the way ALSA works with snd-hda-intel. If you have sound jumping then I recommend you check this link:

[http://www.linuxquestions.org/questions/linux-general-1/alsa-sound-jumpy-alsa-space-xrun-of-at-least-11.449-msecs.-resetting-stream-310756/]("http://www.linuxquestions.org/questions/linux-general-1/alsa-sound-jumpy-alsa-space-xrun-of-at-least-11.449-msecs.-resetting-stream-310756/")

Basically you have to create a file ".asoundrc" without quotes in your home directory and make sure you give it plenty of buffer. The configuration he recommends in his code box worked perfectly for me (although I gave myself more buffer to be sure). And here it is again:

```
pcm.dsp {
	type plug
	slave.pcm "dmixer"
}

pcm.!default {
	type plug
	slave.pcm "dmixer"
}

ctl.!default {
	type hw           
	card 0
}

pcm.dmixer {
	type dmix
	ipc_key 1024
	slave {
		pcm "hw:0,0"
		period_time 0
		rate 48000
		period_size 4096
		buffer_size 16384
	}
	bindings {
		0 0
		1 1
	}
}

ctl.dmixer {
	type hw
	card 0
}
```

Happy listening

---

### Post by RichLouth on 2009-06-23
This might help:

[http://ubuntuforums.org/showthread.php?p=7505646#post7505646]("http://ubuntuforums.org/showthread.php?p=7505646#post7505646")

---

