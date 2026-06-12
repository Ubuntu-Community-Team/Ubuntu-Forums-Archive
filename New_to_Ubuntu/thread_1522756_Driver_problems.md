---
title: "Driver problems"
date: 2010-07-02
forum: New to Ubuntu
---

### Post by dlanger on 2010-07-02
Alright hows it going people? Last week I "upgraded" To Linux Ubuntu from windows! So far it has been an interesting journey and I have enjoyed it a lot. But then It came time for me to start using wine which I have absolutely no experience with and I wanted to use it to run Warcraft 3. I went to a separate forum and it said that to start I had to go System > Administration > Hardware Drivers. hardware drivers window said No proprieatary drivers are in use on this system (there is a screenshot of this in the attachment please view) but I know I have the graphics cards for it because I ran Warcraft 3 on this computer when I had windows. ALSO I forgot what drivers I have so now I want to find out what drivers I am running and make it so they work and I have no idea what I'm talking about please help!](*,):-({|=[-o<
P.s. this is only problem 1 of 2 major problems that came up some time the other one is my sounds doesn't work what now?

---

### Post by QIII on 2010-07-02
Welcome to Ubuntu!

Could you tell us what GPU/card you are using?

Unfortunately, WINE is not a silver bullet.  Some things work well, others not so much.

---

### Post by dlanger on 2010-07-02
> **QIII said:**
> Welcome to Ubuntu!

Could you tell us what GPU/card you are using?

Unfortunately, WINE is not a silver bullet.  Some things work well, others not so much.

Thank you for starting to help. Okay well I would have told you that it's just I have no idea how to find out what my GPU/card I am using?

---

### Post by j.bell730 on 2010-07-02
Go to **Applications** > **Accessories** > **Terminal** and copy/paste this...
```
lspci | grep VGA
```
Post here what comes up after that.

---

### Post by dlanger on 2010-07-02
dan@dan-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
dan@dan-desktop:~$ 
Thats what came up.

---

### Post by arpanaut on 2010-07-02
> **dlanger said:**
> dan@dan-desktop:~$ lspci | grep VGA
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
dan@dan-desktop:~$ 
Thats what came up.

Yup!  ATI/AMD stopped providing drivers in Linux for those chips a while ago. I don't know how wine/games will work with the open-source drivers, I dumped my 9800 pro card a couple of years ago, but there are limited AGP cards available anymore... Good Luck!

---

### Post by dlanger on 2010-07-02
Question then A) What should I do know? B) If I got it to work with Warcraft 3 and World of Warcraft don't you guys think it would be possible to do it now with wine or is it that wine isn't compatible with those cards. If it isn't compatible what would you suggest?

---

### Post by QIII on 2010-07-02
A)  How old is your computer, and what would you be willing to spend on a  new card?  Any of the newer AMD/ATI "HD" cards will work with the  drivers available in the repos for your particular version.  I imagine  that you are running Lucid Lynx?  Sorry I don't have better news, but  your current card does not have driver support for the latest version of  XServer.

B) I don't think it is a matter of Wine working with the card, exactly.  Wine provides a compatibility layer for Windows programs to run in what is known as a "loop device" with a set of libraries that allow a Windows program to hook Windows APIs in a user space.  But it works through the X Server using wineserver.

I believe, then, that graphics rendering would still be dependent on a Linux driver.  Anyone can feel free to step in and correct me here.

---

### Post by dlanger on 2010-07-02
Wait so now I'm confused. I don't have a lot to spend and its in no way a new computer... What would I have to do fix this problem?

---

### Post by QIII on 2010-07-02
Effectively, you need a new ATI/AMD or nVidia graphics card that is supported with either company's latest drivers.

How fast you want it to play and what sort of graphics quality to want it to give will have to be the criteria you use to choose a model from low- to high-end.

---

### Post by dlanger on 2010-07-02
Is there a cheap in between end? what would you suggest. And in your own experience with a lot of work can my crappy out-of-date computer be upgraded by any means possible without throwing it in the trash?

---

### Post by QIII on 2010-07-02
Can you give me some specs on the old nag?

I've had good luck in the past nursing old computers along, but the deal here will be whether or not the mobo will work with one of the newer cards.  Many of them require at least a free PCIe slot, usually x16 if you are using a 64 bit system.  If your system is old and 32 bit, you may find a card that will work with the older 32 bit PCI slot.

Technology moves along.  I have the means and the time to stay state of the art, so I don't do much with the old "classics" these days.

So it would be tough to recommend anything without some technical specs on the mobo.

---

