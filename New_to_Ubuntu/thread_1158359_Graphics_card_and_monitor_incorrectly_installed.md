---
title: "Graphics card and monitor incorrectly installed"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by ads98765 on 2009-05-13
Im abit new to this ubuntu so be nice

I am currrently running ubuntu 9.04 and struggling to install the ati repository much help need as i dont want to revert to windows

I am trying to install my ati radeon 9200se using the ati repository i previously entered a command into terminal (but i cant remember what it is now) and i think it displayed my graphics card drivers but it wasnt of ati? Also when using System>Preferences>Display my monitor is reading as a AOC 16" when its a 17" 

Mainly im just trying to install this repository so i can use the s video.

Ive downloaded the ati-driver-installer-8.28.8.run and in terminal used:

adam@adam-desktop:~$ sh ./ati-driver-installer-8.28.8.run
sh: Can't open ./ati-driver-installer-8.28.8.run
adam@adam-desktop:~$ 

as stated on the ati website

Any help apprciated

---

### Post by camper365 on 2009-05-13
>  adam@adam-desktop:~$ sh ./ati-driver-installer-8.28.8.run

Try:
```
./ati-driver-installer-8.28.8.run
```

---

### Post by aeiah on 2009-05-13
as a side note, you can see your previous terminal commands by cycling through them with the up arrow, or see all of them by typing 'history'. you can combine history with grep if you want to be specific. for a while i always forgot the command for restarted gdm so in a terminal id type
```

history | grep gdm

```

but anyway. what's stopping you using system > administration > hardware drivers? im unfamiliar with ati cards but i would have thought you could get the restricted drivers straight from there, unless your card is super new.

---

### Post by ads98765 on 2009-05-13
that reads no drivers are in use on this system not quite sure how that works

all im really after doing is getting my svideo out to work on my tv when i boot the computer up it works up until ubuntu logs on. cant understand why

---

### Post by Jazzy_Jeff on 2009-05-13
Have you tried to go to System > Administration > Hardware Drivers to see if it shows one for your card? If so just click on it and install it.

---

### Post by ads98765 on 2009-05-13
no when i go to that the window reads "no drivers are in use on this system" and the boxes are empty

---

### Post by Wa1k3rTXRang3r on 2009-05-13
if the drivers arent showing up then that means that there are non proprietary drivers already in use for that hardware.

i know this because my laptop has a ati video card and it runs just fine without any proprietary drivers activated for it

---

### Post by Jazzy_Jeff on 2009-05-13
I believe ATI stopped supporting a lot of their older cards recently. That may be why there are no options to choose from.

---

### Post by Wa1k3rTXRang3r on 2009-05-13
actually i had heard about that. how is your display working without the driver? if its ok i suggest just not worrying about it

---

### Post by MontelEdwards on 2009-05-13
> **camper365 said:**
> Try:
```
./ati-driver-installer-8.28.8.run
```
he'll probably need to sudo chmod a+x

---

### Post by Jazzy_Jeff on 2009-05-13
> **Wa1k3rTXRang3r said:**
> actually i had heard about that. how is your display working without the driver? if its ok i suggest just not worrying about it

He is trying to get other things to work is the problem.

---

