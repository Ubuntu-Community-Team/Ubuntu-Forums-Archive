---
title: "backing up my many hours of work"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by madoldfart on 2009-05-11
1)Ok, i have now installed all the apps, themes, icons etc and have ubuntu running and looking just the way i like it on my dell inspirion 9400 laptop

I now want to copy/backup what i have done and install it on my daughters laptop so it looks and does the same things. 

Can it be done and how do you do it?

2) I am also looking at installing iDeneb v1.4 10.5.6 OSX86 onto my dell inspirion 9400 laptop and dual booting osx and ubuntu.
Im guessing that i will have to reformat my hard drive on my Dell, then install iDeneb v1.4 10.5.6 OSX86, then install ubuntu.

As i have spent many hours getting ubuntu personalized for me, when i reinstall ubuntu can i copy/backup/install something so it looks and does the same things.

Any advise to issue 2 appreciated as there may be a better way to install osx86 and ubuntu without having to reformat my drive and backup what i have already done in ubuntu.

Note: i do not want to backup any photo,music,office files,i just want to backup the apps installed and the themes,icons etc.

ps I am an absolute beginner and am enjoying the challenges and education on how to have a choice in which operating system i use. As i hate windows.

These forums are very very helpful and you guys are very very knowledgable.:)

---

### Post by logos34 on 2009-05-11
There's [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html")

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

---

### Post by madoldfart on 2009-05-11
> **logos34 said:**
> There's [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html")

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

Thankyou for the quick reply 5min amazing.
I have had a quick look at the links, it looks fairly straight foward even for a beginner. I will play around with this over the weekend. Hopefully my daughter and i will be dual booting in no time.

Thanks Heaps
Problem solved=D>

---

### Post by Ericyzfr1 on 2009-05-11
You might want to have a look at Clonezilla 1.2.2-2. Works very well with 904, saves partition  fast and file size is very reasonable.

---

### Post by logos34 on 2009-05-11
CLonzilla is a great app, as Ericyzfr1 suggested...the only problem is that it will make a perfect copy of your installation--your personal files and user account too, right down to same partition UUID.  Not sure if that's what you want, though, in light of what you said:

> **madoldfart said:**
> Note: i do not want to backup any photo,music,office files,i just want to backup the apps installed and the themes,icons etc.

unless you want to delete all those files afterward, change accounts, etc.  Might be a little faster though

---

### Post by madoldfart on 2009-05-11
is this the link
[http://freshmeat.net/projects/clonezilla](http://freshmeat.net/projects/clonezilla)
latest version is 1.2.2-13

and sorry for my ignorance what is 904

stupid me ive just realised 904 is jaunty - derr

---

### Post by ktrnka on 2009-05-11
> **logos34 said:**
> There's [Remastersys]("http://www.geekconnection.org/remastersys/remastersystool.html")

[http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html](http://www.ubuntugeek.com/creating-custom-ubuntu-live-cd-with-remastersys.html)

I second remastersys.

---

### Post by madoldfart on 2009-05-12
just preparing myself for the weekend.

After using remastersys or clonezilla to do a full system backup
The next step i need to do is to remove ubuntu so i can do a clean install of that other OS i mentioned earlier.

Once i have installed the other OS i will use my ubuntu backup disk to reinstall ubuntu.

My question is 
How do i easily/safely remove ubuntu so i can do a clean install of the other OS.

---

### Post by logos34 on 2009-05-12
> **madoldfart said:**
> 
Im guessing that i will have to reformat my hard drive on my Dell, then install iDeneb v1.4 10.5.6 OSX86, then install ubuntu.


Are you sure you have to install iDeneb on an empty disk? All I saw was this:

> # Do Not Install the iDeneb Base System over an existing Base System! This could cause the failure of the installation! To always execute a fresh install;

[http://ideneb.net/en/blog/37-blog/60-rilasciata-ideneb-v14-1056-](http://ideneb.net/en/blog/37-blog/60-rilasciata-ideneb-v14-1056-)

which seems to refer to an existing *iDeneb* installation, meaning wipe the target partition (not the whole drive) before installing. Better double-check.


> 
How do i easily/safely remove ubuntu so i can do a clean install of the other OS.

If indeed you must remove ubuntu first and install other OS on clean disk, you don't need to do anything special.  Either use gparted on the ubuntu live cd to simply delete the partitions, or let the iDeneb installer format the entire disk. It should install it's own bootloader.  When you restore ubuntu, you can either reinstall grub to the mbr or add ubuntu entry to iDeneb's bootloader so you can dual-boot

---

### Post by logos34 on 2009-05-12
a quick google turned up this:

> How Successfully Dual-Boot Hackintosh and Ubuntu Linux
[http://geeks.pirillo.com/profiles/blogs/how-successfully-dualboot](http://geeks.pirillo.com/profiles/blogs/how-successfully-dualboot)

applies to:
- iATKOS
- iPC (This is the distro we used.)
- iDeneb
- Kalyway (This has a reputation for being one of the easiest Hackintosh distros to get set up.)


again, nothing to indicate that you can't add it to a disk with an existing ubuntu installation

hope that helps

---

### Post by madoldfart on 2009-05-13
you guys are great:)

my interpretation of Do Not Install 

[SIZE="2"][SIZE="1"]the iDeneb Base System over an existing Base System! This could cause the failure of the installation! To always execute a fresh install;[/SIZE][/SIZE]
ment ensure you have a clean system ie no linux,no osx, no windows OS.

I will take your advise and read the links, if it fails, then no real loss, i will just keep trying.

---

