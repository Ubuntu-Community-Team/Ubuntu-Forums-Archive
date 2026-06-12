---
title: "no KB or Mouse"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by mayagrafix on 2010-05-14
Normal Boot does not work, when I get to log in screen no input from KB or Mouse available. 

Using the recovery mode menu, I can boot into the command line interface and use txt file and directory commands like ls and cd. 

However, when I execute Startx the GUI comes up on screen but the KB and Mouse cease to operate. 

If I boot using Live CD, everything works fine. 

Using 10.04 LTS

---

### Post by Black Hawk on 2010-05-14
Hi. I'm taking a shot in the dark here, but you could try this:

hal might not be started. hal is needed for KB and mouse to work in the gui ( or more precicly in X).
boot in recovery mode and type ```
 sudo start hal 
```
if it says start: Job is already running: hal. Then hal is already running an is'nt the cause of your truble if it says something different try running startx. If this works you'll need to investigate why hal doesn't start on bootup.

---

### Post by moep on 2010-05-14
Are you using a USB or PS2 Keyboard/Mouse? Is it a Desktop PC or Laptop? 

If it is a Desktop PC with USB keyboard you could try to plug in a PS/2 keyboard to debug the issue by checking if other USB devices work. Maybe you can also find something related in the logs.

---

### Post by mayagrafix on 2010-05-14
> **Black Hawk said:**
> Hi. I'm taking a shot in the dark here, but you could try this:

hal might not be started. hal is needed for KB and mouse to work in the gui ( or more precicly in X).
boot in recovery mode and type ```
 sudo start hal 
```
if it says start: Job is already running: hal. Then hal is already running an is'nt the cause of your truble if it says something different try running startx. If this works you'll need to investigate why hal doesn't start on bootup.

I get this message:
> ubuntu@ubuntu:~$ sudo start hal
**start: Unknown job: hal**
ubuntu@ubuntu:~$ 


I think along the same lines as you do, that the necessary services for the keyboard + mouse do NOT get loaded at boot time. Works mighty fine using LiveCD of 10.04. and keyboard works good at command line interface in recovery mode. When I tried to run 'hal' command in recovery mode I got the message reply of: Unknown command, and in LiveCD it says Unknown Job. Which I guess means that the command hal is no longer used in 10.04.

Is there any other way of starting USB keyboard  + mouse services from the command line?

Thanks to everyone for their help.

---

### Post by mayagrafix on 2010-05-14
> **moep said:**
> Are you using a USB or PS2 Keyboard/Mouse? Is it a Desktop PC or Laptop? 

If it is a Desktop PC with USB keyboard you could try to plug in a PS/2 keyboard to debug the issue by checking if other USB devices work. Maybe you can also find something related in the logs.

Thanks for the sugestion, but this Desktop has no PS/2 conection, only USB ports. My first instinct was to plug in another KB+mouse, but only USB ports available. 

The KB works fine when I use the recovery mode at the CLI level, and both the KB + Mouse work fine when I boot using LiveCD.

---

### Post by mayagrafix on 2010-05-14
Ich habe keine Verwendung von Tastatur und Maus beim Ubuntu anzumelden lila Bildschirm

---

