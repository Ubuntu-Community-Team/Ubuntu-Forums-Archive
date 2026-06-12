---
title: "google earth"
date: 2011-03-15
forum: New to Ubuntu
---

### Post by DaveMcC on 2011-03-15
Hello all
Have now try ed 3 times to get Google earth to run on Ubuntu ver10 but its a no go

It installs "I think" then when clicked on the earth icon, nothing

Dave

---

### Post by howefield on 2011-03-15
Try installing the package lsb-core from the package manager.

---

### Post by DaveMcC on 2011-03-15
> **howefield said:**
> Try installing the package lsb-core from the package manager.

Can't find the core as it don't open, its just a wee brown box type icon, ubuntu software center opens goes thur the part as if its installing
But thats it, it installed OK on ubuntu 9 but not 10

Dave

---

### Post by spook1980 on 2011-03-15
first open up synaptic package manager and remove google earth

then in a terminal(type in each command indivigly)

sudo apt-get install googleearth-package

sudo apt-get install lsb-core

sudo googleearth-package

after all that is done in your home folder you should see a .deb package install that with gdebi, and all should be good

---

### Post by DaveMcC on 2011-03-15
After a lot of looking and trying no to go blind or cross eyed the

"synaptic package manager" will only let me mark it for installation (googleearth)

Unless I am doing this wrong?

Dave

Thats something else I can give up on, dont know what I am doing, all this command line crap should have died with DOS 6.2
Some day, Linux might discover, that not every body wants to learn obscure  line commands

If Ubuntu 10, is so good, how come the google earth thing installed on Ver 9 and not on 10
Point, click, download, click, install, thats all there should be not miles of sudo = etc = mud = not today

Dave

---

### Post by rg4w on 2011-03-15
> **DaveMcC said:**
> Thats something else I can give up on, dont know what I am doing, all this command line crap should have died with DOS 6.2
Some day, Linux might discover, that not every body wants to learn obscure  line commands

If Ubuntu 10, is so good, how come the google earth thing installed on Ver 9 and not on 10
Point, click, download, click, install, thats all there should be not miles of sudo = etc = mud = not today
You'll often see command line tips posted because they're simpler and less ambiguous than trying to describe GUI steps for how to get packages via Synaptic Package Manager.

In this case, the core issue isn't Ubuntu at all, but simply that Google hasn't yet delivered an Earth .deb package with all the required info for a smooth install.

---

### Post by jcolyn on 2011-03-15
If you want to install the latest current version of Googleearth follow these simple steps and you will have it up and running in no time.

First though you will need to purge any installs or attempts at installing Googleearth.

These terminal entries have to be entered exactly as typed below so you may want to copy/paste into your terminal.

To start: Open a terminal and enter ```
sudo apt-get install lsb-core
``` Once done enter ```
sudo apt-get install googleearth-package
``` After the package is installed enter ```
sudo make-googleearth-package --force
``` This process will take several minutes and you will see many warning notices but ignore them.

Once the above process is completed close the terminal and go to your /home folder where you will find a googleearth_xx.deb package. Double-click it and follow instructions.

Once installed you should have the Googleearth link in your Internet folder.

Enjoy

---

### Post by jcolyn on 2011-03-15
> **DaveMcC said:**
> Thats something else I can give up on, dont know what I am doing, all this command line crap should have died with DOS 6.2
Some day, Linux might discover, that not every body wants to learn obscure  line commands

Microshaft had the right idea with DOS. When Windoze came along that ruined it for me. I dumped it and haven't looked back since.

The only halfway decent version was Win 2K and it was only a fraction better...

> **DaveMcC said:**
> If Ubuntu 10, is so good, how come the google earth thing installed on Ver 9 and not on 10
Point, click, download, click, install, thats all there should be not miles of sudo = etc = mud = not today

Dave

Ubuntu has nothing to do with software provided by another software maker so the installation is not Ubuntu's fault..

Googleearth in v9 was/is an old version. My understanding is Google won't let Linux make the current version available in the repos..so we have to build it from the downloaded googleearth.bin file per my instructions in my post above..

---

### Post by DaveMcC on 2011-03-17
Thats funny, in a good way, I enjoy a good laugh on Paddy's day, this bloody irish computer won't work now, yes I am from Northern Ireland

jcolyn
Have been trying to do the code thing that you have provided
Started by 
Open a terminal and enter 
First line of code
I get reply, 
enter password, 

