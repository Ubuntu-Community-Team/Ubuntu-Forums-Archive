---
title: "Beginner trying to start a wireless network connection"
date: 2008-10-19
forum: Networking &amp; Wireless
---

### Post by pugnaciousmcgillycuddy on 2008-10-19
Hi all, new to the forum and new to Ubuntu as well.
I don't know too much about PC's nor Ubuntu.
Just installed it and it looks great except I have a major problem. I cannot connect to the internet with it, I can't figure out how to get my wireless connection established even though I have all my wireless details to hand.
Also I cannot find the start, run, or command prompt.
Basically I am lost trying to set up my wireless connection so I am posting this using Windows and opera but I would rather get up and running using Ubuntu.
Any help much appreciated although as I say, I  wouldn't be too PC literate (took me a while to figure out how to install from the ISO disc, so you probably know where I am coming from).
Thanks in advance....

---

### Post by pugnaciousmcgillycuddy on 2008-10-20
Any takers ... ? ?

---

### Post by melojo on 2008-10-20
Use the Terminal.

Applications-Accessories-terminal

are you able to hook up with a cable so you don't have to reboot back into windows?

In the terminal type lspci (this will list your pci dievices)

---

### Post by melojo on 2008-10-20
double posted

---

### Post by pugnaciousmcgillycuddy on 2008-10-21
Hi melojo,
I typed Ipsis into the terminal and just got an error message.
I forgot to mention that I am running Ubuntu from an external harddrive, would this be the cause of the problem do you think ?
Thanks,
Pug.
P.s. I installed some type of Broadcom driver for Ubuntu, don't know too much about drivers.

---

### Post by pugnaciousmcgillycuddy on 2008-10-21
> **melojo said:**
> Use the Terminal.

Applications-Accessories-terminal

are you able to hook up with a cable so you don't have to reboot back into windows?

In the terminal type lspci (this will list your pci dievices)
Sorry, I nearly forgot, I had hooked up and was connected fine using an RJ cable.
Thanks again.
Pug.

---

### Post by pugnaciousmcgillycuddy on 2008-10-21
> **pugnaciousmcgillycuddy said:**
> Sorry, I nearly forgot, I had hooked up and was connected fine using an RJ cable.
Thanks again.
Pug.
Sorry, making a mess of this, I mean I typed Ispci.

---

### Post by Ayuthia on 2008-10-21
> **pugnaciousmcgillycuddy said:**
> Sorry, making a mess of this, I mean I typed Ispci.

That first letter in lspci should be a lower case L instead of an I.  That is why it is not coming out right.

---

### Post by pugnaciousmcgillycuddy on 2008-10-21
Thanks, got it and am up and running.....
Pug

---

