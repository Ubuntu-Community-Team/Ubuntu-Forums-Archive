---
title: "How to install linksys wireless-g pci adapter with speedbooster"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by JustLikeJsh on 2007-11-20
OK. i am finally on here posting from Ubuntu 7.10 Gutsy Gibbon. I figured out how to get my wireless card to work. It was so simple after i found this post. [http://ubuntuforums.org/showthread.php?t=581406](http://ubuntuforums.org/showthread.php?t=581406)

The second post in that thread helped out %100. So incase there is anyone out there that cant figure out how to install there Linksys WIreless-G PCI Adapter with Speedbooster. Model number WMP54GS. And i think this can actually work with Broadcom 43xx chipsets. So here it is.

Download these two files. [http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb](http://us.archive.ubuntu.com/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb) "and" [http://xeve.de/down/wl_apsta.o](http://xeve.de/down/wl_apsta.o) and burn to a cd. I did it in WIndows XP. For some reason i just couldn't get it to work on Vista but you might have better luck.

After you have your cd. Boot up Ubuntu 7.10 and mount the cd. It should mount by itself. Then double click on the mounted cd and double click on the bcm43xx-fwcutter_006-3_i386.deb file and something should pop up to install it. After that is done then go to System>Administrator>Ristricted Drivers Manager. Check the box to enable Firmware for Broadcom 43xx chipsets family. A small window should pop up. Now browse for the wl_apsta.o file and double click it and then click ok or whatever it says. Then go back to the Ristricted Drivers Manager and enable Firmware for Broadcom 43xx chipsets family. After it is enabled go to the top right and left click newtwork manager. And then click on your wireless connection. And that should be it. It took me awhile to get this but worth the wait. Gutsy Gibbon is the best.

---

### Post by JustLikeJsh on 2007-11-21
bump

so has this helped anyone? I hope it does.

---

### Post by JustLikeJsh on 2007-11-22
Im loving Ubuntu. Now i just got to learn how to get my iPod touch hooked up.

---

### Post by bromix on 2007-11-22
I'm confused, my Linksys wmp54 worked out of the box on Gutsy, even with WPA and TKIP.

---

### Post by JustLikeJsh on 2007-11-23
wmp54 or wmp54gs? becuase they're different and from what im seeing it makes a difference.

---

### Post by anilvjti on 2007-11-25
Thank you JustLikeJsh. It worked.

---

### Post by makksjuh on 2007-11-26
> **JustLikeJsh said:**
> bump

so has this helped anyone? I hope it does.
Thanks a lot! ... I had already ubuntu running on my notebook, but my desktop was still XP.


GREAT!!!:)

---

### Post by JustLikeJsh on 2007-11-26
> **makksjuh said:**
> Thanks a lot! ... I had already ubuntu running on my notebook, but my desktop was still XP.


GREAT!!!:)

No problem, glad i could help some of you so far.

---

### Post by javy29sp on 2007-11-27
Worked for me.  Thanks.

---

### Post by JustLikeJsh on 2007-11-28
no problem.

---

### Post by sappyrocks91 on 2007-12-02
I'm having a problem with the Wireless-G adapter as well.

I am a deffinate newb. I just had Ubuntu installed and I can't get my Linksys to work. 

The main router is connected to a computer that works with windows. 

I came in here and copied al the stuff I'd need for my static IP and it let the internet work for a second but it was really slow. Then it stoped working all together.

Any suggestions how I can get throught this pretty quickly?

---

### Post by Jake.P on 2007-12-22
worked for me! Thanks! the only thing stops me from using my ubuntu installation is solved!

---

### Post by fireboy129 on 2008-01-05
works for me!

to a point. now ubuntu wont even start up... o well.

[EDIT]

ubuntu works now. but sometimes my GUI freezes, which means that I have to redo everything... boo.

---

### Post by rustybronco on 2008-01-05
> **JustLikeJsh said:**
>  Linksys WIreless-G PCI Adapter with Speedbooster. Model number WMP54GS. And i think this can actually work with Broadcom 43xx chipsets.
would you post the output of lspci (just the chipset part) i'm looking to see if it's a 4318, 4306 ect... Thanks for the help in advance J-L-J

---

### Post by rustybronco on 2008-01-05
> **sappyrocks91 said:**
> I'm having a problem with the Wireless-G adapter as well.

His post is for a "gs"(with speed booster) not a wireless "g", do yourself a favor, open the terminal type in **lspci** and look for the chipset your device uses, or look on the bottom of the nic and get the model number and version then do a search for either of the two.
read kevdog's in my signature it will enlighten you further.

---

### Post by nusigmaforce on 2008-01-05
JustLikeJsh, you are the best!!!!!

This is the first time WMP54GS worked. Thank you!!!

---

### Post by nick p on 2008-02-05
WOW, OP, That worked flawlessly. THanks!!  :)  :guitar:

---

### Post by pamepros on 2008-02-13
I tried with those 2 files but I can´t make it work. I install the .deb but it automatically looks for the other file in the website instead of letting me look for it. 
Because of that it never appears in Ristricted Drivers Manager.
HELP PLEASE!!!
thanks
Pam

---

