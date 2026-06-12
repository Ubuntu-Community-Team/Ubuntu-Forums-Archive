---
title: "windows98 replacment"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by jirugi on 2009-08-25
I have 4 very old Siemens PCs that were donated to this school in Uganda. They all have 200Mhz Intel Pentium w/MMX processors with 64Mb ram and 1 or 2 Gb hard drives. Currently they either have windows 2000 or 98 on them and the ones with 2Gb harddrives have Office on them. I would like to put Ubuntu on them but found out it requires higher specs than what they have. I was hoping to put Openoffice on as well instead of Office. I had a look at the required spec for windows 98 which can run on a 66Mhz machine (with 16Mb RAM I think). The machines are mostly used for email.
Is there a REALLY light version of Linux I can run on a 200mhz machine?
 
thanks

---

### Post by Hogosha on 2009-08-25
there is always DSL (Damn Small Linux)

That is about as light as it gets

---

### Post by gordintoronto on 2009-08-25
> **jirugi said:**
> I have 4 very old Siemens PCs that were donated to this school in Uganda. They all have 200Mhz Intel Pentium w/MMX processors with 64Mb ram and 1 or 2 Gb hard drives. Currently they either have windows 2000 or 98 on them and the ones with 2Gb harddrives have Office on them. I would like to put Ubuntu on them but found out it requires higher specs than what they have. I was hoping to put Openoffice on as well instead of Office. I had a look at the required spec for windows 98 which can run on a 66Mhz machine (with 16Mb RAM I think). The machines are mostly used for email.
Is there a REALLY light version of Linux I can run on a 200mhz machine?
 
thanks

