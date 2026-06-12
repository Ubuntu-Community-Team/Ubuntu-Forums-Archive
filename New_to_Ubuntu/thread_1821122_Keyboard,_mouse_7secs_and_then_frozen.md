---
title: "Keyboard, mouse 7secs and then frozen"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by littlboz on 2011-08-08
Computer is a gateway model GT4016.

I go to login into ubuntu and I have 7seconds before the mouse and keyboard no longer work. I have once been able to fully login where I can see my desktop but then it quickly freezes.

I would like to be able to fix this problem without reinstalling ubuntu.

---

### Post by MG&amp;TL on 2011-08-08
Have you tried different Ubuntu desktops? Try 'Ubuntu classic' rather than Ubuntu-I suppose it's possible that your hardware isn't up to Unity, but doesn't tell you for some reason. Haven't a clue else :(

I know you don't want to do a reinstall, but often that is the only way. Buy a cheap USB hard drive, see if you can access your files from a file recovery tool or something like Puppy Linux, whack the files onto the hard drive, reinstall, reinstall files, done. If it works. Has it always done this, or just recently?

---

### Post by amjjawad on 2011-08-08
> **littlboz said:**
> Computer is a gateway model GT4016.

I go to login into ubuntu and I have 7seconds before the mouse and keyboard no longer work. I have once been able to fully login where I can see my desktop but then it quickly freezes.

I would like to be able to fix this problem without reinstalling ubuntu.

... and your Ubuntu is? what release is that? :)

Edit:
Please, list your hardware details.

---

### Post by littlboz on 2011-08-08
> **amjjawad said:**
> ... and your Ubuntu is? what release is that? :)

Edit:
Please, list your hardware details.

oops sorry, This is lucid linx 10.04

---

### Post by Noncon on 2011-08-08
It might be either the mouse or keyboard, or something else.  Try disconnecting one of them, and see if the other one freezes  Then repeat the process to try and isolate the problem.  

KJ

---

### Post by littlboz on 2011-08-08
> **Noncon said:**
> It might be either the mouse or keyboard, or something else.  Try disconnecting one of them, and see if the other one freezes  Then repeat the process to try and isolate the problem.  

KJ
Unplugged keyboard and then mouse. It still did not work on either try. I have had this problem for about 6 months and it randomly comes and goes but the coming is far to frequent.

---

### Post by amjjawad on 2011-08-08
> **littlboz said:**
> oops sorry, This is lucid linx 10.04

I might seem irreverent but I have a feeling which is telling me that it could be another issue and it's not your mouse and keyboard which are frozen but more preciously your screen.

Are you connected to the internet via Wireless Connection, Wired or both at the same time?

What type of mouse and keyboard do you have? PS2 or USB?

---

### Post by littlboz on 2011-08-08
> **amjjawad said:**
> I might seem irreverent but I have a feeling which is telling me that it could be another issue and it's not your mouse and keyboard which are frozen but more preciously your screen.

Are you connected to the internet via Wireless Connection, Wired or both at the same time?

What type of mouse and keyboard do you have? PS2 or USB?

I am connected to a wireless linksys router picked up by a wireless card inside the computer. My mouse is a USB my keyboard is a ps2. I will try it out with other keyboards and mouses.

---

### Post by littlboz on 2011-08-08
I have tried a different mouse and keyboard and shuffling various usb plugins around. I haven't touched the wireless card.

---

### Post by littlboz on 2011-08-08
Whew, it just started to work. My friend seems to have magic fingers. I was able to take a business card that I was working on gimp out and onto a usb drive so my heart is not thumping so hard. I rebooted and now it doesn't work :-/

---

### Post by amjjawad on 2011-08-08
Sorry, what is going on with you now?
You have tired different mouse and keyboard so does it work or it doesn't?

---

### Post by littlboz on 2011-08-08
> **amjjawad said:**
> Sorry, what is going on with you now?
You have tired different mouse and keyboard so does it work or it doesn't?
mmm...sorry I was not straightforward. It is still not working. The different mouse and keyboards still led to the computer freezing.

Occasionally it won't freeze and I had that chance to back up my current projects. It has worked 3 times today but I have rebooted numerous times so it isent that often.

I am going to bed, I won't respond for about another 12 hours. Thank you for you're help so far amjjawad.

---

### Post by amjjawad on 2011-08-09
Please, have a look at [**this**]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Keyboard+and+mouse+frozen+ubuntu+10.04&as_qdr=all&sa=Google+Search&lang=en#1083").
Hope you could find something helpful :)

You most welcome ;)

---

### Post by littlboz on 2011-08-09
> **amjjawad said:**
> Please, have a look at [**this**]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Keyboard+and+mouse+frozen+ubuntu+10.04&as_qdr=all&sa=Google+Search&lang=en#1083").
Hope you could find something helpful :)

You most welcome ;)

Your link doesn't seem to direct me anywhere. would you mind reposting it?

---

### Post by amjjawad on 2011-08-09
> **littlboz said:**
> Your link doesn't seem to direct me anywhere. would you mind reposting it?

Type: Keyboard and mouse frozen ubuntu 10.04
here: [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by MG&amp;TL on 2011-08-09
Agreed. Most useful. Thanks Amjjawad!

---

### Post by BigMamma on 2011-08-10
If your video chip is Intel, you might need to upgrade your xorg-xserver-video-intel package.   Following sections 2 and 3 of this solved the problem for me:
[http://olafsblog.sysbsb.de/solved-xserver-lock-ups-in-ubuntu-10-04-with-intel-gfx/](http://olafsblog.sysbsb.de/solved-xserver-lock-ups-in-ubuntu-10-04-with-intel-gfx/)

---

### Post by littlboz on 2011-08-16
> **amjjawad said:**
> Type: Keyboard and mouse frozen ubuntu 10.04
here: [http://www.googlubuntu.com/](http://www.googlubuntu.com/)

Sorry for the late response. The forum I found had some ideas that I did not understand and I did not have the time to play with them until now, mostly I had to work up some courage. The forum stated that noapic was a line that would fix my problem. [http://ubuntuforums.org/showthread.php?t=1480881](http://ubuntuforums.org/showthread.php?t=1480881)

(I added some pictures to offer clarity they are marked with *)
Anyways, I go to my booting up menu* and press "e" to "edit the commands before booting" *I then press control C and get a grub> line thing*. I type in noapic and unfortunately it says the command is unknown.



I am not giving up and I am excited to learn some of these new things...if all else I have finally come to terms that I may need to reinstall ubuntu.

---

