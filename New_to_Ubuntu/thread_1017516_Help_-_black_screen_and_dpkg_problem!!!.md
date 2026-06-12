---
title: "Help - black screen and dpkg problem!!!"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by firsttimeholmes on 2008-12-21
Hi everyone 

Im v new to linux and ubuntu and find it all a bit of a challenge....

My son (18mths) got hold of my laptop and as a result i couldnt get firefox to open and my network doo dah disappeared... :(

Im not sure what he pressed... then i got a dkpg error come up when i tried to sort it out with the synaptics manager

I had also done a software update yesterday so maybe thats whats messed it up..

anyway i decided to try and fix it by going into recovery mode and now when i switch it on i get the ubuntu progress bar but then a black screen and nothing else happens...

PLs help me :(
:confused::confused::confused::confused:

---

### Post by ibizatunes on 2008-12-21
Hello, depends on what has happened but from what i can make out, a update hasnt finished installing

if you can get to the terminal type, (you may need to reboot and drop in to recovery mode)

```
sudo dpkg --configure -a
```

then

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by firsttimeholmes on 2008-12-21
> **ibizatunes said:**
> Hello, depends on what has happened but from what i can make out, a update hasnt finished installing

if you can get to the terminal type, (you may need to reboot and drop in to recovery mode)

```
sudo dpkg --configure -a
```

then

```
sudo apt-get update && sudo apt-get upgrade
```
Already tryed that :( found that earlier on - doesnt seem to make any difference :(

---

### Post by firsttimeholmes on 2008-12-21
Would i be better off just reinstalling and starting all over again and if so where do i start - and is it possible to do it from a usb as I dont have a cd drive in my webbook

---

### Post by ibizatunes on 2008-12-21
Can you copy the error message and put it on the forums, that will help

---

### Post by Eisenwinter on 2008-12-21
You can also try sudo apt-get -f install

---

### Post by firsttimeholmes on 2008-12-22
How do i get the error message?? 

i vaguely remember it being something along the lines of 'configure--a'

if that helps - but followed instructions that i found online for that and it didnt fix it

---

