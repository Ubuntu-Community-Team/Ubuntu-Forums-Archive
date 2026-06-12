---
title: "Linksys wireless card not recognized...hmmm"
date: 2005-08-13
forum: Networking &amp; Wireless
---

### Post by Zarkoth on 2005-08-13
Hey there, I posted previously on this subject, but have made progress since then, and my thread is buried under mountains of other forgotten threads now, so I decided it would be good to make a fresh start here.

So here's the situation, I now have ndiswrapper 1.1 successfully installed, and as of now, it says "driver present" but not "hardware present" so what do I do to get it to recognize my card?

I have a Linksys Wireless-B PCI card, WMP11 V 2.7, and I'm attempting to connect to our linksys router which is running on an XP computer....the card and stuff worked when I had 98 installed on my comp, but since I switched to Ubuntu it's been quite a fight just to get this far.

Any help is very much appreciated, and thanks in advance.

---

### Post by pierreski on 2005-08-24
Hey there, I'm having the exact same problem with my WMP11 v2.7 PCI card.  I've searched the internet and found a few articles on using this card on linux/ubuntu.

I've searched the internet and found out that I should ndiswrapper an .INF file called BCMWL5.INF.  I also found out that this file can be found in a Compaq support file ("SP28538.exe").  I took the inf out of the compact and tried

sudo ndiswrapper -i bcmwl5.inf

The computer gave me a message about changing some sort of BG mode from 0 to 2 of something then I did

sudo ndsiwrapper -l

and I got the response

bcmwl5            invalid driver!

Please help someone!  I keep trying to use linux on my computer, but I keep giving up because I can't get WIFI to work!

---

### Post by ZBlach on 2005-08-24
I have that card too. I got around that error by using the drivers on the CD the card came with. 

I mean, those are the drivers for that specific card already, right?

WMP11V27.inf and .cab, i think.

-Z

---

### Post by pierreski on 2005-08-25
I'll give it a shot later this evening and write back if all goes well [-o<

---

### Post by pierreski on 2005-08-26
I tried 

ndiswrapper -i wmp11v27.inf

and I got

installing wmp11v27
Forcing parameter Radiostate|0 to Radiostate|1

When i tried ndiswrapper -l, I got

wmp11v27     invalid driver!

This is driving me nuts!
Every driver I install is invalid!!! Help!!!

---

### Post by hbweb500 on 2005-08-26
Have you tried including the .sys and/or .ini files too? A lot of times the .inf file just points to other files whihc actaully include the drivers.

I installed the bcmwl5.inf file as well, but when I extracted it, I put every other file in the archive into the same folder as the extracted driver, and it worked, whereas it didnt before.

---

### Post by ssck on 2005-08-26
[QUOTE=pierreski]I tried 

ndiswrapper -i wmp11v27.inf

and I got

installing wmp11v27
Forcing parameter Radiostate|0 to Radiostate|1

When i tried ndiswrapper -l, I got

wmp11v27     invalid driver!

This is driving me nuts!
Every driver I install is invalid!!! Help!!![/QUOTE]


make sure that you have all the files such as sys files, not just the inf file.

---

### Post by pierreski on 2005-08-26
:)   :)   :)   :)   :)   :) 

[SIZE=2]**Thank You so much!  That was brilliant!  Works great**[/SIZE]

---

