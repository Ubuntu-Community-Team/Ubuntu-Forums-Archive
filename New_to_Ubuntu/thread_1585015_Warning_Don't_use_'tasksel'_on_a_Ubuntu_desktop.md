---
title: "Warning: Don't use 'tasksel' on a Ubuntu desktop"
date: 2010-09-29
forum: New to Ubuntu
---

### Post by oregonbob on 2010-09-29
I wanted to add dns-server to a Ubuntu Karmic running Mint 8. The "tasksel" command looked very handy for this, so I did a "**sudo tasksel**", then put a checkbox on "DNS Server" and hit the only other option--an "**OK**" button. Without and warning or prompt or anything it wiped out most of the operating system including gnome, all the components of desktop and network configuration! It removes all packages of ubuntu-desktop! Crazy! Even worse if you crash out of it, it finished removing packages in the background! That seems like definition of a virus to me, definitely malware.

So be warned don't use "**tasksel**"! It is a dangerous command!

---

### Post by cariboo on 2010-09-29
I've been using tasksel for over 10 years, I've never seen it do anything like that. 

Did you have any other pending actions?

---

### Post by oleink on 2010-09-29
interesting.  Sounds weird cause I thought lots of people used it without problems. I'm not super smart so i'm not sure i'd even know what i was doing in the first place.  Well i mean i'm smart just haven't been as exposed to this stuff yet.  Most of my stuff is not server related although I have been part of a networking program

---

### Post by oregonbob on 2010-09-29
No I wasn't trying to install or remove anything else. I found a thread on here of others who confirm this horrible bug. Maybe you use options when you install with tasksel? I just entered "tasksel" at command line.

I also see people running 10.04 with same bug. I checked bug reports. So it is in all versions apparently. The machine I was on was remote, so now I can't connect to it at all. I'll have to drive to site tomorrow. 

