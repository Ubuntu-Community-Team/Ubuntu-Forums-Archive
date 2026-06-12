---
title: "Ubuntu Software Centre"
date: 2010-12-25
forum: New to Ubuntu
---

### Post by fin2010 on 2010-12-25
Hi i am completely new to ubuntu, been using it for a day now and its been fine up to now. I tried instaling a snes emulator on ubuntu software centre but its just got suck on applying changes, then i tried cancelling it and it got stuck on that. After restarting the laptop I tried again and had the same problem. 
Now I find that I cannot install or remove anything, it just says applying changes.
Any suggestions?
Thanks

---

### Post by matt_symes on 2010-12-25
Hi

Open a terminal and type

```
sudo apt-get install -f
```

Enter your password. You will not see it echoed to the screen. This is normal. Then try again. 

If that does not work try.

```
sudo dpkg --configure -a
```

Then

```
sudo apt-get update
```

Post any errors back here.

Kind regards

---

### Post by fin2010 on 2010-12-25
Thanks a lot , seemed to work. I tried removing a game and it worked. 
The problem started by trying to install a snes emulator, now after following your instructions and sorting the problem I thought  I would download another snes emulator , but it got stuck on 'applying changes' again lol so got to do the hole process again. 
Is there something wrong with snes emulators or is it me ?

---

### Post by matt_symes on 2010-12-25
Hi

> Is there something wrong with snes emulators or is it me ?

I have never tried the snes emulator so i don't know?

Maybe someone else here has used it and has some tip for the OP?

Kind regards

---

### Post by fin2010 on 2010-12-26
Been looking into some of the coding for the terminal and I managed to install the snes emulator throught terminal, worked 100% . 
Anyway thanks a lot for the help :KS

---

### Post by Peanuts123 on 2010-12-26
I had a problem with installing my first hours of using ubuntu. I tried to download everything I could get my mouse clicker on. Unfortunately it didnt happen because I had not installed the updates for most of the things I could download. Make sure you have these up to date.

---

