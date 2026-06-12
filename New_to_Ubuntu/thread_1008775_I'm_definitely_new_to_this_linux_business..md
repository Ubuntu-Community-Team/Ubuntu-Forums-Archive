---
title: "I'm definitely new to this linux business."
date: 2008-12-11
forum: New to Ubuntu
---

### Post by bozomcguirk on 2008-12-11
Umm I just installed Ubuntu and I am trying to get everything in working order. Thus far the only stuff that doesn't work is my laptop's built in card reader and my headphone jack.I have a fujitsu lifebook n3410.I basically have no clue what I am doing.

Flying by the seat of my pants

---

### Post by Kellemora on 2008-12-11
Hi BCQ

Welcome to the club):P, hi hi..........

Your card reader may require downloading the drivers for it.
As well as for your audio card.

In order for the guru's to give you some help here, there are a few things you will have to post for them to study.

It is courtesy to enclose the results of what you are asked by placing a bracket [ with the word Code inside] and my typing it this way may mess up this message, and then end the results with the a right slash and the word code inside of brackets.
I know that is confusing and I don't know how to show it, I'm a noob too!

```
But the box will look like this if done right
```

To get to the info required, you would type
```
sudo /etc/fstab
```
this will give your helper the file system info.

They may also ask for
```
lshw
``` and
```
lspci
```

Those messages are typed in the Terminal, so you might practice doing that so you will be ready when asked for same by one of the guru's that can help you.

Sorry, I'm not familiar enough with Ubuntu yet to help with your particular problem though.

Good Luck

TTUL
Gary

---

### Post by Nodnelg on 2008-12-11
> **bozomcguirk said:**
> Umm I just installed Ubuntu and I am trying to get everything in working order. Thus far the only stuff that doesn't work is my laptop's built in card reader and my headphone jack.I have a fujitsu lifebook n3410.I basically have no clue what I am doing.

Flying by the seat of my pants
Have you tried booting up the machine with a card in the card reader to see if that helps it be recognized by the system? I don't know if this will help or not but I have had problems with mass storage devices not being reccognized unless they were present during boot. Mind you this was on a different operating system, but I would try it if you have not already.

---

### Post by Moop on 2008-12-11
Go to System-Administration-Hardware Drivers and see if there are any drivers available to install.

---

### Post by bozomcguirk on 2008-12-13
Thanks for all the help I will give it shot.

---

