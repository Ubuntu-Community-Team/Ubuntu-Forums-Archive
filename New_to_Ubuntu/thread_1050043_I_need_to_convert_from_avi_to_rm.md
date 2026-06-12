---
title: "I need to convert from avi to rm"
date: 2009-01-25
forum: New to Ubuntu
---

### Post by ghostat2005 on 2009-01-25
I tried to install realproducer_basic_111_linux_setup.tgz and after after installed it i cant use it its too hard
after that tried this command sudo apt-get install mencoder
and this command didn't work :confused:

At last installed 2 program (easy real media producer - Real.Producer.Plus) but the Windows version runs with Wine

And didn't work also :( i get error message (the file doesn't contain recognized data to encoding ](*,)

Plz help me 

Thanks

---

### Post by ghostat2005 on 2009-01-25
up

---

### Post by oldos2er on 2009-01-25
Can you please post the output of the command you entered, 'sudo apt-get install mencoder'

---

### Post by ghostat2005 on 2009-01-25
> **oldos2er said:**
> Can you please post the output of the command you entered, 'sudo apt-get install mencoder'

Thanks for your reply 

And the out put was

Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package mencoder

---

### Post by trentscott4 on 2009-01-25
It's in the multiverse repository which you need to enable:

[http://ubuntuforums.org/showthread.php?t=510621](http://ubuntuforums.org/showthread.php?t=510621)

Then do a 'sudo apt-get install mencoder' :).

---

### Post by ghostat2005 on 2009-01-25
> **trentscott4 said:**
> It's in the multiverse repository which you need to enable:

[http://ubuntuforums.org/showthread.php?t=510621](http://ubuntuforums.org/showthread.php?t=510621)

Then do a 'sudo apt-get install mencoder' :).

Thanks i will try this

What about Windows version with wine in these program easy real media producer - Real.Producer.Plus

---

### Post by llamabr on 2009-01-25
Wine is so rarely the answer.

What happened when you installed mencoder?

---

### Post by oldos2er on 2009-01-25
"What about Windows version with wine in these program easy real media producer - Real.Producer.Plus"

 You can check the Wine database here: [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by ghostat2005 on 2009-01-25
when i try this code :gksudo gedit /etc/apt/sources.list

the output was :

 gksudo gedit /etc/apt/sources.list
-bash: gksudo: command not found

---

### Post by oldos2er on 2009-01-25
Which version of Ubuntu are you running? Xubuntu or Kubuntu?

---

### Post by ghostat2005 on 2009-01-25
> **oldos2er said:**
> Which version of Ubuntu are you running? Xubuntu or Kubuntu?

Ubuntu 8.04.1 and i use kde interface

---

### Post by jerome1232 on 2009-01-25
Then that command will be
```
kdesu kate /etc/apt/sources.list
```

---

### Post by ghostat2005 on 2009-01-25
> **jerome1232 said:**
> Then that command will be
```
kdesu kate /etc/apt/sources.list
```

Thanks and i will try

---

### Post by ghostat2005 on 2009-01-25
This is the output 

kdesu kate /etc/apt/sources.list
kdesu: cannot connect to X server

---

### Post by ghostat2005 on 2009-01-25
Up

---

### Post by llamabr on 2009-01-25
just try:

sudo nano /etc/apt/sources.list

to edit that file.

---

### Post by 3rdalbum on 2009-01-25
The terminal window in KDE is called Konsole. No need to do a "Control-Alt-F1" switch.

Can I ask why you need your files in Real Media format? There are much better video codecs out there, like h.264 or MPEG-4.

---

### Post by ghostat2005 on 2009-01-26
> **3rdalbum said:**
> The terminal window in KDE is called Konsole. No need to do a "Control-Alt-F1" switch.

Can I ask why you need your files in Real Media format? There are much better video codecs out there, like h.264 or MPEG-4.

Because rm files smaller than avi ,h.264 and MPEG-4 also good Quality

---

### Post by ghostat2005 on 2009-01-26
> **llamabr said:**
> just try:

sudo nano /etc/apt/sources.list

to edit that file.

this code worked but i didn't see any # to enable multiverse 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted univer$

Any way thanks for help

---

### Post by ghostat2005 on 2009-01-26
up

---

### Post by oldos2er on 2009-01-26
> **ghostat2005 said:**
> this code worked but i didn't see any # to enable multiverse 

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted univer$

Any way thanks for help

 Is that your entire sources.list? Read [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine) , about the middle of that page there's help on adding multiverse.

---

### Post by tdayal on 2009-01-26
To be honest, I would stay away from realmedia. Do some research, the codecs mentioned earlier are a LOT better.

---

