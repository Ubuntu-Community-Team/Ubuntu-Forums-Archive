---
title: "How do you make .ISO disks from driver CD's?"
date: 2010-04-20
forum: New to Ubuntu
---

### Post by suomalainen on 2010-04-20
Ubunteros,

I got a few cd's that I received when purchasing things like webcams or other PC related hardware. Obviously, many contain the drivers needed to make the hardware work.

Could someone suggest a good way to make .ISO copies of these disks/CD's so I can store them on my hard drive?

Thank you!!!!

---

### Post by egalvan on 2010-04-20
Since the software and drivers are probably Windows-oriented,
I would suggest using imgburn under Windows to make an iso
It's what I use, and it works great.
iso -> cd
cd -> iso
(I also donate to the authors.)

imgburn.com


But if what you need is to store the driversas iso files, then someone else will have to chime in...
the Linux software exists (there is even a command-line one) but I don't use it, so I don't know it.

---

### Post by Bachstelze on 2010-04-20
Open a terminal and do

```
dd if=/dev/cdrom of=image.iso
```

It will save an ISO file as image.iso in the current directory. Of course, you can change the name of the saved ISO...

---

### Post by freesitebuilder on 2010-04-20
If they are for Windows, they won't work in Ubuntu - you may have drivers installed already for some hardware, or you may need to install the Linux versions. This is the hardware info section
[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

Is that what you mean?

---

### Post by candtalan on 2010-04-20
Welcome!
If you copy the cd to a 'file' rather than to another cd, I think you will find that what has been saved is an image, which I think is iso (?)

Maybe the option to save to file might need a setting, not sure. Also, there is more than one cd copier, so if one does not have the facility you want, look (or ask) for others.

---

### Post by dwarfolo on 2010-04-20
On windows I would suggest InfraRecorder.
[http://infrarecorder.org/](http://infrarecorder.org/)

On Ubuntu I would suggest brasero.

---

### Post by coffeecat on 2010-04-20
Install the app k3b. From Tools menu > Copy. Then tick the 'only create image' box under settings.

---

### Post by suomalainen on 2010-04-20
Hi all,

What I'm looking to do and what I would like to do is take a CD and/or DVD, place it into the CD/DVD drive and have a software program turn it into a .iso so that if I lose the original disk I have a backup that I can easily burn.

Does anyone know how to do this in Linux Ubuntu?????

Thank you

---

### Post by Dayofswords on 2010-04-20
do read Bachstelze post, it should do exactly what you want

---

### Post by suomalainen on 2010-04-20
Will this commmand:

dd if=/dev/cdrom of=image.iso

Also save to my desktop?

Thanks??

---

### Post by Didius Falco on 2010-04-20
Message #3 has the easiest answer:

```
dd if=/dev/cdrom of=cd.iso
```

---

### Post by coffeecat on 2010-04-20
> **suomalainen said:**
> 
What I'm looking to do and what I would like to do is take a CD and/or DVD, place it into the CD/DVD drive and have a software program turn it into a .iso so that if I lose the original disk I have a backup that I can easily burn.

Does anyone know how to do this in Linux Ubuntu?????

Yes. Read my last post. The one before yours.

**Edit:** in fact, as someone else has already pointed out, you can also do it with Brasero which will be already installed. Simply choose 'Disc copy' and the rest (to get an ISO) is trivially easy.

---

### Post by Didius Falco on 2010-04-20
> **suomalainen said:**
> Will this commmand:

dd if=/dev/cdrom of=image.iso

Also save to my desktop?

Thanks??

it will if you either:

A. Change to the Desktop in the Terminal before you start the command.

B. Include the path in the command; ie 

```
dd if=/dev/cdrom of=~/Desktop/cd.iso

```

---

### Post by suomalainen on 2010-04-20
EVERYONE!!!!!

YOu all have been great!!!! I already burned a couple of disks and it workd!!!

Brasero is great too!!!!

Thank you again for helping me out with all your expertise....

Much appreciated!!!!

---

