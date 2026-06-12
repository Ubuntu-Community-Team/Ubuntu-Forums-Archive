---
title: "Have no sound n Hardy Heron"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by Lakeside5 on 2008-12-10
I have no sound on Hardy Heron whatsoever.
> Start here:

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

Once you know your sound card is recognized go here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

I must be doing it wrong. I started out entering this line, exactly like this, at the root: mkdir ~/pulse-backup && cp -r ~/.pulse ~/.asound* /etc/asound.conf /etc/pulse -t ~/pulse-backup/ and then this one after it was finished: sudo rm -r ~/.pulse ~/.asound* /etc/asound.conf, and then step 3, and 4, and 5 (and then saw pulseaudio WAS listed in applications) But when I tried `Open the PulseAudio Volume Control application` select volume control, and try to set volume meter playback and recording, I get `no default sink set`. If I try to launch it from the terminal, I see `segmentation fault. If I just click on `volume control` in the menu, I don`t see anything, something goes by so quick, I don`t see it. I look in `Manager` and see that default sink and default source are not set. so I check default source, default sink, and default server and and no network devices are found. What am I doing wrong please

---

### Post by gettinoriginal on 2008-12-10
try typing Alsamixer in terminal and see what results you get.  If there is only one, you only have alsa, if there are more, you have pulse also

---

### Post by Lakeside5 on 2008-12-10
I typed it in, lower case (also tried first letter capitalized) just like this: :~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
that is what I got :(
Then, I got the idea to use `locate`, and did this and found these files:

locate alsamixer
/usr/bin/alsamixer
/usr/share/app-install/desktop/alsamixergui.desktop
/usr/share/app-install/desktop/gnome-alsamixer.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_alsamixergui.xpm
/usr/share/app-install/icons/_usr_share_pixmaps_gnome-alsamixer_gnome-alsamixer-icon.png
/usr/share/doc/alsa-utils/README.alsamixer
/usr/share/man/man1/alsamixer.1.gz
But I`m a noob, so I don`t know what this means or what to do with it :)

---

### Post by billgoldberg on 2008-12-10
> **Lakeside5 said:**
> I typed it in, lower case (also tried first letter capitalized) just like this: :~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such file or directory
that is what I got :(
Then, I got the idea to use `locate`, and did this and found these files:

locate alsamixer
/usr/bin/alsamixer
/usr/share/app-install/desktop/alsamixergui.desktop
/usr/share/app-install/desktop/gnome-alsamixer.desktop
/usr/share/app-install/icons/_usr_share_pixmaps_alsamixergui.xpm
/usr/share/app-install/icons/_usr_share_pixmaps_gnome-alsamixer_gnome-alsamixer-icon.png
/usr/share/doc/alsa-utils/README.alsamixer
/usr/share/man/man1/alsamixer.1.gz
But I`m a noob, so I don`t know what this means or what to do with it :)


Go to sound -> preferences -> sound and see if OSS works.

Also, use the asoundconf command to see if your sound device is being used (or intall asoundconf-gtk for the gui tool).

---

### Post by Lakeside5 on 2008-12-10
Ok, this is what I got from asoundconfig at the terminal: Usage:
asoundconf is-active
asoundconf get|delete PARAMETER
asoundconf set PARAMETER VALUE
asoundconf list

Convenience macro functions:
asoundconf set-default-card PARAMETER
asoundconf reset-default-card
asoundconf set-pulseaudio
asoundconf unset-pulseaudio
so then, being a noob, I was guessing and put this in the terminal: asoundconf set-pulseaudio
(hey, I`m a little impulsive I know, but I haven`t had sound for 3 weeks, and I need it for some tutorials ;(  :)  thanks for all your help so far billgoldberg, I hope I can figure this out!

---

### Post by Lakeside5 on 2008-12-11
Thanks for all the help so far from everyone. I`m still trying to figure this out though..:(

---

### Post by abn91c on 2008-12-11
in a terminal sudo modprobe snd- then press the TAb key then press enter, look for your sound card driver next type sudo modprobe snd-your sound card
example mine is sudo modprobe snd-opl3sa2
if it tell you something like the card is found you are Ok, next do aplay -l
if the card is found it will be listed, next to save the card type sudo alsactl store 0
follow this guide for more details [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by Lakeside5 on 2008-12-11
I got: module snd- not found.  So I googled `find sound card..` and wound up here: [https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting) and followed the advice, installing ALL those modules and rebooting, and still no card was found, I did not see any `audio device` listed when I entered `lspci -v | less`, just a long list of things that all had `unknown device` in them, all I recognized was  ASRock Incorporation K7VT6 motherboard
, and Via Technologies Inc. if that helps. Typing in  aplay -l just gave me: 
 List of PLAYBACK Hardware Devices ****
card 0: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 0: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
Is my sound card in there somewhere? I had this computer built for me, by a little old man in a shop that doesn`t exist anywhere, and I can`t find the man, so I`m not sure, maybe it is a strange sound card lol.

---

### Post by Lakeside5 on 2008-12-11
Wow! I just found my `device manager` on here (browsing around trying to figure why I couldn`t view my nework connection info. but that`s another issue, oh boy) and discovered all this info about my audio!  Turns out my sound card is: VIA 8237 with CMI9761A+, anyway I chose this for my sound playback, and was jolted with very old Marley Music, literally music to my ears!  I hope I can remember what I did if this happens again when I update to say, 8.10 (no no nooooooooo) lol. thanks, this forum rocks:guitar:

---

### Post by abn91c on 2008-12-11
> **Lakeside5 said:**
> I got: module snd- not found.  
, and Via Technologies Inc. if that helps. Typing in  aplay -l just gave me: 
 List of PLAYBACK Hardware Devices ****
card 0: V8237.

 try sudo modprobe snd-v8237

---

### Post by Lakeside5 on 2008-12-11
Thanks, I will try that, because I am getting sound from music files in my computer, but not from videos on youtube, or tutorials from websites. (crossing my fingers).
*edit* just did that, and I got: FATAL: Module snd_v8237 not found.
Why, oh why :(
Well, now I know what my soundcard is ( Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 A), that it is installed, and also that Ubuntu is detecting the presence ofmy soundcard, but the drivers are not installed/running. After this, it gets fuzzy for me.  The link suggested to `search for your sound card (chipset) manufacturer in the dropdown box.` isn`t for a helpful site. And another site I went to, for alsa, didn`t have info on my soundcard, but maybe I typed it in wrong? Do I type the whole thing? Or maybe I really do just need a compatible sound card, for ubuntu. I hopenot $$$$$ lol.
It`s weird though, I CAN hear music files from my hard drive, just not on websites...(like  youtube etc.) Any thoughts? and thanks for all the help so far, I feel less `lonely` in  my struggle lol.

---

### Post by Lakeside5 on 2008-12-12
You know, I`ve been thinking, sine I can hear the .avi movie files in my computer, and the mp3`s too, but not the videos on the net, it is probably an adobe flash player problem etc. If so, I will google on this (I usually do anyway, in addition to bugging you guys on the formums :) ) If anyone has advice, that`s good too.

---

### Post by philinux on 2008-12-12
Have a look in ```
about:plugins
``` to determine which flash player is operational.

---

### Post by Lakeside5 on 2008-12-12
Ok Philinux, I shall do that, thanks.  I just did this though: sudo apt-get install libflashsupport and suddenly I can hear youtube videos. Life just gets better and better...lol thanks.
I entered: about:plugins just like that, no sudo or anything, but it said command not found.

---

### Post by philinux on 2008-12-12
> **Lakeside5 said:**
> Ok Philinux, I shall do that, thanks.  I just did this though: sudo apt-get install libflashsupport and suddenly I can hear youtube videos. Life just gets better and better...lol thanks.
I entered: about:plugins just like that, no sudo or anything, but it said command not found.

Goes in firefox address bar. :p

---

### Post by Lakeside5 on 2008-12-12
:oops: Lololololol! I shall type it in there then..
*edit* Wow, what a cool trick, thanks so much for that amazing tip, now I know what I have, and I see the flashplayer I just installed!

---

### Post by markbuntu on 2008-12-12
if you really want to get your sound dialed in you can go here

A quick fix for Intrepid and Hardy if you have sound somewhere

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

For more extensive help troubleshooting or setting up your sound

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

---