when I try that,! the key brd stops working except for the enter key
Which I then get 

sorry about that
retype password

Can't keybrd don't work


I have found a quick way to make google warth work
Click on computer B on my KVM thing and run other computer which has Ubuntu 9 running gooogle earth

Dave

---

### Post by pacman5 on 2011-03-20
> **jcolyn said:**
> If you want to install the latest current version of Googleearth follow these simple steps and you will have it up and running in no time.

First though you will need to purge any installs or attempts at installing Googleearth.

These terminal entries have to be entered exactly as typed below so you may want to copy/paste into your terminal.

To start: Open a terminal and enter ```
sudo apt-get install lsb-core
``` Once done enter ```
sudo apt-get install googleearth-package
``` After the package is installed enter ```
sudo make-googleearth-package --force
``` This process will take several minutes and you will see many warning notices but ignore them.

Once the above process is completed close the terminal and go to your /home folder where you will find a googleearth_xx.deb package. Double-click it and follow instructions.

Once installed you should have the Googleearth link in your Internet folder.

Enjoy
I went through all the above steps on my daughter's Ubuntu 8.04 system and restarted the system and have the Googleearth link in my Internet folder but when I click on it nothing happens. No Google Earth and no error messages. 

Can you tell me where I should go from here ?

Thank you.

---

### Post by Daveth on 2011-03-20
try this
[HTML]https://help.ubuntu.com/community/GoogleEarth[/HTML]

---

### Post by jcolyn on 2011-03-20
> **pacman5 said:**
> I went through all the above steps on my daughter's Ubuntu 8.04 system and restarted the system and have the Googleearth link in my Internet folder but when I click on it nothing happens. No Google Earth and no error messages. 

Can you tell me where I should go from here ?

Thank you.

The new version of Googleearth may not be compatible with 8.04

I know it works on the current version 10.10 and previous 9.04 but have not tried it on older versions.

---

### Post by cmcanulty on 2011-03-20
I have tried all the above several times with 3 different gateway computers and no luck. Also tried it on a brand new ubuntu HP G72t laptop no luck. Google earth worked fine before maverick with my gateways it only gives flash screen then crashes. I did all the suggested things and many other attempts. This is bad for Ubuntu's reputation.

---

### Post by cyncicle on 2011-03-20
Works fine on my Dell laptop after I installed lsb-core through Package Manager.  I didn't even need to reinstall Earth.

---

### Post by jcolyn on 2011-03-20
> **cmcanulty said:**
> I have tried all the above several times with 3 different gateway computers and no luck. Also tried it on a brand new ubuntu HP G72t laptop no luck. Google earth worked fine before maverick with my gateways it only gives flash screen then crashes. I did all the suggested things and many other attempts. This is bad for Ubuntu's reputation.

The problem is not with Ubuntu. I'm running it on Kubuntu 10.10, Mint 10 KDE, Mint 10 Gnome on a laptop, and Natty 11.04 Kubuntu.. So it does work on newer Ubuntu OS's

---

### Post by scouser73 on 2011-03-20
Dave, you've stated that you have already installed Google Earth but that you're having a problem with it, there is an easy fix but it requires that you use the Terminal.

**1** - Go to **Application**, then click on **Accessories** and then click **Terminal**.

**2** - Now copy and paste this command into Terminal and press enter.

> **sudo apt-get install lsb-core**

3 - Now press Enter and a password request will show on terminal, go ahead and enter your password, don't worry that your password won't show, nor will any asteriks.

Now that you have followed the steps, click on Google Earth and it will show up without any hitch.

---

### Post by pacman5 on 2011-03-21
> **Daveth said:**
> try this
[HTML]https://help.ubuntu.com/community/GoogleEarth[/HTML]

Thanks, Daveth.

During the installation process masses of different things which meant nothing to me, even if I had been able to read them as they flashed past on the terminal screen, were installed. Do I have to remove/deinstall all those things before following your suggestion and, if so, how.

Paddy

---

### Post by tordeu on 2011-03-21
> **DaveMcC said:**
> 
Started by 
Open a terminal and enter 
First line of code
I get reply, 
enter password, 

when I try that,! the key brd stops working except for the enter key
Which I then get 

sorry about that
retype password

Can't keybrd don't work


It is not that the keyboard does not work. It is just asking for your password, but it will not display what you are typing.
So, when it asks for your password in command line, just enter your password and then press enter.

If it says "sorry about that, retype password" it just means that you did not enter the password correctly.

