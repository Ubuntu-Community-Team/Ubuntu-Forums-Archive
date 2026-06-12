---
title: "Cannot play any media files"
date: 2010-05-22
forum: New to Ubuntu
---

### Post by ajbain88 on 2010-05-22
On my Ubuntu I can't play any media files through VLC, mplayer, movie player, or any media player I download. I can play media thats streamed through the internet but whenever i try to open a music or video file the media player immediately closes itself. 

Any help would be more than appreciated as it's really bloody annoying!! :(

(I don't know if this is related but I also can't play any audio through headphone/speakers, even though it plays perfectly fine through the laptop speakers.)

---

### Post by stevedes on 2010-05-22
Try running the player from the terminal and see if it spews out any error messages upon crashing.

---

### Post by ajbain88 on 2010-05-22
OK so I opened it through terminal and this is the message I got after it closed...

QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x9df4ca0] pulse audio output: No. of Audio Channels: 2
[????????] x11 video output error: X11 request 132.19 failed with error code 11:
 BadAlloc (insufficient resources for operation)
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  132 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  106
  Current serial number in output stream:  107
Segmentation fault

Is there anything I can do about it??

---

### Post by gordintoronto on 2010-05-22
Please tell us the specs for your system: memory, disk space, processor, video adapter.

Did you install the "restricted extras"?

---

### Post by sandyd on 2010-05-22
try running ```
sudo pulseaudio -k
```and see if your sound returns. If it does, then I got a fix for you.

---

### Post by ajbain88 on 2010-05-22
I tried the code but this was the message i got:

boomtingthe1st@boomtingthe1st-laptop:~$ sudo pulseaudio -k
E: core-util.c: Home directory /home/boomtingthe1st not ours.
E: main.c: Failed to kill daemon: Permission denied



I'm using this on quite an old laptop and my system specs are:

Intel Celeron 1.7 GHz
512mb RAM
VIA UniChrome Pro Shared Video Memory (UMA)

---

### Post by ajbain88 on 2010-05-22
And yes I already have the restricted extras package installed

---

### Post by tankjer on 2010-05-22
> **ajbain88 said:**
> boomtingthe1st@boomtingthe1st-laptop:~$ sudo pulseaudio -k
E: core-util.c: Home directory /home/boomtingthe1st** not ours**.
E: main.c: Failed to kill daemon: Permission denied

Explanation: You run from a root account by using sudo, and sudo doesn't own your user directory.

Solution: Run *pulseaudio -k* and there should be no errors

---

### Post by ajbain88 on 2010-05-22
I don't understand, how do I run without using sudo??

---

### Post by tankjer on 2010-05-22
> **ajbain88 said:**
> I don't understand, how do I run without using sudo??
Think of a sudo as a command that runs other command. When you run for example, a gedit program by typing in 'gedit' in terminal, you run without sudo. When you type 'sudo gedit', sudo runs first, and then executes gedit. So by running 'gedit', or 'pulseaudio -k' in this case, you don't run sudo at all.

tl;dr You don't write sudo at the beggining of the command

---

### Post by ajbain88 on 2010-05-22
Oh OK i see what you mean. I tried that and nothing happened, and i tried opening music and video files and still no luck...

---

### Post by ashwinhgtx on 2010-05-23
Have you ever been able to play media files on this computer? As in with previous versions of Ubuntu or any other OS?


Can you play audio files?

Try changing the video output to xv in mplayer.

---

### Post by lidex on 2010-05-23
Try this. In a Terminal="Applications->Accessories->Terminal"
```
sudo apt-get update
sudo apt-get upgrade
sudo update-grub
```
**Reboot**
Do parts 1 & 2 here:
[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

---