Bug report: [https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/150252?comments=all](https://bugs.launchpad.net/ubuntu/+source/tasksel/+bug/150252?comments=all)

Other thread on here: [http://ubuntuforums.org/showthread.php?t=1369551&highlight=tasksel+removes+packages](http://ubuntuforums.org/showthread.php?t=1369551&highlight=tasksel+removes+packages)

I keep that system up to date too!

---

### Post by oleink on 2010-09-29
> **oregonbob said:**
> No I wasn't trying to install or remove anything else. I found a thread on here of others who confirm this horrible bug. Maybe you use options when you install with tasksel? I just entered "tasksel" at command line.

I also see people running 10.04 with same bug. I checked bug reports. So it is in all versions apparently. The machine I was on was remote, so now I can't connect to it at all. I'll have to drive to site tomorrow. 

I keep that system up to date too!

man sorry that stinks.  You are still having problems then?  and if so what are they now?

---

### Post by jwbrase on 2010-09-30
> **oregonbob said:**
> That seems like definition of a virus to me, definitely malware.

"Never attribute to malice what can be explained by stupidity."

It's most likely not malware, it was simply not written competently. In any case, I agree that it *is* dangerous.

---

### Post by NightwishFan on 2010-09-30
I never tried tasksel on Ubuntu, it works great on Debian.

---

### Post by jtarin on 2010-09-30
It works like most ncurses tools......select and deselect using the spacebar. You should go through the complete list and insure Ubuntu Desktop was still selected. We're victims of "new 'n' shiny 'n' easy"....place this in the archives along with kernel and software upgrades.

---

### Post by rockerphil on 2010-09-30
> **NightwishFan said:**
> I never tried tasksel on Ubuntu, it works great on Debian.

i'd like to second this statement. i haven't used Ubuntu on my own personal machines for a while although i do still install it on people's PCs that want to try Linux, but it seems like the Debian users are a bit more prone to the command line and a bit more nostalgic by nature

---

### Post by mcduck on 2010-09-30
I have always used tasksel on all my Ubuntu machines for installing LAMP server, additional desktops or Ubuntu Studio packages. Never had any troubles. 

But perhaps the bug is related to running tasksel on it's own instead of directly telling it what you want to install. (I always run "sudo tasksel install lamp-server" instead of running "tasksel" and selecting LAMP-server from the list. Although I *do* occasionally use the list feature through Synaptic Package Manager and that' hasn't caused any problems either).

---

### Post by indytim on 2010-09-30
> I have always used tasksel on all my Ubuntu machines for installing LAMP server, additional desktops or Ubuntu Studio packages. Never had any troubles.

But perhaps the bug is related to running tasksel on it's own instead of directly telling it what you want to install. (I always run "sudo tasksel install lamp-server" instead of running "tasksel" and selecting LAMP-server from the list. Although I do occasionally use the list feature through Synaptic Package Manager and that' hasn't caused any problems either).

I agree with McDuck.  I too have used tasksel to install LAMP for several years without incident.  I've always used it from the whole tasksel menu.  

I did have a reader of one of my tech papers bork up his whole operating system once by using tasksel.  Seems the genius decided that he would "de-select" a lot of the system installed services from tasksel as well as installing LAMP.... duh.

IndyTim

---

### Post by HermanAB on 2010-09-30
Yup, the issue is a general one, not just limited to tasksel.

Uninstalling complex programs from a Linux system should be done with the utmost care, since it is akin to unscrambling an egg.  I never bother to uninstall anything.  It is far less hassle to re-install the whole system every few years from scratch.

---

### Post by SlugSlug on 2010-09-30
I done the same yesterday,

I was a bit suspicious as Ubuntu Desktop was unticked as soon as I hit OK I seen it uninstalling stuff it shouldn't.


So a new ssh session to kill it (Ctrl+c dnt work)

and then a grep removed /var/log/dpgk  showed me what I had to reinstall

---

### Post by tgalati4 on 2010-09-30
Sounds like tasksel does exactly what it's supposed to.

---

### Post by oregonbob on 2010-09-30
How can you say it does what it is supposed to do? It removes packages with no warning. I've used it before too with success. I didn't deselect the packages it removed. All I did was select "DNS Server".

When one gets totally unexpected behavior from a program there is no way it does what it is supposed to do. There is a long list of users caught by this bug. It should have a warning at least. The idea behind installing packages is great, removing them without warning is not.

Further: Do you realize there is NO way to simply quit out of tasksel menu without it taking actions you didn't intend? Take a look. I went back into the menu and it displays a list of install choices and then an "OK" button. When you hit OK it starts removing things without any prompt. You can't even Control-C out of it. You have to kill it and kill background package manager.

I tried "grep removed /var/log/dpkg.log" but that doesn't work for discovering exactly what it removed. It lists bundle names not packages. I guess the trick is NEVER run tasksel without options, always use command line instructions.

---

### Post by oregonbob on 2010-10-01
This has numerous bug reports and apparently it has never been corrected. If you hit the bug, prepare to have to reinstall the OS. Try googling these words: "tasksel launchpad bug".

Among a long list of victims you will find such as this one:
[http://www.google.com/search?source=ig&hl=en&rlz=&=&q=tasksel+launchpad+bug&aq=f&aqi=&aql=&oq=&gs_rfai=C39GPQ2qlTIaIHJuaoASt5az4CgAAAKoEBU_QzyVA](http://www.google.com/search?source=ig&hl=en&rlz=&=&q=tasksel+launchpad+bug&aq=f&aqi=&aql=&oq=&gs_rfai=C39GPQ2qlTIaIHJuaoASt5az4CgAAAKoEBU_QzyVA)

It may happen when you select an option and then deselect it. Regardless tasksel is a loaded gun with a bad safety. That is a shame because concept is great.

---

### Post by jtarin on 2010-10-01
It's an axe....not a scalpel.

---

### Post by oregonbob on 2010-10-01
There appear to be many "axe" in Ubuntu these days. apt-get is just as dangerous. If you want an example (DON'T DO THIS), run the simple command "sudo apt-get install xfs" (DON'T DO THIS). If you are running the ubuntu version that almost all users are, this will **completely remove your entire desktop system and all unrelated applications that use gnome without warning**. It is funny to think that apt-get warns you if you want to add a small package that might use 10 MB of disk space, but it does NOT warn you if it is about to remove your entire system. Something is wrong with this. I guess there long line of users caught by this will have to get longer before a change is made.

Yes, I did this on another system. I was installing 64-bit flash because a flash website wasn't working (speakeasy speed test). When I did it, it displayed a line that said "Suggested package to install: xrunner... xfs". So I did that and it wiped out a system. Heaven forbid it was a mission critical system. It removed gnome and all applications that use gnome...think about that.

This is a very serious bug. There needs to be an override option for removing a large number of packages and then make default to prompt warnings.

---

### Post by niteshifter on 2010-10-01
Hi,

tasksel was doing what it was instructed to do. I will say this: It takes some getting used to ;)

And how would you do that, without doing damage?

```
tasksel -t
```
aka test mode, show what is going to happen without actually doing it. As to it being poorly written, wonder why that option is present? :)

---

### Post by NightwishFan on 2010-10-01
> **oregonbob said:**
> If you want an example (DON'T DO THIS), run the simple command "sudo apt-get install xfs" (DON'T DO THIS). If you are running the ubuntu version that almost all users are, this will **completely remove your entire desktop system and all unrelated applications that use gnome without warning**.

It did not here on lucid. apt-get should always warn you.

```
sudo apt-get install xfs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  xfs
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 89.8kB of archives.
After this operation, 369kB of additional disk space will be used.
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/universe xfs 1:1.0.8-6 [89.8kB]
Fetched 89.8kB in 1s (47.1kB/s)         
Selecting previously deselected package xfs.
(Reading database ... 156386 files and directories currently installed.)
Unpacking xfs (from .../xfs_1%3a1.0.8-6_amd64.deb) ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for man-db ...
Setting up xfs (1:1.0.8-6) ...
Setting up X font server socket directory /tmp/.font-unix...done.
Starting X font server: xfs.
```

---

### Post by oregonbob on 2010-10-01
> **niteshifter said:**
> Hi,

tasksel was doing what it was instructed to do. I will say this: It takes some getting used to ;)