---

### Post by tordeu on 2011-03-21
> **DaveMcC said:**
> After a lot of looking and trying no to go blind or cross eyed the

"synaptic package manager" will only let me mark it for installation (googleearth)

Unless I am doing this wrong?

Dave

After you mark something for installation in Synaptic Package Manager, you need to click on the "Apply" button at the top of the Synaptic Package Manager.

"Mark for Installation" just means that you want to install that software, but it does not install it right away, it just collects what you want to install. (Because you might want to install several things).
When you are done with selecting all the software you want to install/uninstall/reinstall etc., you have to click "Apply" and only then will the Synaptic Package Manager carry out all the Installations.

---

### Post by Daveth on 2011-03-22
it might be appropriate to upgrade ubuntu to a newer version, then follow the guide i suggested. It installed easily in Lucid, but i think JColyn may be right in asserting that the current version of google-earth might just have too many dependency version differences to make it worthwhile bothering with. Taking the Ubuntu upgrade path seems the most obvious solution, then try installing Google-earth.

---

### Post by tordeu on 2011-03-22
Funny thing: I just had a the same problem this morning (What are the chances?): Clicking on Google-Earth and nothing happens. (Besides: I did not have this problem before, so GoogleEarth was working before, which means that this might be totally unrelated to your problem although the symptom is the same), so the guide provided above might indeed be what you need.

Here is what I did:

When it did not start I tried to run it from command line and it told me that another instance of GoogleEarth was running (which was not the case) and GoogleEarth itself suggested deleting the file ~/.googleearth.instance-running-lock.
This fixed the problem for me. So, all that was necessary in my case, was:

```

rm ~/.googleearth/instance-running-lock

```

As I said, this might be totally unrelated to your problem (since you just did a fresh install), but you never know, so I wanted to post this.

Nevertheless: If you think you installed it, but it does not start, you might want to just try calling it from command line and see if it gives you some error:

[CODE]
googleearth
[CODE]

---

### Post by beew on 2011-03-22
Just install lsb-core like others said and download the .deb package from googleearth's website. I used the google package in creating the .deb in Maverick, it installed without a hitch. Only problem is the the Panoramio pictures don't show up. Installed the .deb from ge on Natty and everything works, including the pictures. I will try that on Maverick later.

---

### Post by jcolyn on 2011-03-22
> **beew said:**
> download the .deb package from googleearth's website. .

The problem with installing this package is it is a generic .deb package and does not work on all debian based computers. When you follow the instructions I gave it builds a package configured to that particular computer.

Again below are the instructions...

```
sudo apt-get install lsb-core
``````
sudo apt-get install googleearth-package
```and finally

```
sudo make-googleearth-package --force
```ignore the warnings since they have nothing to do with the final output.

Now go to your /home folder and double-click the googleearth package not the .bin file. You can delete the .bin file..

---

### Post by beew on 2011-03-22
> **jcolyn said:**
> The problem with installing this package is it is a generic .deb package and does not work on all debian based computers. When you follow the instructions I gave it builds a package configured to that particular computer.
..


It says debian/ubuntu. I have installed it on Ubuntu 11.04 (alpha) with no problem. Haven't tried it on Maverick yet. Does it give you any trouble? I have installed ge on Mav with the googleearth-package, but like i said the Panoramio pictures don't show up.

---

### Post by jcolyn on 2011-03-22
> **beew said:**
> It says debian/ubuntu. I have installed it on Ubuntu 11.04 (alpha) with no problem. Haven't tried it on Maverick yet. Does it give you any trouble? I have installed ge on Mav with the googleearth-package, but like i said the Panoramio pictures don't show up.

Tried it on my LMDE and Debian 6 machines without success. No error messages or anything.. It just sat there doing nothing...

I built the package as mentioned in my previous post and it installed and worked fine. I have not tried it on any other machines.

---

### Post by Donnie Love on 2011-03-23
> **jcolyn said:**
> 
These terminal entries have to be entered exactly as typed below so you may want to copy/paste into your terminal.
Enjoy

I don't think you can paste into the DOS window. Don't you have to retype the magic gibberish by hand?

---

### Post by dnairb on 2011-03-23
Copy the commands as you would normal text.
Then, in terminal, press <CTRL><SHIFT><V> together, which will paste into the terminal window.

---

### Post by Donnie Love on 2011-03-23
Shift? Of course. Always the extra step.

