---
title: "Synaptic generates error 404 Not Found"
date: 2009-08-25
forum: New to Ubuntu
---

### Post by Pierrot Lafouine on 2009-08-25
Hi

I'm trying to download libsdl1.2-dev on Ubuntu 7.10, without success.
I'm doing this command :
```
sudo apt-get install libsdl1.2-dev
```
And I'm getting this error :

```
Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/libglu1-xorg-dev_7.2-5ubuntu13_all.deb 404 Not Found [IP: 91.189.88.40 80]
```

Synaptic is getting same errors when trying to install same lib.
What's wrong ?

Thanks

Pierre.

---

### Post by zvacet on 2009-08-25
Change server in system>admin software sources.

---

### Post by Pierrot Lafouine on 2009-08-25
I don't have this menu.
I have Ubuntu 7.10
Any other idea ?
Thanks
Pierre

---

### Post by j.bell730 on 2009-08-25
Go to **Synaptic** > **Settings** menu > **Repositories**, and in the "**Download from**" menu, select "**Other**", and click "**Select Best Server**".

---

### Post by Pierrot Lafouine on 2009-08-25
Hi
I don't have menu Download from.
What can I do ?

Pierre

---

### Post by RedRat on 2009-08-25
The problem may be even more fundamental. It may well be that all support for 7.10 has stopped and the url is no longer valid. I upgraded from 7.10 to 8.04 LTS and had some backport sites in my repo list. I kept getting that same type error. My advice is to upgrade to 8.04 LTS or a more recent version 9.04. However, as you can see from many comments here, 9.04 can have some issues with your system.

---

### Post by Pierrot Lafouine on 2009-08-25
Thanks
How can I confirm this ?  This is serious issue.
We are in the beginning of application deployment and I will upgrade if only needed.

Pierre

---

### Post by RedRat on 2009-08-25
> **Pierrot Lafouine said:**
> Thanks
How can I confirm this ?  This is serious issue.
We are in the beginning of application deployment and I will upgrade if only needed.

Pierre

Well first off, use your browser and type in that url:
[http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/libglu1-xorg-dev_7.2-5ubuntu13_all.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/libglu1-xorg-dev_7.2-5ubuntu13_all.deb)

