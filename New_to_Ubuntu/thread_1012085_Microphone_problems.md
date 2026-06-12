---
title: "Microphone problems"
date: 2008-12-15
forum: New to Ubuntu
---

### Post by papanoelys on 2008-12-15
My mic suddenly stopped working on skype.clicked on volume icon,the settings appear ok,all turned up
tried sudo/ete/dev/dsp1>/dev/dsp a message"device or resource busy" came up
 tried vumeter-r&   a message returned "cannot connect to sound daemon please run esd at a command promt"  
I opened the sound recoder but am unable to capture any output from the microphone. I  selected capture 1 and 2
can anyone help

---

### Post by gettinoriginal on 2008-12-15
Don't know if this will help, as I don't use skype.  Open your volume control, switches tab, tic mic boost.  :p

---

### Post by donkyhotay on 2008-12-15
Sounds like your mic is in use by another program/service. If you don't have anything using it right now it may be a crashed program locking you up. Try restarting your computer then recording something with the sound recorder.

---

### Post by papanoelys on 2008-12-16
Thanks guys for the replies .No luck with those posts.Mic boost option does not seem to be available .I rebootd my pc several times.

---

### Post by linux_tech on 2008-12-16
Try this
Install gnome-alsamixer

```
sudo apt-get install gnome-alsamixer
```
then run gnome-alsamixer
```
gnome-alsamixer
```
unmute mic

---

### Post by papanoelys on 2008-12-18
Getting what sounds like static when I try and playback my voice recording. No skype output at all. Tried "vumeter-r&" command but got message saying cannot connect to sound daemon.

---

### Post by donkyhotay on 2008-12-18
Are you using alsa or ESD? I found this other post that sounds like it might be related to your issue:
[http://www.linuxquestions.org/questions/linux-newbie-8/bizarre-cannot-connect-to-sound-daemon...-17301/](http://www.linuxquestions.org/questions/linux-newbie-8/bizarre-cannot-connect-to-sound-daemon...-17301/)

---

### Post by papanoelys on 2008-12-19
Using ALSA mixer. Still no joy. Will try and load alsa drivers again.

---

### Post by papanoelys on 2008-12-20
Looks like I already have the latest ALSA drivers. I dont know what to do next.

---

### Post by papanoelys on 2008-12-21
Can anyone help ?

---

### Post by linux_tech on 2008-12-21
> **papanoelys said:**
> My mic suddenly stopped working on skype.
```
sudo apt-get install skype-static-oss
```

---

### Post by papanoelys on 2008-12-22
Couldn't find package skype-static-oss,This message came up when I typed that Command in. thanks

---

### Post by papanoelys on 2008-12-27
Anyone have any ideas please?

---

### Post by papanoelys on 2009-02-27
This problem turned out to be a faulty microphone. I want to say a sincere thank you to all who posted replies to help me. I am only sorry I didnt check the obvious first,but I learned alot in the whole process of troubleshooting audio problems.

---