And how would you do that, without doing damage?


Then tasksel is supposed to have a long list of users who accidentally remove and destroy their systems? I don't think so. Simple fix: if any program is about to remove a bunch of packages when you give it a command to *install*, it should by default inform the user of packages to be removed. You could have a force option for those who like living dangerously. As I pointed out apt-get has the same flaw. There should be no program that you tell it to *install* and it proceeds to *remove* large numbers of packages *without warning*.

I understand the great advantages of tasksel. That is why I used it. It just has a serious flaw in design. If you want proof of the flaw, just [Google]("http://www.google.com/search?source=ig&hl=en&rlz=&q=tasksel+launchpad+bug") words "tasksel launchpad bug" and there are [many more]("http://www.google.com/search?source=ig&hl=en&rlz=&=&q=tasksel+bug+removed+deleted&btnG=Google+Search&aq=f&aqi=&aql=&oq=&gs_rfai="). This sort of crap turns people away from ubuntu/linux forever and go back to windows.

---

### Post by psusi on 2010-10-01
> **oregonbob said:**
> As I pointed out apt-get has the same flaw. There should be no program that you tell it to *install* and it proceeds to *remove* large numbers of packages *without warning*.

No, it does not.  It tells you EXACTLY what it is going to install or remove and asks if you want to continue.  If you try to install something that conflicts with something else, then it tells you it is going to have to remove the something else.  If you say go ahead, then you had your warning.

---

