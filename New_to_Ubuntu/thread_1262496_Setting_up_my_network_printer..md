---
title: "Setting up my network printer."
date: 2009-09-09
forum: New to Ubuntu
---

### Post by Windows Nerd on 2009-09-09
Okay guys, today is the second day of school and already my Socials teacher is on me and assigned homework. I typed out my whole assignment, then went to print my document mindlessly without even thinking if I had set it up or not to print. Turns out not. I went through the setup started to add a new printer. It recognized my printer as a network printer, but then when it went to look for drivers, it found none with my model.

My model is a Brother MFC 7440N. I googled it to try and find some help, though the only thing I could find was a whole set of complicated instructions with CUPS and all that. 

I would like to set up printing, so I dont have to put it on a USB key and transfer it to a Windows machine *every *time. 

Scott

---

### Post by Windows Nerd on 2009-09-10
Bump

---

### Post by PunkLV on 2009-09-10
If I did get this right, try this:
[http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html](http://raldztech.blogspot.com/2005/12/share-windows-xp-printer-to-linux.html)

---

### Post by MrWES on 2009-09-10
> **Windows Nerd said:**
> Okay guys, today is the second day of school and already my Socials teacher is on me and assigned homework. I typed out my whole assignment, then went to print my document mindlessly without even thinking if I had set it up or not to print. Turns out not. I went through the setup started to add a new printer. It recognized my printer as a network printer, but then when it went to look for drivers, it found none with my model.

My model is a Brother MFC 7440N. I googled it to try and find some help, though the only thing I could find was a whole set of complicated instructions with CUPS and all that. 

I would like to set up printing, so I dont have to put it on a USB key and transfer it to a Windows machine *every *time. 

Scott

Try this web site:
[http://solutions.brother.com/linux/en_us/index.html]("http://solutions.brother.com/linux/en_us/index.html")

However, I didn't see your specific printer listed as supported. There were a couple close to your model number, and they may work.

Bill

Actually I now see the 7440N -- which may work.

---

### Post by Windows Nerd on 2009-09-10
> **MrWES said:**
> Try this web site:
[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)

However, I didn't see your specific printer listed as supported. There were a couple close to your model number, and they may work.

Bill

Actually I now see the 7440N -- which may work.

Do I get the cupswrapper driver .deb or LPR driver?

Scott

---

### Post by Windows Nerd on 2009-09-10
Okay, got the cupswrapper driver and installed it. Now in the printer setup it cannot see the printer at all (or any of my other windows machines for that matter). Additionally, my firefox updated itself, and I can no longer start it, both from the command line or GUI. My error message I get either way is (see attatchment):

Damn, and my system was doing so well beforehand...now it decides to be all Windows like on me and mess itself up.

Edit: I looked through the repositories and there was no drivers there for my model either. I should have installed it through the repos so it didnt mess up my system.. :(

Edit2: I fixed Firefox by simply logging out and back in

---

### Post by plucky on 2009-09-11
> **Windows Nerd said:**
> Do I get the cupswrapper driver .deb or LPR driver?

Scott

You need to install both the cupswrapper and LPR drivers.Follow the instructions given on the Brother Solutions website.

Good Luck

---

### Post by longtom on 2009-09-11
> **Windows Nerd said:**
> Okay, got the cupswrapper driver and installed it. Now in the printer setup it cannot see the printer at all (or any of my other windows machines for that matter). Additionally, my firefox updated itself, and I can no longer start it, both from the command line or GUI. My error message I get either way is (see attatchment):

Damn, and my system was doing so well beforehand...now it decides to be all Windows like on me and mess itself up.

Edit: I looked through the repositories and there was no drivers there for my model either. I should have installed it through the repos so it didnt mess up my system.. :(

Edit2: I fixed Firefox by simply logging out and back in

Interesting bat file on your desktop....

---

### Post by MrWES on 2009-09-11
heh..no doubt.

---

### Post by Windows Nerd on 2009-09-12
I keep it for when I need to teach my Windows-using friends just how easy it is to hack.
It is short...all it contains is three lines.

I installed both drivers now...lets see if it works...I hope.

Edit: It still wont work. Now my problem is when it searches for printers, it shows nothing. Before it would detect the printer. Now not so. Additionally, I cannot access any of the other Windows machines connected to my home network.

Scott

---

### Post by Windows Nerd on 2009-09-12
Sorry, the server just lagged real bad and made me post many times unnecessaryly. Oops :O (This post was a double post)

---

### Post by Windows Nerd on 2009-09-12
Okay, I got it to find my printer. But then how do I get it to use the new drivers I just installed? I can provide a PPD, select it from a database provided by the manufacturer, or search for a printer driver. Searching does nothing. In the database there is none for my model. And the drivers I downloaded were not a PPD. Any ideas?

Scott

---

### Post by Windows Nerd on 2009-09-12
Bump

---

### Post by Windows Nerd on 2009-09-12
Bump. Anyone?

---

### Post by plucky on 2009-09-13
This [link](http://solutions.brother.com/linux/en_us/instruction_prn1a.html) might help especially step 5a.


Good Luck

---

### Post by Windows Nerd on 2009-09-18
Sorry for taking so long to post, I have been extremely busy. I fixed my problem: I just needed the correct drivers for my model. Silly me, that solution required no knowledge of Linux, just Windows...

Thread now marked as solved.

Scott

---

