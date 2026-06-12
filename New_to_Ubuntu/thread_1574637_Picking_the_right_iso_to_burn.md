---
title: "Picking the right iso to burn"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by distortedtempo on 2010-09-14
I've burnt one disk with it on it. When the auto run came up on my computer it just sits there for a long time then doesn't load. I need some help picking the right iso for this computer.

---

### Post by cchhrriiss121212 on 2010-09-14
What image have you burned?
What are your cpu specs?

To install Ubuntu Studio you need to boot from the DVD drive before Windows loads, it has no Wubi (install form Windows) and it uses a text based install. If any of that sounds too complicated, then try out regular Ubuntu.

---

### Post by bodhi.zazen on 2010-09-14
Hard to know without additional information. Could be anything from a hardware incompatibility to a bad download to a bad burn.

What hardware do you have ? CPU ? Videocard ? How much RAM ?

Did you check the md5sum of the iso and test the media ?

---

### Post by distortedtempo on 2010-09-14
Well I've never done a text based install could you give me a walk through?

---

### Post by cchhrriiss121212 on 2010-09-14
Had a look at your other posts, and it seems you are using an old G3 Mac, is that what you wish to install Ubuntu Studio on?
If so I would tell you now not to bother installing studio, it will be way too heavy for it. As the other thread you started mentions, you should go with something lightweight. 
Crunchbang or Puppy Linux.

---

### Post by distortedtempo on 2010-09-14
> **cchhrriiss121212 said:**
> Had a look at your other posts, and it seems you are using an old G3 Mac, is that what you wish to install Ubuntu Studio on?
If so I would tell you now not to bother installing studio, it will be way too heavy for it. As the other thread you started mentions, you should go with something lightweight. 
Crunchbang or Puppy Linux.
 I'm on my laptop it's a Toshiba satellite, I already have ubuntu running on it plus windows vista.  I had my specs up earlier but deleted them because no one was answering.

---

### Post by snowpine on 2010-09-14
> **distortedtempo said:**
> I'm on my laptop it's a Toshiba satellite, I already have ubuntu running on it plus windows vista.  I had my specs up earlier but deleted them because no one was answering.

If you already have Ubuntu installed, you do not need to reinstall Ubuntu Studio!

All of the ubuntu-studio applications can be easily installed using your choice of Synaptic,command line, or Ubuntu Software Center.

---

### Post by cchhrriiss121212 on 2010-09-14
OK, if you are running Vista you should be fine.

Back to your question: a text-install.
First you should plan what you want to do with the OS. Are you going to dual boot Studio with Ubuntu and Windows?
If you have regular Ubuntu installed already, what you can do is upgrade it to Studio, which will be easier than installing another OS. 
Open synaptic package manager and search for ubuntu studio, then install the meta packages you want to use, so for audio work you install ubuntu studio-audio. You can also install the studio theme if you like the look of it.

---

### Post by distortedtempo on 2010-09-14
> **cchhrriiss121212 said:**
> OK, if you are running Vista you should be fine.

Back to your question: a text-install.
First you should plan what you want to do with the OS. Are you going to dual boot Studio with Ubuntu and Windows?
If you have regular Ubuntu installed already, what you can do is upgrade it to Studio, which will be easier than installing another OS. 
Open synaptic package manager and search for ubuntu studio, then install the meta packages you want to use, so for audio work you install ubuntu studio-audio. You can also install the studio theme if you like the look of it.
What I was wanting to do is just get rid of normal ubuntu and replace it with studio mainly. I'm a musician so it sounded right for me. I'm gonna use it for a youtube channel i'm gonna be running.

---

### Post by JK3mp on 2010-09-14
Why not just...

```
sudo apt-get install ubuntustudio-desktop
```

---

### Post by distortedtempo on 2010-09-14
> **JK3mp said:**
> Why not just...

```
sudo apt-get install ubuntustudio-desktop
```
Thanks man that saved me some trouble :D

---

