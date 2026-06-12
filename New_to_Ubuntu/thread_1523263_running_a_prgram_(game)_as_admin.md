---
title: "running a prgram (game) as admin"
date: 2010-07-03
forum: New to Ubuntu
---

### Post by etiennechausse on 2010-07-03
I have this game installed on Ubuntu which is just great, it is called Heroes of Newerth. However, whenever i click on the game shortcut it opens then closes automatically. It took me a while to understand that this game needed administrator permission to acces the graphic card. Whenever i run it in the terminal as admin

cd HoN
sudo ./HoN.sh

It works but it is anoying always having to go through the terminal to open it
it there a way to always open as admin one program without going through the terminal?

---

### Post by -humanaut- on 2010-07-03
Change the permissions on it so your "user" can run it open nautilus with alt+f2 gksu nautilus 

find the file right click and set the permissions You probably don't want to be running that game as root.

---

### Post by etiennechausse on 2010-07-03
> **-humanaut- said:**
> Change the permissions on it so your "user" can run it open nautilus with alt+f2 gksu nautilus 

find the file right click and set the permissions You probably don't want to be running that game as root.

when i right click on the file and click on properties/permissions
i only have these options
Owner
Acces
group
access
others
access
execute

---

### Post by lkjoel on 2010-07-03
Yes, it is quite possible to run it as root, without a terminal window open.
Type this in a terminal:
```
gedit HoN/RunHoN.sh
```I am assuming that the folder HoN does not have a RunHoN.sh already.
Then as a window pops up, type this in:
```
#!/bin/bash
gksu ./HoN.sh
```Save it then close.
Still in the terminal window, type this in:
```
cd HoN
chmod +x RunHoN.sh
```To run it, just double click on RunHoN.sh.

Just a question... Is it available from the synaptic?

---

### Post by etiennechausse on 2010-07-03
> **lkjoel said:**
> Yes, it is quite possible to run it as root, without a terminal window open.
Type this in a terminal:
```
gedit HoN/RunHoN.sh
```I am assuming that the folder HoN does not have a RunHoN.sh already.
Then as a window pops up, type this in:
```
#!/bin/bash
gksu ./HoN.sh
```Save it then close.
Still in the terminal window, type this in:
```
cd HoN
chmod +x RunHoN.sh
```To run it, just double click on RunHoN.sh.

Just a question... Is it available from the synaptic?

I dowbloaded it from the HoN website so i don't know
It was open beta for 6 months, but you now have to pay 30$ (1 time fee to play)

if you want to try i I had 2 beta keys so this one is yours
User: jaibob pass: 12345

It is open only for the weekend tho

I will tell you if running it as root worked ASAP, i am still trying to get my NVIDIA card back on ^^

---

### Post by lkjoel on 2010-07-03
> **etiennechausse said:**
> I dowbloaded it from the HoN website so i don't know
It was open beta for 6 months, but you now have to pay 30$ (1 time fee to play)

if you want to try i I had 2 beta keys so this one is yours
User: jaibob pass: 12345

It is open only for the weekend tho

I will tell you if running it as root worked ASAP, i am still trying to get my NVIDIA card back on ^^
Wow, thanks!
One question: what does ASAP mean?
Also, if openGL doesn't work, try MESA.
Though it is seriously slower, it is an alternative.
MESA is a software renderer.

---

### Post by lkjoel on 2010-07-03
EtienneChausse, I replied to Gedit doesn't recognize file:
[http://ubuntuforums.org/showthread.php?p=9542780#post9542780](http://ubuntuforums.org/showthread.php?p=9542780#post9542780)
So you may install your drivers correctly!

---