Thanks. this worked pretty good. :0>

---

### Post by oldos2er on 2011-03-23
Or just Shift-Ins to paste.

---

### Post by Torp3x on 2011-03-23
> **DaveMcC said:**
> Thats something else I can give up on, dont know what I am doing, all this command line crap should have died with DOS 6.2
Some day, Linux might discover, that not every body wants to learn obscure  line commands

If Ubuntu 10, is so good, how come the google earth thing installed on Ver 9 and not on 10
Point, click, download, click, install, thats all there should be not miles of sudo = etc = mud = not today

Dave


I agree. Although I've become oddly fond of terminal for things like aircrack which is quite satisfying to use, for general home computing it needs to die in a fire. If I want to install the latest Google Earth, Firefox or whatever, 90% of that process shouldn't be googling Linux forums trying to find out what obscure code I need to copy and paste, or what extra packages I need to install from a command line. It's not just applications either, nothing I've plugged into my laptop while running Ubuntu hasn't required me to alter some low level system settings, and a lot of my hardware still doesn't work at all.

I will stick with Ubuntu though because it has potential to be an amazing operating system when I get more experience with it. If I was a Linux genius I would definitely love it. But I'm not, and neither are most people, and that's why most people use Windows.

---

### Post by beew on 2011-03-24
> **Torp3x said:**
> I agree. Although I've become oddly fond of terminal for things like aircrack which is quite satisfying to use, for general home computing it needs to die in a fire. If I want to install the latest Google Earth, Firefox or whatever, 90% of that process shouldn't be googling Linux forums trying to find out what obscure code I need to copy and paste, or what extra packages I need to install from a command line. It's not just applications either, nothing I've plugged into my laptop while running Ubuntu hasn't required me to alter some low level system settings, and a lot of my hardware still doesn't work at all.

I will stick with Ubuntu though because it has potential to be an amazing operating system when I get more experience with it. If I was a Linux genius I would definitely love it. But I'm not, and neither are most people, and that's why most people use Windows.


Look, I have installed GE many times and I never have to use the command line (I chose to when I build it with the ge package, but I didn't have to) Maybe OP is just doing it the wrong way. You can install it from the medibuntu ppa or  download an up to date .deb file from Googleearth (and install lsb-core from Synaptic) and installation is just one click.  Finally, if you want to build GE with the goolgleearth-package you would have to type in about 3 lines in the terminal and you can cut and paste from any tutorial on the web or on UF.

It seems that some people are having troubles installing GE because they are getting bad advice from out of date web tutorials and  geeks who make things unnecessarily complicated (because they are more interested in showing off than to help), one guy on this forum actually told a new user to download a tar ball and compile from source and of course the latter got into a big mess because of dependency problems.

---

### Post by Elfy on 2011-03-24
> **dnairb said:**
> Copy the commands as you would normal text.
Then, in terminal, press <CTRL><SHIFT><V> together, which will paste into the terminal window.

> **Donnie Love said:**
> Shift? Of course. Always the extra step.

Thanks. this worked pretty good. :0>

> **oldos2er said:**
> Or just Shift-Ins to paste.

or select the text and then middle mouse button in the terminal

---

### Post by cmcanulty on 2011-03-24
it just doesn't work in 10.10 on some laptops I have tried everything posted and more with 2 gateway laptops and a new hp laptop

---

### Post by tordeu on 2011-03-24
Besides from having to delete the lock file yesterday, because it would not start otherwise (which did not happen before) and the fact that GoogleEarth sadly does use locale when importing (and probably exporting) MyPlaces, I did not have had problems with it. Especially not when it comes to getting it started at all.

But I have mostly installed in on desktop systems. It would interesting to know what happens when you call googleearth from terminal and if the systems it does not run on have something in common (I am thinking especially about the graphics chip (manufacturer). Maybe a graphics driver problem as well).

---

### Post by cmcanulty on 2011-03-24
yes I think it is the graphics chip as I get errors on that but even so it ran on same computers up through 10.04, 10.10 broke it somehow or googleearth got more robust and requires more power. I really miss it though.

---

### Post by tordeu on 2011-03-24
Mmh... that's interesting. Maybe it has something to do with the video driver. I heard that some have problems running things with the open source AMD/ATI drivers, but the closed sourced ones work. Depending on which chip you got problems with, maybe it is something different. And maybe it will work with 11.04, again.
While I don't use GoogleEarth regularly, I would really miss it either.

---