### Post by oregonbob on 2010-10-01
> **NightwishFan said:**
> It did not here on lucid. apt-get should always warn you.


I did "apt-get install xfs" and it completely removed gnome and gnome apps without warning. I couldn't believe what happened on tasksel yesterday was now happening again  on a different system and apt-get. I sat here in disbelief as I watched:
[COLOR="Blue"]Removing ....
Removing ....
Removing ....[/COLOR]

At least on this pc it still had network and I used "apt-get install ubuntu-desktop" to return to almost normal.
Did you have gnome installed when you ran that command?

---

### Post by NightwishFan on 2010-10-01
Yes sirre oregon bob. I am not doubting you, but it has always warned me.

---

### Post by oregonbob on 2010-10-01
> **psusi said:**
> No, it does not.  It tells you EXACTLY what it is going to install or remove and asks if you want to continue.  If you try to install something that conflicts with something else, then it tells you it is going to have to remove the something else.  If you say go ahead, then you had your warning.

Now you have me wondering, I may have ignored the single line that states "x packages installed, x packages to be removed" because I don't specifically remember what it said. I am used to having it install what I say to install and not remove a long list of critical applications including all networking and remote access.

Update: No, I'm not crazy, just lookat results of Googling "tasksel launchpad bug" and similar searches. Lots of users describe same symptoms.

---

### Post by lisati on 2010-10-01
> **NightwishFan said:**
> Yes sirre oregon bob. I am not doubting you, but it has always warned me.

It is possible that we're getting different mileage out of any warnings issued. My experience is that sometimes you do get a chance to say "no", and sometimes you don't. After using Ubuntu for over 3 years, I haven't figured out the pattern yet.

---

### Post by psusi on 2010-10-01
> **lisati said:**
> It is possible that we're getting different mileage out of any warnings issued. My experience is that sometimes you do get a chance to say "no", and sometimes you don't. After using Ubuntu for over 3 years, I haven't figured out the pattern yet.

The pattern is whether or not it does ONLY what you said to.  If you say install package x, and that's all it's going to do, then it does't bother asking.  If it realizes it needs to install packages y, z, and remove package d, then it stops and asks if that's ok.

---

### Post by jtarin on 2010-10-01
> **lisati said:**
> It is possible that we're getting different mileage out of any warnings issued. My experience is that sometimes you do get a chance to say "no", and sometimes you don't. After using Ubuntu for over 3 years, I haven't figured out the pattern yet.
That's why I have been accustomed to using Synaptic.....no surprises.

---

