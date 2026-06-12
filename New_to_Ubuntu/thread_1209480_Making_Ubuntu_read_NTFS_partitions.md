---
title: "Making Ubuntu read NTFS partitions?"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by FoxFireX on 2009-07-10
I would like my Ubuntu to be able to read my Windows partition, and be able to access all my docs and pics on windows and stuff. I know its possible I've done it before but I can't be bothered to try to figure it out again.. Is there a simple command I can put into the terminal that will install and it do all the dirty work for me?

---

### Post by LowSky on 2009-07-10
under synaptic search for ntfs-3g

---

### Post by FoxFireX on 2009-07-10
Thanks :D

---

### Post by Sef on 2009-07-10
Easier way to find NTFS-3g:

Applications > Accessories > Show: All Available Applications > Search: NTFS > tic the top box (NTFS Configuration Tool > click apply changes > click apply close

---

### Post by Troll_the_Great on 2009-07-10
> **FoxFireX said:**
>  Is there a simple command I can put into the terminal that will install and it do all the dirty work for me?

```
sudo apt-get install ntfs-config
```

---

### Post by kansasnoob on 2009-07-10
I always like to install ntfsprogs either from Synaptic or you can install using the terminal:

```
sudo apt-get install ntfsprogs
```

[http://man.linux-ntfs.org/](http://man.linux-ntfs.org/)

---

### Post by XCan on 2009-07-10
I don't know how I managed but when I installed Jaunty on a machine having XP already installed I could read the NTFS by default. The partitions belonging to XP showed up under "Places", and all I had to do was to click on them to mount.

---

### Post by random turnip on 2009-07-10
> **XCan said:**
> I don't know how I managed but when I installed Jaunty on a machine having XP already installed I could read the NTFS by default. The partitions belonging to XP showed up under "Places", and all I had to do was to click on them to mount.

Same here, it's just called "167GB storage" or something like that.

---

### Post by FoxFireX on 2009-07-10
Yeah, I can read them by auto sense ntfs was already install, I'm just having some mounting view probs tho it seems.

---

### Post by LewRockwell on 2009-07-10
> **FoxFireX said:**
> 

...

I know its possible I've done it before but I can't be bothered to try to figure it out again...

...



bother?

you're kidding, right?

YOU can't be bothered...but WE can?

what's that foul smell?

Hmmm...

.

---

### Post by FoxFireX on 2009-07-10
Well, If your smart enough to know immediately after reading the question, It wouldn't be bothersome to you, But if you have to think about it and figure it out for me, then yeah that would make me lazy.
I know I'm not smart enough to know how to do it right out of the top of my head, so I was asking somebody who knows how to do it to tell me how, I wasn't asking somebody to go through the trouble of figuring it out for me. After all it is a helping forum isint it? Quit trolling, It not like you even contributed to the question.

---

### Post by LewRockwell on 2009-07-10
> **FoxFireX said:**
> Well, If your smart enough to know immediately after reading the question, It wouldn't be bothersome to you, But if you have to think about it and figure it out for me, then yeah that would make me lazy.
I know I'm not smart enough to know how to do it right out of the top of my head, so I was asking somebody who knows how to do it to tell me how, I wasn't asking somebody to go through the trouble of figuring it out for me. After all it is a helping forum isint it? Quit trolling, It not like you even contributed to the question.

then there's always this...

[http://www.doobybrain.com/2008/11/19/here-let-me-google-that-for-you/](http://www.doobybrain.com/2008/11/19/here-let-me-google-that-for-you/)

.

---

### Post by FoxFireX on 2009-07-10
I felt like interacting with somebody, chill out you'll be okay.

I figured I would of gotten a faster, more simple answer off here. After all most people enjoy helping people. I'm not hurting anything by asking a question. Sure I could google every question I have, But sometimes its easier and faster for me to just ask somebody and get a quick simple basic answer.

And if you are trying to really be a smartass, you could of used "letmegooglethatforyou.com".

kthxbai.

PS: if anything I'm contributing to google, by asking this question. :)

If I wanted to spend time search google I wouldn't of posted here.

---

