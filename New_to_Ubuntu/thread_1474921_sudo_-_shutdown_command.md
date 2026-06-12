---
title: "sudo - shutdown command"
date: 2010-05-06
forum: New to Ubuntu
---

### Post by Kapser on 2010-05-06
I tried "sudo shutdown +100" to shut it down in an hour forty.When i woke up the next morning I saw the shutdown screen and the ubuntu sign.So i persisted and tried again (with +1). Basically my computer started to go off and the ubuntu purple screen with it's logo came, this lead me to believe that it was going off but instead it just stopped at that purple screen. 

So does this happen with you to on Lucid ? Or is there any way to rectify it ?

---

### Post by spiky001 on 2010-05-06
have you tried seting a time ie 19.10 see what happens

---

### Post by QLee on 2010-05-06
> **Kapser said:**
> I tried "sudo shutdown +100" to shut it down in an hour forty.When i woke up the next morning I saw the shutdown screen and the ubuntu sign.So i persisted and tried again (with +1). Basically my computer started to go off and the ubuntu purple screen with it's logo came, this lead me to believe that it was going off but instead it just stopped at that purple screen. 

So does this happen with you to on Lucid ? Or is there any way to rectify it ?

Perhaps you want your system to halt (-h or maybe -H), you can read about the shutdown command if you enter man shutdown in a terminal, that will bring up the manual page for the command, shutdown.

---

### Post by dracayr on 2010-05-06
yep, it's shutdown -h to halt. ("sudo shutdown -h now" to shutdown the computer at that moment)

dracayr

---

### Post by Kapser on 2010-05-07
Works perfectly with -h, thanks. 
But for curiosity's sake whats the other command suppose to do then ? (without -h, just given a particular time i.e +200)

---

### Post by Mustard on 2010-05-07
> **Kapser said:**
> Works perfectly with -h, thanks. 
But for curiosity's sake whats the other command suppose to do then ? (without -h, just given a particular time i.e +200)

I'm guessing it drops to another init level, or single user mode or such. :)

I havent read the manual in a while.

---

### Post by bredman on 2010-05-07
Confirmed the initial post. shutdown +1 waits 60 seconds, tries to halt, and gets stuck at a purple screen.

init 0 seems to work OK. You could try the following command to die in 5 minutes
sleep $((5*60); init 0

Because init 0 needs sudo, you will need to put this command into a script and use sudo to launch the script.

---

### Post by r-senior on 2010-05-07
Wouldn't it be easier just to use shutdown -h +5 or shutdown -P +5?

---

### Post by bredman on 2010-05-07
I experimented a bit with
shutdown +1 
 shutdown -h +1 
 shutdown -H +1 
shutdown -P +1 

It seems that -H brings you to the purple screen, -P powers off, and -h is system dependent.

The manpage does not say what happens if no option is specified, but from my experiments, it may be that -h or -H is the default.

---

### Post by bredman on 2010-05-07
Just noticed in post 5 that on Kapser's system, the system-dependent -h is equivalent to -P, while on my system, the system-dependent -h is equivalent to -H.

To answer the question in post 5, this means that shutdown +1 must be equivalent to shutdown -H +1

---

### Post by r-senior on 2010-05-07
> **bredman said:**
> 
It seems that -H brings you to the purple screen, -P powers off, and -h is system dependent.
If the splash screen, etc. was turned off, you'd probably find a message at the bottom that says "System Halted". Certainly in my early days of Linux boxes (c. 1996) I recall systems doing this and you had to press the button to cut the power or do a warm boot.

Good detective work. =D> As you say, the manual page doesn't describe what shutdown does with no parameters.

---

