---
title: "WPA Enterprise, i need it, but wont know what it is lol"
date: 2007-10-31
forum: Networking &amp; Wireless
---

### Post by mattgaunt on 2007-10-31
Hey everyone

I have looked at the stickied thread but i dont understand why i need to do that plus have a few questions about that anyway

Basically to connect wirelessly at uni i need to use WPA

On the uni's site it gives me instructions and shows me a window like this

[CENTER][IMG]http://www.wireless.bris.ac.uk/gfx/ubuntu-eduroam/x3.png[/IMG][/CENTER]

Now what i really want is to just be able to install something that makes my ubuntu have that WPA Enterprise option.

I dont think the stickied how-to is for me (I could be wrong) because i use the wireless on my home network as well so it wont be WPA Enterprise all the time which the how-to looks like it sets up.

Any help, tips or anything would be great

Matt

---

### Post by Bliepo32 on 2007-10-31
After searching a while (I had once seen this thread and thought of it), I found this: [http://ubuntuforums.org/showthread.php?t=202834](http://ubuntuforums.org/showthread.php?t=202834)

---

### Post by mattgaunt on 2007-10-31
cheers for the help Bliepo, but that was the thread i had kinda hoped i wudnt hav to follow

Would love gnome-network-manager to work as shown above rather than code the wpa settings into the interface file

Gaunt

---

### Post by staticsage on 2007-10-31
That window is from NetworkManager. You should see that window by default when connecting to a network that requires that type of authentication. Do you see the network manager applet in your tray?

To install NetworkManager (it comes installed with Ubuntu):
Alt + F2 then enter gksudo apt-get install network-manager-gnome

What version of Ubuntu are you using?

---

### Post by mattgaunt on 2007-10-31
Im running ubuntu gutsy gibbon, i get a screen similar but i dont have the WPA Enterprise option on the drop down menu

Sorry didnt give that description in the first place

Gaunt

---

### Post by Colbrac on 2007-11-12
You only get this screen when you 'connect to other wireless network' or something like that. The dropdown list now has wpa-enterprise and wpa2-enterprise.

---

### Post by wieman01 on 2007-11-12
> **mattgaunt said:**
> Im running ubuntu gutsy gibbon, i get a screen similar but i dont have the WPA Enterprise option on the drop down menu

Sorry didnt give that description in the first place

Gaunt
If you don't happen to have that option, your wireless adapter or driver does not support WPA. What hardware have you got?

---

### Post by mattgaunt on 2007-11-12
Netgear MA521 PCMIA laptop card

Gaunt

---

### Post by wieman01 on 2007-11-13
> **mattgaunt said:**
> Netgear MA521 PCMIA laptop card

Gaunt
Do you happen to know what chipset it is?

---

### Post by mattgaunt on 2007-11-13
Sorry i havent got a clue what chip set it is - How wud i find out?

Gaunt

---

### Post by mattgaunt on 2007-11-22
i found out the chipset is a realtek RTL8180L - im sure this thread is dead by now but just thought id mention it

Gaunt

---

### Post by wieman01 on 2007-11-22
The thread is still alive, mate. Just post away. :-)

---

### Post by mattgaunt on 2007-11-22
lol cheers so how do i find out if my chipset supports WPA enterprise???

---

### Post by kevdog on 2007-11-22
Probably have to google around for it!

---

### Post by wieman01 on 2007-11-23
I suggest that you install [WICD]("http://wicd.sourceforge.net/features.php") as it support TTLS. If your driver supports it as well, WICD should do the job.

---

### Post by harrydb on 2008-02-26
See my post in this thread for a howto connecting to eduroam using the network manager applet:
[http://ubuntuforums.org/showthread.php?t=708148#post4410798](http://ubuntuforums.org/showthread.php?t=708148#post4410798)

---

