---
title: "radeon driver is frustrating me please help"
date: 2011-05-29
forum: New to Ubuntu
---

### Post by skilgannon82 on 2011-05-29
i have a radeon hd 6470m card and at first i had problems booting ubuntu it just went to a black screen and booted when it felt like it but that is not my problem now

now i have the ati proprietary driver installed and it boots fine it will not load unity anymore but thats not a problem but i cannot open catalyst control centre it says the ati is not running properly or not there at all

the problem is i want to run pyrit (not for illegal use) but to get the benefit of my graphics card it needs to use the catalyst control centre is there a way to fix this or does it mean i cannot use pyrit 

i have had nothing but problems with this card but i am a noob and most of the time have no idea what i am doing but im very sure i have done everything correctly for setting everything up 

if somebody has a solution please help

---

### Post by skilgannon82 on 2011-05-29
bump 

anybody?

---

### Post by skilgannon82 on 2011-05-29
bump again

---

### Post by skilgannon82 on 2011-05-29
buuuuump!

---

### Post by alphacrucis2 on 2011-05-29
> **skilgannon82 said:**
> bump again

I presume you installed the Catalyst driver via the additional drivers program? If so you could try the Catalyst 11.5 from AMD as I think the Ubuntu repo one is a pre release version. 

1. Download Linux driver (32 or 64 bit) from AMD website

2. then uninstall the existing Catalyst via

```
sudo apt-get remove --purge fglrx*
```

3. Then install the driver downloaded from AMD using the builpkg method as described in the ATI binary driver howto:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by Revender on 2011-05-29
[QUOTE=alphacrucis2]```
sudo apt-get remove --purge fglrx*
```[/QUOTE]

It worked for me.

---

### Post by skilgannon82 on 2011-06-08
i have followed the instructions completely but i am getting this error when trying to create the .deb package from my download 

sh: Can't open ati-driver-installer-11-2-x86.x86_64.run

it says its there on the desktop when i check with ls so i dont know what the problem is

---

### Post by skilgannon82 on 2011-06-08
bump

---

### Post by alphacrucis2 on 2011-06-08
> **skilgannon82 said:**
> i have followed the instructions completely but i am getting this error when trying to create the .deb package from my download 

sh: Can't open ati-driver-installer-11-2-x86.x86_64.run

it says its there on the desktop when i check with ls so i dont know what the problem is

The latest driver should be 11-5 not 11-2. 11-2 is just an example from the Howto. ie the latest installer should be ati-driver-installer-11-5-x86.x86_64.run

AMD release a Catalyst update every month. For example, the June one will be ati-driver-installer-11-6-x86.x86_64.run when it gets released later this month

---

### Post by skilgannon82 on 2011-06-08
ok i probably wasnt clear enough im following the instructions completely but using 11-5 instead of the 11-2 in the how to 
=) im a noob but not a total noob

---

### Post by skilgannon82 on 2011-06-08
i am a total noob sorry i see what i did now im using 11-5 but copied and pasted into terminal from the how to with the 11-2 script

---

