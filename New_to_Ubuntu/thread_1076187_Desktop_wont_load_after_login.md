---
title: "Desktop wont load after login"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by piroko on 2009-02-21
Hey, I got a fresh copy of Ubuntu 8.10, it installed fine, boots fine, but after I put in my login user / pass it just loads the desktop background and grinds to a halt, and my keyboard stops responding.

while booting a noticed an 'error' or a 'bug' message:
'... MP-BIOS BUG: 8254 Timer not connected to AO-IPC'
I have no idea what that means, I'm new to linux in general.

My computer is an Emachine T2245
Ram: 1.5GB
Motherboard: Not sure, it's an emachine, whatever it came with.
HDD: 80 GB

I've been looking through other posts; here's what I've tried:

1. I've tried going into the recovery mode and repairing packages and fixing the x server, no dice.

2. Tried changing the runlevels after reading up on them in the manual, so, 2 - 5

3. Brought up a root shell to try and manually have dpkg configure all the packages just in case the recovery mode wasn't getting all of them.


Help much appreciated, I'd like to start learning how to use linux asap.
Thanks for the help anyone who responds.

(Sidenote: I'm using firefox on ubuntu right now only because I brought up the install menu and found out i could click the 'release notes' button and get a browser open)

--piro

---

### Post by piroko on 2009-02-21
...anyone?


bump

---

### Post by piroko on 2009-02-21
bump for help

---

### Post by Omegaxis on 2009-02-21
When you boot your computer you'll see a screen that says Grub loading.
Press the ESC (escape) key when you see it. You'll then want to find your version of ubuntu (usually the first one), scroll down to it and press "c".

This will get you to the command line. 
type this:

```
noapic
```

return to the previous menu and press enter.

also report back with the results.
> **piroko said:**
> 
(Sidenote: I'm using firefox on ubuntu right now only because I brought up the install menu and found out i could click the 'release notes' button and get a browser open)


Well, I learned something today! I had no idea you could do that.

---

### Post by piroko on 2009-02-21
> **Omegaxis said:**
> When you boot your computer you'll see a screen that says Grub loading.
Press the ESC (escape) key when you see it. You'll then want to find your version of ubuntu (usually the first one), scroll down to it and press "c".

This will get you to the command line. 
type this:

```
noapic
```

return to the previous menu and press enter.

also report back with the results.


Well, I learned something today! I had no idea you could do that.

Thaaank you omega, I've been waiting for an answer for almsot an hour and a half now. TYVM. :]

---

### Post by piroko on 2009-02-21
> **piroko said:**
> Thaaank you omega, I've been waiting for an answer for almsot an hour and a half now. TYVM. :]

Mmk omega, it says that I need to enter a certain string selected off of the TAB menu selections. I didnt write them down cause theres a lot of them, but there's no 'noapic' listed. The only way I can think to do that is to test it runing off the live cd, which I did before.
Testing the noapic setting gave me the same result. Also just tried logging into the failsafe GNOME setting, same error.

---

### Post by piroko on 2009-02-21
bamp]

---

