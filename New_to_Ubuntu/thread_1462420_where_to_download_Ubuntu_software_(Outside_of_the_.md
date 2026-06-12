---
title: "where to download Ubuntu software (Outside of the software center)"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by silkworm2.5 on 2010-04-25
Hi all.
Recently I installed Ubuntu to my dads computer since I liked it so much on my laptop. I just have one problem. He has no internet connection and I would like to put some software on it.
I have no Idea where to download the linux program files (.DEB files?) The software I want most is **Amarok**, and **Kubuntu/Ubuntu restricted extras**. Unfortunately, I a using pendrive linux right now because the hard drive is broken, so I get a message up saying "Not available in the current data" so I can't even view the website.
So, I cant download them to my netbook through the software centre, and I need to be able to move them about.

So, any help would be much appreciated! Especialy today, because tommorrow my netbook is going for repairs.
:KS:KS

---

### Post by carl4926 on 2010-04-25
You might consider a Ubuntu variant called Mint, it comes with those working OOTB.

You know amarok is kde, so were you talking kubuntu?
Mint does a kde version too.

It's probably possible to make a local repo on your HD though. But I don't know how. Someone will.

---

### Post by zekopeko on 2010-04-25
> **silkworm2.5 said:**
> Hi all.
Recently I installed Ubuntu to my dads computer since I liked it so much on my laptop. I just have one problem. He has no internet connection and I would like to put some software on it.
I have no Idea where to download the linux program files (.DEB files?) The software I want most is **Amarok**, and **Kubuntu/Ubuntu restricted extras**. Unfortunately, I a using pendrive linux right now because the hard drive is broken, so I get a message up saying "Not available in the current data" so I can't even view the website.
So, I cant download them to my netbook through the software centre, and I need to be able to move them about.

So, any help would be much appreciated! Especialy today, because tommorrow my netbook is going for repairs.
:KS:KS

Try this: [http://ubuntuforums.org/showthread.php?t=1100816](http://ubuntuforums.org/showthread.php?t=1100816)

---

### Post by tom.swartz07 on 2010-04-25
Usually when it says that it's not available in your area, try updating. I know many people that install and out of the box they need to update some core programs, or else it wont work.


Run updates and try again. 


Also Launchpad is a good place to get information about new programs. [http://launchpad.net](http://launchpad.net)

---

### Post by The Thunder Chimp on 2010-04-25
Here's how I would do it. You take a pen and a paper and take note of every program that you want. Then go to [this site]("http://packages.ubuntu.com/")and download each program you need. On the download page of each program, take note of every other package it depends on. These are the dependencies. Download these noted dependencies too (plus there dependencies if they have any, if such is the case, put the dependency's dependency in another folder). Put the programs in a folder than you can call Ubuntu Programs (the name is arbitrary, choose another one if you want), and the Dependencies in a folder called Ubuntu Dependencies. Put both filled folders on a flash drive.

Go on your dad's computer and install every dependency in the Ubuntu Dependencies folder, from your flash drive (starting with the dependencies that don't have any dependencies themselves). Once that is done, you may proceed in installing the programs.

Contact me if you have any questions.

---

### Post by silkworm2.5 on 2010-04-25
Thanks for the quick replies! :)
@carl4926 - I would prefer to keep ubuntu because it is what I'm used to and I really like it. And yes, It is Ubuntu, not Kubuntu. :)

@zekopeko - It is program software packages I'm looking to install, not Synaptic ones. But thanks anyway

@tom.swartz07[]("http://ubuntuforums.org/member.php?u=831692") - I don't need to download them into my pendrive installation, just get the installers and use them on the other computer

@The Thunder Chimp - Thanks, I'l try that now.

Wow, the replies on this forum are so fast! I'm used to posting questions then just checking back the next day. Thank you all!

---

### Post by zekopeko on 2010-04-25
> **The Thunder Chimp said:**
> Here's how I would do it. You take a pen and a paper and take not of every program that you want. Write them down in a seperate list on your piece of paper. Then go to [this site](http://packages.ubuntu.com/)and download each program you need. On the download page of each program, take note of every other package it depends on. These are the dependencies. Download these noted dependencies too (plus there dependencies if they have any, if such is the case, put the dependency's dependency in another folder). Put the programs in a folder than you can call Ubuntu Programs (the name is arbitrary, choose another one if you want), and the Dependencies in a folder called Ubuntu Dependencies. Put both filled folders on a flash drive.

Go on your dad's computer and install every dependency in the Ubuntu Dependencies folder, from your flash drive (starting with the dependencies that don't have any dependencies themselves). Once that is done, you may proceed in installing the programs.

Contact me if you have any questions.

The link to the thread I posted is FAR easier and less of a hassle.

---

### Post by zekopeko on 2010-04-25
> **silkworm2.5 said:**
> Thanks for the quick replies! :)

@zekopeko - It is program software packages I'm looking to install, not Synaptic ones. But thanks anyway

There is no difference. Packages are the same.

Look try and do this. Open Synaptic and simply click to install (or if you already have it installed then reinstall). After you selected all the packages you want go to File>Generate package list

After that simply follow the tutorial I posted.

---

### Post by silkworm2.5 on 2010-04-25
What does it mean by CD? I'm kind of newish to ubuntu still, and have had little practice with terminals...

---

### Post by The Thunder Chimp on 2010-04-25
In the terminal, cd (in lower case, as Linux Terminals are case sensitive) means "change directory". It basically changes your working area. For instance, if you want to search for a file, but you don't want to search the whole filesystem, then you change the directory to a the directory in which you know your file is in. It's as simple as that. Contact me if you don't understand.

---

### Post by zekopeko on 2010-04-25
> **silkworm2.5 said:**
> What does it mean by CD? I'm kind of newish to ubuntu still, and have had little practice with terminals...

change directory

mkdir is make directory.

just follow the tutorial I gave you.

---

### Post by achase79 on 2010-04-25
you can also check out [keryx]("http://www.keryxproject.org") or AptOnCd (which is in the repositories) to download packages along with their dependencies.

---

### Post by silkworm2.5 on 2010-04-25
Hey zekopeko, achase79, both your things are working well. But in neither of them can I get the restricted extras which I need for amarok to run. What should I do?

---

### Post by zekopeko on 2010-04-25
> **silkworm2.5 said:**
> Hey zekopeko, achase79, both your things are working well. But in neither of them can I get the restricted extras which I need for amarok to run. What should I do?

In Synaptic find restricted extras and right click on it. Click on Properties and then on the Dependencies tab. There you will find all that restricted extras installs.

---

### Post by silkworm2.5 on 2010-04-26
That's the problem. I cant find it. In either synamptic or Keryx.

---

### Post by sisco311 on 2010-04-26
> **silkworm2.5 said:**
> That's the problem. I cant find it. In either synamptic or Keryx.

ubuntu-restricted-extras is in the multiverse repository. 

Go to System -> Administrations -> Software Sources and enable the repo, then install it via Synaptic.

Or, run the following commands in a terminal:
```

sudo software-properties-gtk -e multiverse 
sudo apt-get update
sudo apt-get install ubuntu-restricted-extras 

```

---

### Post by silkworm2.5 on 2010-05-04
OK, I just did the simple thing and brought the computer to my house to access the Internet. Updated it that way and managed to get everything I needed.
Thanks to you all for your help!
:D

---