And you will see that it is non existent at:
[http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/](http://us.archive.ubuntu.com/ubuntu/pool/main/x/xorg/)

It appears that libglu1-xorg-dev_7.2-5ubuntu13_all.deb is just not there. 

Please take a look at the discussion at:
[http://ubuntuforums.org/showthread.php?t=1238623](http://ubuntuforums.org/showthread.php?t=1238623)

Plow through it all and you will see my comments and problems and there you should also see the comments about Gutsy (7.10). If you are planning some kind of deployment, I would strongly urge you to upgrade to 8.04LTS because support should be around until 2010. Version 7.10 was not a long term support or LTS version, I believe that the other LTS was 6.04. You have two choices, either upgrade to 8.04LTS or try 9.04 and take your chances that all will be well.

---

### Post by Pierrot Lafouine on 2009-08-25
Ok thanks,
I'm downloading 8.04 LTS.  Can I upgrade from the ISO CD or it will install fresh OS ?  
I'm guessing I can upgrade from CD, but I had a bad experience once with a Windoz CD just overwrote all registry without telling.*&^!%$^%$%^

Thanks

---

### Post by RedRat on 2009-08-25
> **Pierrot Lafouine said:**
> Ok thanks,
I'm downloading 8.04 LTS.  Can I upgrade from the ISO CD or it will install fresh OS ?  
I'm guessing I can upgrade from CD, but I had a bad experience once with a Windoz CD just overwrote all registry without telling.*&^!%$^%$%^

Thanks

Well before doing anything, BACKUP anything that you cannot afford to loose!!!!! That is true for whatever OS you are using. A word to the wise.

When I did my upgrade, I did it from Synaptic because it was set up to show upgrades to the system. It has been over a year since I did that but I recall that there was a button to upgrade to the latest LTS version, which was the only one available at that time. It should work from the disk, but perhaps others here might have some experience.

A bit of a warning, you MIGHT find some problems with the graphics. There was some kind of change in the kernel between 7.10 and 8.04. However, that might have been taken care of in the release you are now downloading. This has to do with the nVidia and ATI cards. Be prepared to use EnvyNG to install the proper driver for your graphic cards. You may get off scott free though. But be prepared just in case. I say this because I had these graphic problems with my conversion. It was not a disaster but really annoying, the best way to describe it.

---

### Post by zvacet on 2009-08-26
Sorry for late response and overlook.If you want to upgrade your system it will be good idea to have separate home partition.In that case your data/files will be safe,but you can do backup just in case.If you want separate home follow [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.after that edit your source list with command 

```
gksudo gedit /etc/apt/sources.list
```

replace all lines with **archive.ubuntu.com** with **old-releases.ubuntu.com.**

For example 
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted

to 

deb [http://old-releases.ubuntu.com./ubuntu/](http://old-releases.ubuntu.com./ubuntu/) gutsy main restricted


```
sudo apt-get update && sudo apt-get upgrade
```

you can do upgrade with alternate CD.In that case if something goes wrong you always have CD fro fresh install.

---

### Post by slakkie on 2009-08-26
You could upgrade following the EOL upgrade guide.

---

### Post by 3rdalbum on 2009-08-26
> **Pierrot Lafouine said:**
> Thanks
How can I confirm this ?  This is serious issue.
We are in the beginning of application deployment and I will upgrade if only needed.

Believe me, if you are deploying any operating system on your computers, you don't want to deploy one with known security flaws that won't get patched because the OS is end-of-life.

Definitely run Hardy unless you have machines too new to take it.

---

### Post by Pierrot Lafouine on 2009-12-23
> **3rdalbum said:**
> Believe me, if you are deploying any operating system on your computers, you don't want to deploy one with known security flaws that won't get patched because the OS is end-of-life.

Ok, we migrate our application on an other up-to-date server.
I want to upgrade my computer from 7.10 to 8.04 LTS.
I'm following this guide ; [https://help.ubuntu.com/community/EOLUpgrades/Gutsy](https://help.ubuntu.com/community/EOLUpgrades/Gutsy)

As per guide, I tried code : sudo do-release-upgrade
This is the output : sudo: do-release-upgrade: command not found

What do I do with that ?
Thanks

---

### Post by Pierrot Lafouine on 2009-12-23
Quote:
Originally Posted by 3rdalbum View Post
Believe me, if you are deploying any operating system on your computers, you don't want to deploy one with known security flaws that won't get patched because the OS is end-of-life.
Ok, we migrate our application on an other up-to-date server.
I want to upgrade my computer from 7.10 to 8.04 LTS.
I'm following this guide ; [https://help.ubuntu.com/community/EOLUpgrades/Gutsy](https://help.ubuntu.com/community/EOLUpgrades/Gutsy)

As per guide, I tried code : sudo do-release-upgrade
This is the output : sudo: do-release-upgrade: command not found

What do I do with that ?
Thanks

---

### Post by Pierrot Lafouine on 2009-12-23
> :
Originally Posted by 3rdalbum View Post
Believe me, if you are deploying any operating system on your computers, you don't want to deploy one with known security flaws that won't get patched because the OS is end-of-life.
Ok, we migrate our application on an other up-to-date server.
I want to upgrade my computer from 7.10 to 8.04 LTS.
I'm following this guide ; [https://help.ubuntu.com/community/EOLUpgrades/Gutsy](https://help.ubuntu.com/community/EOLUpgrades/Gutsy)

As per guide, I tried code : sudo do-release-upgrade
This is the output : sudo: do-release-upgrade: command not found

What do I do with that ?
Thanks

---

### Post by Geoff918 on 2009-12-23
Maybe try the following: (It might be a newer command, but worth a shot--never used Ubuntu that old)

sudo apt-get dist-upgrade

---

### Post by wojox on 2009-12-23
Do you have these packages installed:

```
sudo aptitude install update-manager update-manager-core
```

---

### Post by Pierrot Lafouine on 2009-12-23
> **wojox said:**
> Do you have these packages installed:

```
sudo aptitude install update-manager update-manager-core
```

Look like it worked.
Thanks

---

### Post by Pierrot Lafouine on 2009-12-23
Huuumm
How do I install a clean /etc/apt/source.list file ?
The file has now plenty commented stuff (old-releases.ubuntu.com/ubuntu/ gutsy) etc...
Maybe its working, but I would to finish the job

Thanks

---

### Post by orlox on 2009-12-23
The instructions in comment #18 do not perform an upgrade, it just installs the update-manager. You should have that installed by default, so that command wont do much.

To perform an upgrade, try running:
```

update-manager -d

```

The update manager should appear, with a message telling you there's another version available to upgrade. I'm not 100% sure this will work as it should though, cause I don't have experience with versions that are pass it's lifetime.

---

### Post by orlox on 2009-12-23
It seems I wasn't right after all...

The correct procedure is described [here]("https://help.ubuntu.com/community/EOLUpgrades/Gutsy"). Dont worry about a lot of additional files in /etc/apt, just ensure that your sources.list file is the one shown there.

---

### Post by wojox on 2009-12-23
[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

---

### Post by Pierrot Lafouine on 2009-12-24
Huuumm
How do I install a clean /etc/apt/source.list file ?
The file has now plenty commented stuff (old-releases.ubuntu.com/ubuntu/ gutsy) etc...
Maybe its working, but I would to finish the job, and clean the file.  To do that, do I removed commented stuff ?

Thanks

---

### Post by orlox on 2009-12-24
As mentioned in the above link I gave you, it's enough for your sources.list to be this:

> 
## EOL upgrade sources.list
# Required
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-updates main restricted universe multiverse
deb [http://old-releases.ubuntu.com/ubuntu/](http://old-releases.ubuntu.com/ubuntu/) gutsy-security main restricted universe multiverse


Just delete everything, and replace it by that.

---

### Post by Pierrot Lafouine on 2009-12-24
Ok thanks, sorry for the doublon, I didn't refresh the good web page, so I didn't see your answers...
Thanks all, I feel better having a supported distro now

---

