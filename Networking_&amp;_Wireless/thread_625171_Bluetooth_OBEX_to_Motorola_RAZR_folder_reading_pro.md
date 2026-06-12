---
title: "Bluetooth OBEX to Motorola RAZR folder reading problem"
date: 2007-11-27
forum: Networking &amp; Wireless
---

### Post by Gyatak on 2007-11-27
I'm having a funny problem with Bluetooth/Obex file transfers on Gutsy with my Motorola RAZR. When I connect to my RAZR, I see the various folders, but I'm not able to open them. They appear as files in the OBEX File Transfer window. When I click to open them, I'm asked what application I'd like to use.

Strange.

This was all working fine on Feisty, and I was able to view all stored files on my RAZR from my laptop (Dell Inspiron 9400). Maybe I'm missing a critical piece of software?

Any ideas?

---

### Post by trepid666 on 2007-12-01
Hey there. I am just curious if u tried to run these programs using "sudo"?

U must be root inorder to write right?

---

### Post by Gyatak on 2007-12-10
> **trepid666 said:**
> Hey there. I am just curious if u tried to run these programs using "sudo"?

U must be root inorder to write right?

That doesn't seem to be the problem. I've noticed that Gutsy's Dolphin is able to interpret these items as folders correctly. It's something about the way Konqueror is seeing them.

Any ideas where to look?

---

### Post by andrewoftheelves on 2007-12-20
i have a dell inspiron 9400 with gutsy as well, and i cant get bluetooth to work at all, i dont even know how to turn it on. any help would be appreciated(because it sounds like your farther along on this problem than i am)

---

### Post by Gyatak on 2007-12-20
One thing I found is that everything got much better on my Inspiron 9400 when I ditched KDE and switched to Gnome. Bluetooth, wifi, compiz, AWN--all lost 95% of their problems in the Gnome environment.

What are you running?

---

### Post by andrewoftheelves on 2007-12-20
haha gnome, but i i dont think the bluetooth hardware in my computer is on because the bluetooth icon isnt on, do you know how to switch that on?

---

### Post by Gyatak on 2007-12-20
I must start by saying I'm somewhat new to Ubuntu myself, but here's what I'd do:

Open Synaptic (under System > Administration), and search for bluetooth utilities. You want to find the Bluetooth Manager, and make sure it is installed.

After installing, restart and if the Bluetooth icon doesn't appear in your system tray, try finding the Bluetooth manager in the Applications or System menu and open it. 

However, I seem to remember going through something else to get it recognize the hardware. Wish I could remember what it is. Is the blue Bluetooth light on above the keyboard?

---

### Post by andrewoftheelves on 2007-12-26
no the blue light is not on. i just downloaded bluetooth obex. but i cant get it to recognise the hardware yet, but im fiddeling with it

---

### Post by -dp- on 2007-12-27
Hi guys, also having issues with my connection to mobile phone (see post: [http://ubuntuforums.org/showthread.php?p=4021355#post4021355](http://ubuntuforums.org/showthread.php?p=4021355#post4021355))

I will check the above in anycase as I don't see a bluetooth icon in the system tray.

---

