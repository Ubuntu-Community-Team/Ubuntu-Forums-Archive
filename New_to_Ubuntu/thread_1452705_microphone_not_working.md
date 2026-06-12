---
title: "microphone not working"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by rexwesker on 2010-04-12
i cant use my mic.it says that it is umaplified.need help please

---

### Post by Sef on 2010-04-12
Moved to ABT.

---

### Post by sydbat on 2010-04-12
> **rexwesker said:**
> i cant use my mic.it says that it is umaplified.need help pleaseCan we get more information please? 

What version of Ubuntu are you using? 
Have you tried opening the 'Sound Preferences' and making sure the mic is not muted?
If the mic is not muted, there should be an option for mic boost.

---

### Post by rexwesker on 2010-04-12
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc3/hs463.snc3/25419_114120351939992_100000260830054_187034_5425208_n.jpg[/IMG]

i got ubuntu 9.10 :lolflag:

---

### Post by rexwesker on 2010-04-13
tnx in advance for the help..:guitar:

---

### Post by Azrael3000 on 2010-04-13
what kind of computer do you have?
what mic are we talking about (built in/external)?
can you post the output of
```

lspci | grep Audio

```

---

### Post by rexwesker on 2010-04-13
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)

Desktop computer and external MIC

---

### Post by Azrael3000 on 2010-04-13
did you already find the following thread: [http://www.linuxquestions.org/questions/linux-hardware-18/microphone-doesnt-work-intel-hd-audio-619337/](http://www.linuxquestions.org/questions/linux-hardware-18/microphone-doesnt-work-intel-hd-audio-619337/)

the last post is actually about ubuntu.

---

### Post by rexwesker on 2010-04-13
sorry,still unsolved

---

### Post by Azrael3000 on 2010-04-13
can you post a screenshot when running
```

alsamixer

```
in a terminal and press [TAB] once (on the top left line 'View' [Capture] should be highlighted.

---

### Post by rexwesker on 2010-04-13
[IMG]http://sphotos.ak.fbcdn.net/hphotos-ak-snc3/hs463.snc3/25419_114213115264049_100000260830054_187471_4617840_n.jpg[/IMG]

i can record sound now.but i cant use it in voice chat on tinychat.com

---

### Post by lidex on 2010-04-14
Go here and work through the page. Make sure to install the alsa-backports:
[https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats]("https://wiki.ubuntu.com/DebuggingSoundProblems/KarmicCaveats")
Do 'Part A' here:
[http://ubuntuforums.org/showthread.php?t=789578]("http://ubuntuforums.org/showthread.php?t=789578")
When that's done, open alsamixer and press F4 or tab to select capture devices.

---