### Post by mc4man on 2010-10-01
> My experience is that sometimes you do get a chance to say "no", and sometimes you don't.
I would think that if any add. packages (dep.'s and or recommends) are to be installed you'd need to confirm.
(removals always require confirm

As far as tasksel - I can't see it doing anything other than requested, but because of the -y option it's going to proceed no matter what 
(to a point - Ex.
If I run 
sudo apt-get -y remove ubuntu-desktop^  it would fail here due to broken packages (nothing removed) though I could see it proceeding on some installs 

It would seem in most cases issues with tasksel are probably user errors

---

### Post by oregonbob on 2010-10-01
> **mc4man said:**
> It would seem in most cases issues with tasksel are probably user errors

I keep seeing these crop up... if you google "tasksel launchpad bug remove" you will find at least one report that was confirmed by testers and bumps. You will see many reports of similar bug reports.

I know on tasksel I selected INSTALL "DNS server". It ended up removing all gnome, network manager, all network settings, open-ssh and more.

---

### Post by lykwydchykyn on 2010-10-02
If I can take a half-informed, assumption-packed stab at what's going on here...

tasksel is part of the debian installer.  It was written initially to provide a user installing debian a quick way to set up a new machine for a specific purpose.

It's also from Debian, whose official package management front-end is aptitude.

tasksel is brought into Ubuntu for text-mode installations such as Ubuntu server, alternative install CD, minimal CD, netinstall, etc.  

For reasons that I don't understand (and let's not start another flamewar about), Ubuntu uses apt-get for package management rather than Debian's default aptitude.  

apt-get and aptitude track installation of packages differently; many people have learned the hard way that mixing the two can be disastrous.

I'm assuming (though I don't know) that tasksel in Ubuntu still uses aptitude for its backend.  

If so, that's going to cause problems like this.

So, to summarize for tldr:

 - tasksel most likely uses a packaging layer incompatible with the ones used in Ubuntu

 - tasksel's interface was designed for specific use during text-mode OS installation -- hence its inflexibility.

 - Most importantly, just because a tool is included, just because it CAN work, just because some  clever person in a blog/forum/howto-site was able to use it for a purpose -- doesn't mean it's a fool-proof recommended way of doing that thing.

---

### Post by psusi on 2010-10-02
I'm not sure where you get those ideas but both debian and ubuntu have apt-get and aptitude and they both rely on dpkg to track package installation and configuration.

---

### Post by mc4man on 2010-10-02
> know on tasksel I selected INSTALL "DNS server". It ended up removing all gnome, network manager, all network settings, open-ssh and more.
What version of ubuntu sre you using.
In essence tasksel is just running an apt-get command here with a couple of add. options (-q (quiet) and -y
so for dns-server it's no  different than 
```
sudo apt-get -q -y install  dns-server^
```
or 
```
sudo apt-get -q -y remove  dns-server^
```

Obviously you could sub dns-server^ for any other task

---

### Post by mcduck on 2010-10-02
> **psusi said:**
> The pattern is whether or not it does ONLY what you said to.  If you say install package x, and that's all it's going to do, then it does't bother asking.  If it realizes it needs to install packages y, z, and remove package d, then it stops and asks if that's ok.

+1 one to this. This is exactly how I've seen apt-get to behave.

What comes to the idea of tasksel being intended for CLI use only or to be used with aptitude instead of apt-get, then why is it included in Synaptic? Just go to Edit->Mark Packages by Task and you get the same feature... Besides, it even lists plenty of desktop-related tasks, like all the Ubuntu Studio's tasks. :)

---

### Post by bilalakhtar on 2010-10-02
Probably you removed the ubuntu-desktop task?

Tasksel has always been helpful for me, and if you wanted to install dns-server this was a better way:

sudo tasksel install dns-server .

---

### Post by oregonbob on 2010-10-02
This morning I did a clean fresh install of 10.04 desktop, updated it and reboot a couple of times. I then ran "sudo tasksel" with no command line options. Then I selected a few packages being very careful. It installed 4 packages without flaw. Therefore my guess is that a certain set of circumstances trigger the erroneous removal of unrelated packages. I still don't believe it is user error--too many bug reports.

The system I had it trash was a Mint 8 ubuntu Karmic, so Mint 8 variant may have been an issue. But my best guess is that I selected/deselected unrelated packages and that caused the damage. This same bug has been reported and confirmed.

I'll still use tasksel. It is too important and time saving. I'll just be much more careful when I do. I would never do it on a client's computer or mission critical without thorough warning and attention. Design changes are needed. NO program should be given an INSTALL instruction and then have it REMOVE unrelated packages as a result.

---

### Post by lykwydchykyn on 2010-10-03
> **psusi said:**
> I'm not sure where you get those ideas but both debian and ubuntu have apt-get and aptitude and they both rely on dpkg to track package installation and configuration.

The difference is in the tracking of *how* a package was installed: either as an automatic dependency or as a manually specified installation.  This may have been recently fixed, but in the past I've seen many people run into problems going back and forth between the two because of this.

This article has some more info about it: [http://newbiedoc.berlios.de/wiki/Aptitude_-_using_together_with_Synaptic_and_Apt-get](http://newbiedoc.berlios.de/wiki/Aptitude_-_using_together_with_Synaptic_and_Apt-get)

---

