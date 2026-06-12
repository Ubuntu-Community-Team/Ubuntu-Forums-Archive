---
title: "Lmms!"
date: 2010-09-11
forum: New to Ubuntu
---

### Post by Vocapex on 2010-09-11
Hello everyone!

I just downloaded the LMMS which I want to use for music production. I have downloaded and save it and now i dont know how to open it and work with it.

help!

---

### Post by s.fox on 2010-09-11
Hello,

Where did you download it from?

Reason I ask is that it should be listed in synaptic under the universe repository (multimedia) .  If you have that repo enabled you will be able to install from there.

-Silver Fox

---

### Post by Vocapex on 2010-09-11
I downloaded from here.

[http://sourceforge.net/](http://sourceforge.net/)

---

### Post by uRock on 2010-09-11
What is the file package? tar.gz or .deb?

---

### Post by hhlp on 2010-09-11
open a terminal ... plication .. accesories ... terminal

Adding this PPA to your system ... to the end of the file ...

```
gksudo gedit /etc/apt/sources.list

deb http://ppa.launchpad.net/tobydox/lmms/ubuntu lucid main 
deb-src http://ppa.launchpad.net/tobydox/lmms/ubuntu lucid main
``` 

and save it , then the follow ...

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys ADDE29B2
```

and the last one :

```
sudo aptitude install lmms
```

and voila you can find in aplications sound and video

---

### Post by Vocapex on 2010-09-11
tar.bz2 is the file.

ill try the commants

---

### Post by Vocapex on 2010-09-11
good!
now i can see it on the ubuntu software centre
how can i open it?

---

### Post by Vocapex on 2010-09-11
kool i got it thought the applications.!

thanks alot!

much appreciated!

---

### Post by gansvv on 2010-11-15
Thanks! Thats perfect to install LMMS on Lucid.

---

