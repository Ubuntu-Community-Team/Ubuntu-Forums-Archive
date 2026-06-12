---
title: "Visual/Graphics Problem"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by andyzammy on 2010-02-22
Hi all again,

At least i think it is! I'm unable to select any Visual Effect (currently on none). When i try, it searches and can't find the drivers. I'm not sure if its a related problem or not, but Blender won't launch (either version), and when i try to launch SecondLife i get a "Window Creation Error".

I do know that this is the cause of a crash (the laptop overheated and didn't shutdown properly).

How do i fix what's been broken? Also, how do i check to find out what else might have been broken?

Thanks,
zammy

---

### Post by cariboo on 2010-02-23
Boot from the Live CD, and once at the desktop, open an Applications->Accessories->Terminal and type at the prompt:

```
sudo fsck -a /dev/sdb
```

Substitute your partition for the one in the above command.

---

### Post by andyzammy on 2010-02-23
> **cariboo907 said:**
> Boot from the Live CD, and once at the desktop, open an Applications->Accessories->Terminal and type at the prompt:

```
sudo fsck -a /dev/sdb
```

Substitute your partition for the one in the above command.

This is what happened:

```
fsck 1.41.3 (12-Oct-2008)
/dev/sda1: clean, 291870/14696448 files, 31841929/58771786 blocks
```

It didn't fix anything though.

---

### Post by thecliff on 2010-02-23
> **andyzammy said:**
> Hi all again,

At least i think it is! I'm unable to select any Visual Effect (currently on none). When i try, it searches and can't find the drivers. I'm not sure if its a related problem or not, but Blender won't launch (either version), and when i try to launch SecondLife i get a "Window Creation Error".

I do know that this is the cause of a crash (the laptop overheated and didn't shutdown properly).

How do i fix what's been broken? Also, how do i check to find out what else might have been broken?

Thanks,
zammy

Zammy, what graphics card do you have (make/model)?  Do you know if you have the open source or proprietary drivers installed for your card?

---

### Post by andyzammy on 2010-02-23
> **thecliff said:**
> Zammy, what graphics card do you have (make/model)?  Do you know if you have the open source or proprietary drivers installed for your card?

i have a GeForce 9600M GT nvidia card.

The driver i'm using for it is proprietary (version 180, recommended). It actually says "A different version of this driver is in use."

---

### Post by andyzammy on 2010-03-01
bump this please!

---

### Post by 3rdalbum on 2010-03-01
Did you manually install this driver? If you did, and you've had a kernel update since then, you will need to manually install the driver again.

---

### Post by andyzammy on 2010-03-01
> **3rdalbum said:**
> Did you manually install this driver? If you did, and you've had a kernel update since then, you will need to manually install the driver again.

i can't even remember how it obtained the new drivers. i don't even know what the manual install method is so i don't think i did that lol. Everything was automatic, it told me to select a driver when i first installed ubuntu (so i chose proprietary) and it notified me that a newer one was available automatically too.

does this message: "A different version of this driver is in use." matter at all? does it always say that when its using the driver?

---

### Post by tom.swartz07 on 2010-03-01
> **andyzammy said:**
> ..........

I do know that this is the cause of a crash (the laptop overheated and didn't shutdown properly).
......


This phrase is what gives me the most worry. Since the computer overheated and did not properly shut down when it happened, you might have serious hardware damage.

My one friend actually had his computer overheat and some of the soldering on the parts began to melt; the only way he realized something was wrong was when he walked in and saw smoke coming from a melted RAM card on the bottom of his laptop!


I dont think your case is as serious, but it actually might be true that you have some substantial heat damage. 
If everything else is fine, I wouldnt worry too too much about it. Just make sure that everything is backed up.

---

### Post by andyzammy on 2010-03-01
> **tom.swartz07 said:**
> This phrase is what gives me the most worry. Since the computer overheated and did not properly shut down when it happened, you might have serious hardware damage.

My one friend actually had his computer overheat and some of the soldering on the parts began to melt; the only way he realized something was wrong was when he walked in and saw smoke coming from a melted RAM card on the bottom of his laptop!


I dont think your case is as serious, but it actually might be true that you have some substantial heat damage. 
If everything else is fine, I wouldnt worry too too much about it. Just make sure that everything is backed up.

the laptop was sent for "repair" (fan was clogged), the cpu was changed. im confident there's no hw damage (i knew it was an overheating issue and excessively used the acpi -t command to keep track of temp.. though i don't know how close the thermister was to the cpu, it never read over ~110).

i haven't tried it yet but i'm guessing booting from the live cd will show me that visual effects will work.. i just don't want to have to reinstall ubuntu atm.. it feels like one of those "it should just work" problems and i haven't even found out the cause of it yet.

thanks for all the help so far!

---

### Post by andyzammy on 2010-03-04
bump please!

---

