---
title: "webcam and microphone issues"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by glennlad on 2009-01-24
Im having trouble with my microphone and webcam.

I plug them in my cam doesnt show up, and my microphone shows up in the sounds option but if it wont let me use it.

Can anyone assit me please?

Microphone: logitech ICES-003 CLASS B M/N: A-0060A
Webcam: my mom brought it for me its an argos value one lol

---

### Post by amac777 on 2009-01-24
I think you have to run a program that uses the webcam in order to test it. You can try installing the program "camorama" to test the webcam:

```
sudo apt-get install camorama
```

Once it's installed, you'll find it in the menu: Applications->Graphics->Camorama

Also, skype does video and has a webcam testing capability. Both these programs will display my webcam.

About your microphone, does Sound Recorder let you record from it? (Applications->Sound and Video->Sound Recorder)

---

### Post by glennlad on 2009-01-24
I installed camorama opened it and  it said "unable to capture image"

SOund recorder wont give me the option to choose my mic it just says "master"

---

### Post by glennlad on 2009-01-24
*bumps*

---

### Post by diablo75 on 2009-01-24
Click Applications>Accessories>Terminal.

Type in:

```
lsusb
```

And paste the output back in here.

---

### Post by glennlad on 2009-01-24
Bus 005 Device 002: ID 17a1:0128  
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:0a03 Logitech, Inc. Logitech USB Microphone
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bda:0103 Realtek Semiconductor Corp. USB 2.0 Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

---

### Post by diablo75 on 2009-01-24
Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=832805](http://ubuntuforums.org/showthread.php?t=832805)

---

### Post by glennlad on 2009-01-24
OK ive done what they said in ekiga, My cam comes on puts its a green screen instead of me.

---

### Post by glennlad on 2009-01-24
OK ive done what they said in ekiga, My cam comes on puts its a green screen instead of me.

my mic works in ekiga but not the sound recording tool

---

### Post by thunderbirdje on 2009-01-31
it depends on what 'software layer' the program uses:

e.g. camorama uses v4l (if i'm not mistaken), while the newest version of vlc also supports v4l2 (Video for linux 2, same for the program 'cheese'.

My webcam works with the last 2 programs, not with the first.

Good luck!

---

