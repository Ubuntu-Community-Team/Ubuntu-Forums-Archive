---
title: "Old Sound-card On Ubuntu 9.10 not coming up."
date: 2010-03-08
forum: New to Ubuntu
---

### Post by Aster-Phoenix on 2010-03-08
Hi. I recently got Ubuntu 9.10 and its been great, but today i found an old sound-card. Now usually I'd just toss it aside but this one had an old joystick plug in. And i happen to have a joystick and a game that would be awesome to have a joystick for.
So i pop open my PC and stick in the new sound card, start up linux and it boots up. And nothing about a sound card. I went to computer and found nothing. I went to BIOS when booting up but idk where i would see the soundcard. Why wont it see my new-old Soundcard?
I don't know much about it, it doesn't say anything about it on it, and again linux doesn't read it so i can't see anything about it.

---

### Post by marshmallow1304 on 2010-03-08
The first thing to do would be to check if it plays sound.  Also see the Hardware tab in System->Preferences->Sound.

---

### Post by Aster-Phoenix on 2010-03-08
> **marshmallow1304 said:**
> The first thing to do would be to check if it plays sound.
Well It doesn't have a place in which i would plug in sound like on other parts of my machine it has a small jack with the word "Phone" on it 2 line inputs and the joystick plugin

---

### Post by marshmallow1304 on 2010-03-08
I'm not sure then.  I'd just plug in the joystick and see if it works.

---

### Post by Aster-Phoenix on 2010-03-08
> **marshmallow1304 said:**
> I'm not sure then.  I'd just plug in the joystick and see if it works.
I did and it doesn't say a thing doesn't say "New hardware" or anything.

---

### Post by marshmallow1304 on 2010-03-08
> **Aster-Phoenix said:**
> I did and it doesn't say a thing doesn't say "New hardware" or anything.

It's not supposed to. ;)  

With the joystick attached, open a terminal and run
```
cat /dev/input/js0
```
If you see a bunch of symbols when you press buttons, the joystick is recognized.

---

### Post by Aster-Phoenix on 2010-03-08
> **marshmallow1304 said:**
> It's not supposed to. ;)  

With the joystick attached, open a terminal and run
```
cat /dev/input/js0
```If you see a bunch of symbols when you press buttons, the joystick is recognized.
It says this
```
ziggy@bear-desktop:~$ cat /dev/input/js0
cat: /dev/input/js0: No such file or directory

```

---

### Post by marshmallow1304 on 2010-03-08
I'm afraid I'm no expert on joysticks.  You might try [this howto]("http://ubuntuforums.org/showthread.php?t=338457"), or someone else may be able to help.

---

### Post by Aster-Phoenix on 2010-03-08
> **marshmallow1304 said:**
> I'm afraid I'm no expert on joysticks.  You might try [this howto]("http://ubuntuforums.org/showthread.php?t=338457"), or someone else may be able to help.
Alright, thanks.

---

