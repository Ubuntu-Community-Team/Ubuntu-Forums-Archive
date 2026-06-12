---
title: "No sound on gtk-recordMyDesktop"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by hanzj on 2010-05-13
I've just installed gtk-recordMyDesktop (RMD from henceforth) on a fresh-install of UBuntu 10.04. There is no sound in the file that RMD creates.

The sound that I wish to capture is the sound from a flash video playing on a webpage.


I tried the advice given at [http://ubuntuforums.org/showthread.php?t=1428157](http://ubuntuforums.org/showthread.php?t=1428157), but to no avail.

Please help.

---

### Post by einstenian on 2010-05-23
same here,i think this is an unsolvable problem :-(


p.s: 
Solved thanks to the link: [http://fostergrant.ubuntuforums.org/showthread.php?t=1328176&page=3]("http://fostergrant.ubuntuforums.org/showthread.php?t=1328176&page=3")

1) Install pulse mixer applet;
2) Open alsamixer and set everything up (except the microphone), including capture;
3) Start the music;
4) Open gtk-recordMyDesktop and in sound tab insert "pulse" in place of "DEFAULT";
5) Start recording;
6) Launch pulse mixer;
7) In the recording tab choose  "Monitor analog stereo of Internal Audio" in place of "analog stereo of Internal Audio";
8) enjoy!;

---

### Post by hanzj on 2010-05-28
Can experienced Linux users confirm whether einstenian's plan is good or not? Thanks.

---

### Post by JohnElway on 2011-01-02
I know this thread is half a year old, but I just wanted to confirm that the above solution did work for me! Thanks!  Just to clear up any confusion, the "pulse mixer applet" is the Pulse Audio Volume Control, which can be found under the name pavucontrol.

---

