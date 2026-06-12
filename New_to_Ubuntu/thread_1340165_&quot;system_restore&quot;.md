---
title: "&quot;system restore?&quot;"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by severedsolo on 2009-11-28
hi, first post here, so play nice please :P

i went to make the jump from windows to ubuntu today, using a dual boot, everything worked out great, right up until the point i went to update my graphics drivers. basically i installed the "recommended drivers" from the "hardware" popup that came up, and it borked, my monitor came up with "input not supported" and i had to uninstall it for now....

so i have 2 questions

1. is there a way to "restore" it without a uninstall? bearing in mind i havent even had a chance to learn how to use it yet.

2. can anybody recommend the RIGHT drivers for an NVIDIA Geforce 7050/610i (onboard)

---

### Post by Don1500 on 2009-11-28
The "restore" is a re-install. It doesn't take that long.

For the driver: System => Administration => Hardware Drivers
You can also get the correct driver from the NVidia web site. Make sure you pick the right one.

---

### Post by severedsolo on 2009-11-28
> **Don1500 said:**
> The "restore" is a re-install. It doesn't take that long.

For the driver: System => Administration => Hardware Drivers

ok i will try that thank you very much for the swift reply!

---

### Post by Don1500 on 2009-11-28
try this site:
[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

---

### Post by halitech on 2009-11-28
There is no "restore" feature built into Ubuntu but most issues can be resolved by logging into a terminal and fixing things. You can use something like remastersys to create a restore disk if you want though.

As far as your driver, sounds like you probably had the right one but it wanted to run at 1600x1200 or something higher then your monitor supported. you could try creating an xorg.conf file and enter the info you need to run correctly.

Open a terminal and run
```
sudo touch /etc/X11/xorg.conf
```
then```
gksudo gedit /etc/X11/xorg.conf
```
and paste this in
> Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
    SubSection "Display" 
        Depth    24 
        Modes    "1024x768"         
    EndSubSection 
EndSection

*taken from this thread [http://ubuntuforums.org/showpost.php?p=8279613&postcount=155](http://ubuntuforums.org/showpost.php?p=8279613&postcount=155)

---

### Post by severedsolo on 2009-11-28
> **halitech said:**
> There is no "restore" feature built into Ubuntu but most issues can be resolved by logging into a terminal and fixing things. You can use something like remastersys to create a restore disk if you want though.

As far as your driver, sounds like you probably had the right one but it wanted to run at 1600x1200 or something higher then your monitor supported. you could try creating an xorg.conf file and enter the info you need to run correctly.

Open a terminal and run
```
sudo touch /etc/X11/xorg.conf
```then```
gksudo gedit /etc/X11/xorg.conf
```and paste this in


*taken from this thread [http://ubuntuforums.org/showpost.php?p=8279613&postcount=155](http://ubuntuforums.org/showpost.php?p=8279613&postcount=155)

ok, thanks very much for the help, when i reinstall i will try the nvidia website and then i will do the above mentioned fix if i get the same problem, again thank you very much for the help, its a shame my first foray into ubuntu ended so abruptly, but i won't let it put me off

---

### Post by Don1500 on 2009-11-28
I just thought of something, When you were trying to add the driver through the Icon at the top right of you screen, did you happen to have the synoptic package manager open?
You can only have one synoptic open at a time to prevent file corruption. (I just did this on a laptop I'm setting up  :oops: so don't worry, we all err.)

---

### Post by severedsolo on 2009-11-28
i had the applications manager open... i think... is that what you mean?

edit: whoops sorry i mean the software centre, i was browsing for what was available also maybe the wireless connection bit as well... i cant remember if i closed it

another edit: i just googled what you meant, no i didnt have that open, but thanks for the info

---

### Post by HandyAndy on 2009-11-28
The *Software Centre* is, like *Synaptic*, a GUI front-end for *apt*, so you did have it open and therefore what Don1500 said does apply and that was possibly the problem.

Welcome and good luck  :)

---

### Post by severedsolo on 2009-11-28
ah.. good to know.... so anything like that from the top bar (for want of a better word) needs to be shut down and the only thing it should be doing is installing the driver?

---

### Post by HandyAndy on 2009-11-28
I know you should only have one instance of anything that uses *apt* running, but I don't really know enough to say if any other programs/processes might corrupt a download.
To be safe, I close everything while I'm installing something.

---

### Post by severedsolo on 2009-11-28
ok.... and im assuming that (unlike windows) ubuntu wont start something in the background from boot without asking me first? (especially as its a new install)

---

### Post by HandyAndy on 2009-11-28
Whatever a clean install has got running from start-up will be safe.

---

### Post by severedsolo on 2009-11-28
thank you very much! you have been very helpful! can i just ask one more question? in the guide i read to dualbooting windows and ubuntu it recommends having a seperate NTFS partition for storage so both OS can read it, and just assigning enough HD space to the OS partitions can install apps and such,

is this the right way to do it? (i know about swap space im accounting for that)
what is a "decent" size for ubuntu and apps?

---

### Post by oldsoundguy on 2009-11-28
you can only have ONE item open at the same time between:
Software Center
Synaptic Package Manager
Terminal

As to the original issue .. Try installing Envy and using it for your NVidia or ATI card (it is in your Package manager)
Once installed it will show up in applications> system tools.  Run it from there.
The only time Envy has failed to install the proper video driver for me is on a unit that has a double generic LCD (one of those 90 buck ones with built in speakers that was on sale for 60 bucks at the drug store!)

---

### Post by severedsolo on 2009-11-28
wow.... im actually shocked by the level of help.... less than half an hour since my first post and i have 3 solutions to my original problem, a solution to a problem i didnt even know i had and had it all explained to me in "newbie" language, try getting that from microsoft.... thank you so much to everyone, i think i have enough to be getting on with now, 

you have certainly made ubuntu a more attractive prosepect for me, and i cant wait to have a proper play with it, thank you again!

---

### Post by Don1500 on 2009-11-28
> **severedsolo said:**
> wow.... im actually shocked by the level of help.... less than half an hour since my first post and i have 3 solutions to my original problem, a solution to a problem i didnt even know i had and had it all explained to me in "newbie" language, try getting that from microsoft.... thank you so much to everyone, i think i have enough to be getting on with now, 

you have certainly made ubuntu a more attractive prosepect for me, and i cant wait to have a proper play with it, thank you again!

I was(am) having a problem with my website storage access via FTP at Roadrunner yesterday and had the most Frustrating time explaining it to them. By the time they finally got someone that could understand my problem I was ready to shoot myself just so I wouldn't have the problem any more. Trying to explain that the problem is on THEIR side and not with my set up is almost impossible. They finally had to replace the drive my site was stored on, yes, they had a hardware problem. (You could hear the unsaid "Opps" on the phone.) I am going to have to take that site down and re publish it some place else.

That is nothing like the FREE service you get here!

---

### Post by presence1960 on 2009-11-28
you can use envyng to download & install the appropriate drivers for your Nvidia card. From Ubuntu open a terminal and run these commands one at a time:

```
sudo apt-get install envyng-core
sudo apt-get install envyng-qt
sudo apt-get install envyng-gtk
```

You can then run Envyng by going Applications > System Tools > EnvyNG or from terminal ```
envyng -t
``` Follow the prompts to install Nvidia driver.

---

### Post by halitech on 2009-11-28
and pray and cross your fingers envy doesn't blow your system up

---

### Post by presence1960 on 2009-11-28
> **halitech said:**
> and pray and cross your fingers envy doesn't blow your system up

never blew mine up nor any of the installs I have done on client's machines. Of course nothing is foolproof or perfect!

---

### Post by halitech on 2009-11-28
drop into the IRC channel sometime and ask what people think of Envy. They even have a factoid warning people against using it as it has blown up enough systems that they won't even deal with trying to fix it.

---

### Post by presence1960 on 2009-11-28
> **halitech said:**
> drop into the IRC channel sometime and ask what people think of Envy. They even have a factoid warning people against using it as it has blown up enough systems that they won't even deal with trying to fix it.

Be that as it may, I have never had a problem with it. But again nothing is foolproof as we are seeing with all the troubles with dist upgrades to 9.04 and 9.10 and in 9.10 GRUB 2. Should we emphatically rule out both of those? I don't think so. I personally opt for a clean install rather than a dist upgrade, but because I do not like dist upgrades does not take away from the fact that many use that function successfully.

I respect your opinion and have found a lot of your posts informative for me, but on this one I will have to respectfully  disagree for the above reason, but with a disclaimer that no software is infallible on any machine.

---

### Post by jrrader on 2009-11-28
I realize this thread has taken a different route but I wanted to add on to this:

> **Don1500 said:**
> The "restore" is a re-install. It doesn't take that long.

With a separate partition for a home folder and a simple shell script to reinstall applications and features you use (and remove those you don't use) reinstalling Ubuntu, or doing a clean install of a new version, can take less time than a Windows system restore.

Example of reinstalling script:
```

#!/bin/bash
whoami > ~/errorlog
date >> ~/errorlog 

#Remove unwanted programs
sudo apt-get -y remove evolution 2>> ~/errorlog
sudo apt-get -y remove empathy 2>> ~/errorlog 

# system tools
sudo apt-get -y install flashplugin-nonfree 2>> ~/errorlog
sudo apt-get -y install compizconfig-settings-manager 2>> ~/errorlog
sudo apt-get -y install virtualbox-ose 2>> ~/errorlog
sudo apt-get -y install ntfs-config 2>> ~/errorlog
```
(my actual script is currently 200 lines long and does quite a bit more than just install and remove.  But it started as a simple list of programs to install)

---

### Post by halitech on 2009-11-28
I've tried it myself twice on 2 different machines and in both cases it blew my system up as well before I switched over to Debian and I've seen it with others. In theory anything in the repos should be safe to use but as you point out, anything can happen and no software is infallible but we should be aware of the possibilty of things going wonky during use.

---

### Post by severedsolo on 2009-11-29
ok just to let everyone know, envy didnt work, (i think because i didnt do the script properly) but i reinstalled using hardware manager and left everything else shut and it worked fine so obviously i accidentally corrupted it using software centre, thanks for the help its all working fine, i ahve to say im quietly impressed with ubuntu, but i wont be dropping windows completely because i have alot of games

---

### Post by halitech on 2009-11-29
glad to hear you got things working and that you like it even though you had some issues getting started. Congrats and welcome to Ubuntu :)

---