The memory is more of an issue than the CPU speed.  I have a similar machine, and after many failures I intend to try Damn Small Linux on it.  However, I think Open Office will not run on a system with 64 MB. [http://www.damnsmalllinux.org/](http://www.damnsmalllinux.org/)

---

### Post by MrWES on 2009-08-25
> **jirugi said:**
> I have 4 very old Siemens PCs that were donated to this school in Uganda. They all have 200Mhz Intel Pentium w/MMX processors with 64Mb ram and 1 or 2 Gb hard drives. Currently they either have windows 2000 or 98 on them and the ones with 2Gb harddrives have Office on them. I would like to put Ubuntu on them but found out it requires higher specs than what they have. I was hoping to put Openoffice on as well instead of Office. I had a look at the required spec for windows 98 which can run on a 66Mhz machine (with 16Mb RAM I think). The machines are mostly used for email.
Is there a REALLY light version of Linux I can run on a 200mhz machine?
 
thanks

A barebones Puppy Linux might work on that amount of RAM:
[http://pupweb.org/wikka/BareBones]("http://pupweb.org/wikka/BareBones")

~Bill

Edit: It appears the download links are broken; I'm looking around now for a copy.
[http://mymirrors.homelinux.org/puppy/]("http://mymirrors.homelinux.org/puppy/")

---

### Post by Hogosha on 2009-08-25
i am currently making a virtual machine with those specs to see if open office will run on that.

I will post results

---

### Post by alexlafreniere on 2009-08-25
I would try CrunchBang Linux - based on Ubuntu, but with just about the lightest desktop environment you're going to find, Openbox. It comes with all the same software as Ubuntu as well. Give it a shot, if not go for DSL as was mentioned.

---

### Post by nikhilbhardwaj on 2009-08-25
there's slitaz [http://www.slitaz.org/en/](http://www.slitaz.org/en/)
and open office runs on this too

its iso is only 30 mb

---

### Post by halitech on 2009-08-25
couple of questions, do they have cdroms? or do you have at least 1 you can transfer between machines to do the installs? Do they have PS/2 keyboard and mice connections or are they the old serial mouse and AT style keyboards? do they have NICs installed and are they PCI or ISA boards?

Depending on the answers, might be easier to slap a copy of Win98 on all of them (I know its outdated but sometimes you have to do what you have to do)

---

### Post by Hogosha on 2009-08-25
yeah, the new versions of open office are not going to run on 64mb of ram. there are other options out there for office apps, DSL does come with a few apps that are downloadable, nothing like open office unfortunately.

---

### Post by snowpine on 2009-08-25
Crunchbang isn't going to work on there, but SliTaz would be a good choice. Be sure to use the SliTaz 'loram' flavor to install. Openoffice might not work, but a lighter alternative is Abiword (word processor) and Gnumeric (spreadsheet). Other popular options for old computers are DSL and Puppy. An even lighter alternative is Deli linux... it is kind of a unique distro, very light.

---

### Post by theozzlives on 2009-08-25
I'd say if their ATX Clones, just get a MOBO, CPU, RAM. Not that expensive and a lot less headaches. I just upgraded my Celeron 500 MHz w/256 MB RAM and SIS video to an AMD Dual Core 2.9 GHz AM3 w/1 GB RAM and NVIDA Video for less than $200.00.

---

### Post by MrWES on 2009-08-25
> **Hogosha said:**
> i am currently making a virtual machine with those specs to see if open office will run on that.

I will post results

Barebones puppy linux 2.01 will run with 64mb, but it doesn't have open office nor Abiword.

Bill

---

### Post by benj1 on 2009-08-25
> **Hogosha said:**
> yeah, the new versions of open office are not going to run on 64mb of ram. there are other options out there for office apps, DSL does come with a few apps that are downloadable, nothing like open office unfortunately.

dsl is based on debian, you can upgrade it to a full debian installation.


i would probably go with dsl then install the stuff from the debian repos that you need, or install debian with a lightweight window manager etc.

re open office, i would be highly suprised if open office worked on 64mb ram, its slow to load on my 500mb ram laptop. why not abiword, personally i havent had any problems with reading .doc files.

what will the word processor, and the computer be used for? is office compatibility important ?
EDIT: just read your post properly, if they are to be used mainly for email, why do you need an office suite at all? perhaps just a lightweight word processor (ted ?)

---

### Post by Mark Phelps on 2009-08-25
While I know the general feeling is that Linux will run on anything, especially "older" machines, what that really means is that "some version of Linux" is likely to be usable on any machine.

And, given the resource limitations of your machines, the Linux version that will install and run will likely present a very different "Linux experience" that what you're expecting from something like Ubuntu or OpenSuse or Mint or any other of the more modern distros.

I did exactly the same thing with a 10-year old laptop running XP (upgraded from Win 98), and the experience was so bad that the person using it insisted on my putting XP back on.

I'm just saying "Don't get your hopes up".

---

### Post by lykwydchykyn on 2009-08-25
There seem to be two kinds of "lightweight" distros out there.

 - Distros that take a general use distribution like Ubuntu or Debian, strip out the applications and desktop environment and replace them with "lighter" alternatives, generally from the default repos.

 - Distros actually built from the ground up to be lightweight and suitable for very old computers.

DSL and DeliLinux are the latter, and some other distros people have mentioned may also be.  Stuff like crunchbang, antiX, and any of the "*buntu's" are going to be the former. 

Probably the key thing to look for is the kernel version.  If it's got a 2.4 kernel, it's probably the second sort, and will do well on Pentium or Pentium II era computers.

> 
dsl is based on debian, you can upgrade it to a full debian installation.

It's worth pointing out that dsl is based on debian WOODY, which was released in 2002 and ended support in 2006.  If one wanted to go this route it'd probably be cleaner and simpler just to get a debian woody CD from the archives.

---

### Post by jirugi on 2009-08-26
Thank you all so very much for your input. I think I'll just stick with Windows. Someone said something about expectations of Linux and that's true here. I was hoping to get something that would make them a bit faster. I was very surprised to see how fast excel and the like open on these machines. 
 To answer some peoples questions. They are ATX format but we are a days journey to the nearest town that would have components and even then you'er paying 4 times the price for them.
 They have CDrom drives, flopy dives and even 2 USB ports.
These machines have been donated to the hospital school where they'll be used to teach things like Word, spreadsheets and database entry. I'm sure they'er very greatfull for any donation but it's like, whats the point in dummping our junk on third world countries. These things should relly be melted down.
 The MAIN problem here is the internet connection which is PAINFULLY slow... if it works.(It's taken me over an hour to get on this forum) and hence one pely to all.

Thanks again

---

### Post by Mark Phelps on 2009-08-26
> **jirugi said:**
> These things should relly be melted down.

Actually, ironic that you mention this because there are companies that actually do this.  They strip PCs of connectors and cards and melt then down for the gold in the connectors.  Lucrative business, as I understand.  Of course, you have to do TONS of this to make any real money.

---

