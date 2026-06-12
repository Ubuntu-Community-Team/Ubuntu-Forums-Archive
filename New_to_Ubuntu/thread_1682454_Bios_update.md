---
title: "Bios update"
date: 2011-02-05
forum: New to Ubuntu
---

### Post by AnnAni1234 on 2011-02-05
I have a dell inspiron 1525 there has been a bios update and i wanted to know how to install it.  I was hoping that it would help with my battery problem, the battery charges but when i boot the system i get a message that the battery isnt recognized by the system and it will not charge and if i unplug the ac adapter it will kill the system.

Ubuntu 10.10
dell inspiron 1525

---

### Post by taseedorf on 2011-02-05
BIOS updates can usually be installed via Windows through dell when you download it....otherwise, on occasion, you can do it through the bios and put the bios (.bin many times) on a flash drive

---

### Post by AnnAni1234 on 2011-02-05
i dont understand what you mean as to putting it on a usb i am all ubuntu and no windows anymore please help i am still learning about linux so i am a noob

---

### Post by jonnny_j22 on 2011-02-05
Flashing your bios is pretty much one of the most risk things you can do software wise with a pc. Things don't often go wrong, but if they do, you're kind of screwed - you basically end up with no bios, so the computer becomes useless. I know this sounds scarey, and to be honest the general rule of thumb is unless you need the update, then don't do it.

For example, samsung released 5 bios updates for my machine, all of which i ignored. the 5th one however meant that xbacklight would now work on my machine. So I gave it a couple of months (just to let any possible kinks get worked out of the release before doing it.


There are basically 2 ways of doing it. The first step for both is to download the .exe file this windows application will replace your bios rom.

You can then either install windows for a day on a bit of your hard drive, and install the update from there, 

Or the usb method which is basically install freedos to a usb key and use that to run the .exe file. (this is actually more complicated - see below - do not just make a usb key and try and run the .exe)
 
I personally feel that the windows install is the safer option if you go ahead and is the meathod I use. If you opt for the usb key I strongly recommend searching for a product specific guide - I remember when I was concidering a the freedos route reading about special configurations for my machine.

---

### Post by sidzen on 2011-02-05
Ignore the "dire" warnings and ***carefully*** follow instructions given [here]("http://manual.aptosid.com/en/bios-freedos-en.htm")
They're the best I've found on how to do what you ask.  
Best wishes!

EDIT:  I see the reference to "usb method" above

---

### Post by sidzen on 2011-02-05
> **AnnAni1234 said:**
>  . . .  i am all ubuntu and no windows anymore . . .

Be Pane-Free!

---

### Post by AnnAni1234 on 2011-02-16
i just looked at the website that you posted about the usb method and it seems too time consumeing i was thinking what if i used virtual box to install windows and the installed the bios update from there once done just simply remove the virtual section from virtual box and keep on using linux

---

### Post by QIII on 2011-02-16
I don't think the virtualbox method would work.

The OS is running in a virtual machine -- not on the actual machine.  I'm not sure you would have any bare metal contact with the motherboard.

Might work, but I doubt it.

---

### Post by Paqman on 2011-02-16
> **AnnAni1234 said:**
> what if i used virtual box to install windows and the installed the bios update from there once done just simply remove the virtual section from virtual box and keep on using linux

[LIST=1]
[*]I don't think that would work
[*]It would take just as long as installing Windows to a partition anyway
[/LIST]

---

