---
title: "avi files have audio and no video"
date: 2010-07-17
forum: New to Ubuntu
---

### Post by ni ni on 2010-07-17
hello all,

absolute beginner here.  no avi, mkv, divx etc file will play.  I only have audio!  I tried vlc, totem etc.

is there something i have to type into terminal?


Sorry i'm a beginner i will provide more info if needed.

---

### Post by jtarin on 2010-07-17
Start the player from the terminal....then with the player, open your file to play. Watch the terminal for any indicative messages of the players functioning and post any seeming abnormalities here.

---

### Post by ni ni on 2010-07-17
how do i start the player from the terminal? :-(

---

### Post by jtarin on 2010-07-17
Usually the player name will do it.

---

### Post by ni ni on 2010-07-17
[HTML]niamh@niamh-laptop:~$ vlc
VLC media player 1.0.6 Goldeneye
QPainter::begin: Paint device returned engine == 0, type: 1
QPainter::begin: Paint device returned engine == 0, type: 1
[0x8f89310] pulse audio output: No. of Audio Channels: 2

[/HTML]

---

### Post by jtarin on 2010-07-17
Thats all?? Try another player and see if you have a different message. Did you ever have video?

---

### Post by jtarin on 2010-07-17
Open VLC Player, Go to Preferences -- Video -- Check Enable video...Then in the **Display** portion check output and if it is set to default and not working select X11 video output from the drop-down list.

Restart VLC Player.

---

### Post by enebre on 2010-07-17
thank you, it works for me.

---

### Post by jtarin on 2010-07-17
Excellent....now to enjoy it.

---

### Post by ni ni on 2010-07-25
Thank you thank you thank you!!!!!!!!!!!!!!!!!!!!!!:KS:KS:KS:KS

---

### Post by Keytard on 2010-08-20
This is the most helpful thread I have ever come across. I have spent days searching the forums here and elsewhere for a solution to this problem.

I have even tried reinstalling Ubuntu, and reinstalling different versions of ubuntu.

I really appreciate the help provided here!

---

### Post by jtarin on 2010-08-20
We appreciate the thanks when we can help someone overcome their difficulties with Linux.....I can remember how it was when I started....and then it was a lot more difficult than it is today.

---

### Post by Jessfarnsworth on 2013-04-20
simple...just set the output to x11...solve my problem in seconds...thank you.

---

### Post by howefield on 2013-04-20
Old thread closed.

---

