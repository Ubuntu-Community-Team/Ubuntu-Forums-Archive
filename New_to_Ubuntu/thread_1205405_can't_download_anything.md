---
title: "can't download anything?"
date: 2009-07-06
forum: New to Ubuntu
---

### Post by Marrkle on 2009-07-06
Okay, so I start off installing ubuntu (7.10, Gutsy Gibbon). 

I then try to install Java for Ubuntu. Then they tell me I cannot install via the add/remove applications program. I try to go to Software Sources and enable universe and multiverse, but I get this error: (Could not download all repository indexes) 

There are 2 repositories and the error message says 'The repository might be no longer available or could not be contacted because of network problems'.....

The two repositories are [http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/universe/binary-i386/Packages.gz:) 404 Not Found (IP: 91.189.88.45 80]

[http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/gutsy/multiverse/binary-i386/Packages.gz:) 404 Not Found (IP: 91.189.88.45 80]

I also can't download any apps from the add or remove program thing because the multiverse and universe installation doesn't work.

---

### Post by Merk42 on 2009-07-06
[Ubuntu 7.10 reaches end-of-life on April 18, 2009 ](http://www.ubuntu.com/news/ubuntu-7.10-eol)

Either get the latest LTS, 8.04, or the latest standard release, 9.04.

I'm not sure you can even upgrade from 7.10 - 8.04 anymore, so you may have to burn a CD/USB Stick.

---

### Post by Marrkle on 2009-07-06
Now what? Is there some way I can download 8.04 without a CD?

EDIT: Am now downloading 9.04 from the website.

---

### Post by Merk42 on 2009-07-06
Without a CD or USB Stick? I dont' believe so.
Check System > Administration > Software Sources

Go to updates tab and make sure Release Upgrade is set to either Normal Releases or Long Term Support Releases.


If that is the case and it still doesn't work you **may** be able to manually edit the sources list, by putting this in the terminal

sudo gedit /etc/apt/sources.list

change any instance of "gutsy" to "hardy" for 8.04 LTS or "jaunty" for 9.04
**I have not tried this so I do not know the repercussions**

---

### Post by SunnyRabbiera on 2009-07-06
Its possible to manually upgrade like that by changing the repositories from Gutsy to hardy, though not the best solution.
Your best bet is to get a burning disk

---

### Post by credobyte on 2009-07-06
> Okay, so I start off installing ubuntu (7.10, Gutsy Gibbon). 

Just curious, where did you get it ? 8-[ As previously said, Gusty is dead - download & install 8.04 LTS or 9.04 ( tough, soon to be replaced by Karmic ).

---

### Post by Marrkle on 2009-07-06
Okay, now I have Ubuntu 8.04 downloaded and on a CD-R drive, what do I do now? It doesn't seem to autorun.

---

### Post by sadaruwan12 on 2009-07-06
Well it's always better to do a clean install with your system 'cos to get the true raw power of the new release you need to get all the new stuff working properly for you. Do a nice clean install and use ext4 as your file system it's seems to make the new Ubuntu work much faster.

---

### Post by Marrkle on 2009-07-06
> **sadaruwan12 said:**
> Well it's always better to do a clean install with your system 'cos to get the true raw power of the new release you need to get all the new stuff working properly for you. Do a nice clean install and use ext4 as your file system it's seems to make the new Ubuntu work much faster.

What is a clean install, how do I do it, and what is ext4 and how do I use it?

also please help me with the 'bootparameters' thing.

---

### Post by sadaruwan12 on 2009-07-06
OK, Clean install means you re-install your full system from scratch and EXT4 is there in the system partitioning part where you'll asked witch file system you want to use.

Read this before you jump in : [http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04]("http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04")

---

### Post by Marrkle on 2009-07-06
> **sadaruwan12 said:**
> OK, Clean install means you re-install your full system from scratch and EXT4 is there in the system partitioning part where you'll asked witch file system you want to use.

Read this before you jump in : [http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04)


Sorry, I have 8.04

also can you help me with my BootParameters post thanks

---

### Post by sadaruwan12 on 2009-07-06
I've posted about that and like to know little bit more details what' happening when you try to boot the system from the CD.

---

### Post by Marrkle on 2009-07-06
Okay. When I don't press f12 the system automatically goes and boots from 7.10. 

So I press F12 and go to option 2. CD-ROM

It shows me the normal menu, try, install, check memory, check disk etc. 

So the first time I selected 'try' but it just hanged there and didn't move

So I read a help thread and it told me to change the quietsplash-- to noapic nolapic, acpi=off, irqpoll or lapic pci=routeirq

I changed to all four but nothing, I left out the quietsplash-- but still nothing...

---

### Post by sadaruwan12 on 2009-07-06
OK, Try this on the boot menu you'll see the options item on the bottom of your screen so press the relevant key to get a small pop up menu from that turn ACPI off and nopic well asnolapic 'cos some time when you do it from the CLI it doesn't work if it still getting stuck tell me. Oh and remember to go straight in to the install function.

---

### Post by Marrkle on 2009-07-06
> **sadaruwan12 said:**
> OK, Try this on the boot menu you'll see the options item on the bottom of your screen so press the relevant key to get a small pop up menu from that turn ACPI off and nopic well asnolapic 'cos some time when you do it from the CLI it doesn't work if it still getting stuck tell me. Oh and remember to go straight in to the install function.

I don't understand, can you rephrase?

and F2 goes to the boot menu and F12 goes to multi-boot config, F8 has options for safe mode/last known good config etc.

---

### Post by sadaruwan12 on 2009-07-06
OK, I replied your other thread so lets do this in one thread. does you get a pop or a progress bar titled Linux kernel loading or something equal to that.

---

### Post by Marrkle on 2009-07-06
> **sadaruwan12 said:**
> OK, I replied your other thread so lets do this in one thread. does you get a pop or a progress bar titled Linux kernel loading or something equal to that.

No, i get the menu

UBUNTU LOGO HERE

Try ubuntu
Install ubuntu
Check CD for errors
Check Memory

F1 for something, F2 for something, F3 for something...

There is no progress bar.

---

### Post by lisati on 2009-07-06
<aside>Link to other thread: [http://ubuntuforums.org/showthread.php?t=1205456](http://ubuntuforums.org/showthread.php?t=1205456) </aside>

What happens when you choose "Try Ubuntu"?

---

### Post by Marrkle on 2009-07-06
> **lisati said:**
> <aside>Link to other thread: [http://ubuntuforums.org/showthread.php?t=1205456](http://ubuntuforums.org/showthread.php?t=1205456) </aside>

What happens when you choose "Try Ubuntu"?

I press enter, the computer hangs... it just stays there... doing nothing.. come back in fifteen minutes and still on that menu screen with the try ubuntu option selected.

---

### Post by sadaruwan12 on 2009-07-06
It seems like your CD is getting stuck try to write another CD if you have one and use the lowest speed you can get on your CD writer. Like to know is your laptop is very new model or an old one.

---

### Post by Marrkle on 2009-07-06
> **sadaruwan12 said:**
> It seems like your CD is getting stuck try to write another CD if you have one and use the lowest speed you can get on your CD writer. Like to know is your laptop is very new model or an old one.

An old one. And my CD writer is the ubuntu default.

---

### Post by sadaruwan12 on 2009-07-06
That means your using Brasario as your CD writing software ok. Do this go to your System -> administration -> Software sources from there go to Update tab then tell me what is selected under the release upgrade heading. Change it to normal release.

---

### Post by Marrkle on 2009-07-06
> **sadaruwan12 said:**
> That means your using Brasario as your CD writing software ok. Do this go to your System -> administration -> Software sources from there go to Update tab then tell me what is selected under the release upgrade heading. Change it to normal release.
\
this is the problem i have [https://help.ubuntu.com/community/BootParameters](https://help.ubuntu.com/community/BootParameters)

---

### Post by sadaruwan12 on 2009-07-06
Try this, this will help you to upgrade your system to 8.04 with out a CD.

[http://www.ubuntugeek.com/upgrade-ubuntu-710-gutsy-gibbon-to-ubuntu-804-lts-hardy-heron-beta.html]("http://www.ubuntugeek.com/upgrade-ubuntu-710-gutsy-gibbon-to-ubuntu-804-lts-hardy-heron-beta.html")

---

### Post by Marrkle on 2009-07-06
> **sadaruwan12 said:**
> Try this, this will help you to upgrade your system to 8.04 with out a CD.

[http://www.ubuntugeek.com/upgrade-ubuntu-710-gutsy-gibbon-to-ubuntu-804-lts-hardy-heron-beta.html](http://www.ubuntugeek.com/upgrade-ubuntu-710-gutsy-gibbon-to-ubuntu-804-lts-hardy-heron-beta.html)

I tried that but Ubuntu doesn't support gutsy any more so i can't do that

EDIT: I think it works, give me a second

---

