---
title: "Updgrade to 10.4 - is it safe?"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by itsols on 2010-05-07
I downloaded the iso of Ubuntu 10.04 LTS (Desktop version) a couple of days ago.

I'd like to know if anyone has had any issues upgrading from 8.04 straight to this new version. My laptop is an old Dell Inspiron 1150 with 512MB RAM.

Any advice would be highly valued.

Many thanks!

---

### Post by SlonUA on 2010-05-07
> **itsols said:**
> I downloaded the iso of Ubuntu 10.04 LTS (Desktop version) a couple of days ago.

I'd like to know if anyone has had any issues upgrading from 8.04 straight to this new version. My laptop is an old Dell Inspiron 1150 with 512MB RAM.

Any advice would be highly valued.

Many thanks!

It will not works !!!
U must upgrade from version to version: 8.04 -> 8.10 -> 9.04 -> 9.10 -> 10.04 .. but i'm not sure.

Better to use upgrade script (not ISO).
Try in terminal
```
$ do-release-upgrade
```

Please, provide output if issue occurs =)

---

### Post by philinux on 2010-05-07
Backup, backup and backup!

Since you have already downloaded the iso I would burn it and run the live cd. My preferred method would be a clean install with home on it's own partition.

You can then use the ext4 file system and of course it will install grub2 see link in my signature.

If you upgrade you will have a lot of download bandwidth and you'll still have the ext3 filesystem. The upgrade will install grub2 and some have encountered problems with this on dual boot windows systems.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

[http://ubuntuforums.org/showthread.php?t=1469475](http://ubuntuforums.org/showthread.php?t=1469475)

You could wait for the point release on July 29th for 10.04.1 which is shown on the maverick release schedule.
This should have more bugs fixed. Yes there are always bugs in any new release. ;)
[https://wiki.ubuntu.com/MaverickReleaseSchedule](https://wiki.ubuntu.com/MaverickReleaseSchedule)

In fact I think the 8.04 LTS will not automatically offer the upgrade until the point release.

---

### Post by philinux on 2010-05-07
> **SlonUA said:**
> It will not works !!!
U must upgrade from version to version: 8.04 -> 8.10 -> 9.04 -> 9.10 -> 10.04 .. but i'm not sure.

Better to use upgrade script (not ISO).
Try in terminal
```
$ do-release-upgrade
```

Please, provide output if issue occurs =)

Above is incorrect. 8.04 is an LTS therefore you can go LTS > LTS
And its ```
update-manager -d
```

---

### Post by Mr Nemo on 2010-05-07
Personally I think it's a better idea to do a fresh install of 10.04. Thats what I did and I've had no problems. Here is a link to an ubuntu help page with system requirements. [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

512 mb of ram is recommended. If the computer is older with lower specs you might want to check out xubuntu.

---

### Post by sports fan Matt on 2010-05-07
I plan to do a clean install once my lucid disk comes.  I never have had any luck burning cd's so I wait and use Backintime with it to restore my system.

---

### Post by muteXe on 2010-05-07
I really have no idea why people upgrade. Clean install is the way for me. Every single time.
Look at the threads of this forum. A lot of them start with "problems with <blah> during *upgrade*".

Backup, clean install, restore your data.

sorry for rant.

---

### Post by philinux on 2010-05-07
> **muteXe said:**
> I really have no idea why people upgrade. Clean install is the way for me. Every single time.
Look at the threads of this forum. A lot of them start with "problems with <blah> during *upgrade*".

Backup, clean install, restore your data.

sorry for rant.

I've had nothing but trouble with upgrades. Some people swear by it. YMMV.

I've got /home on it's own partition so reinstall is a doddle.

---

### Post by Naggobot on 2010-05-07
I have understood that you can not upgrade from desktop iso image i.e if the file name is in the form

```
[ubuntu-10.04-desktop-<architecture>.iso]("http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.iso.torrent")
```then you can only do fresh install. If you want to use iso image to upgrade you need to download the alternate installation cd i.e. the file name is of the form

```
[ubuntu-10.04-alternate-i386.iso]("http://releases.ubuntu.com/10.04/ubuntu-10.04-desktop-i386.iso.torrent")
```

Desktop install image does not offer the upgrade option. 

I downloaded the alternate image and used it and internet connection simultaneously to upgrade. This way I was able to torrent most of the upgrade. You can check my experiences from [here]("http://ubuntuforums.org/showthread.php?p=9212443#post9212443")

Info about alternate cd upgrades and upgrades in general

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

I think (not sure did not read now) this does not mention that with the alternate cd upgrade method you can use internet connection simultaneously with the CD so that relevant stuff is upgraded from the net so that install is up to date after upgrade.

---

### Post by lykwydchykyn on 2010-05-07
Safe is relative.

I upgraded a kiosk system I had here from 8.04 to 10.04.  Everything went well except for a MAJOR apt-hiccup with a flashplayer package that ended up requiring me to make some edits to a script in /var/cache/apt or something (it's been a week now, I forget what I did).

I worked through it and it's all fine, but it wasn't for the faint of heart.  Of course, my kiosks are not standard Ubuntu installs, but built up from a minimal install so that makes a difference.

The way I see it:
 - backup your data
 - Attempt an upgrade
 - If you run into problems you can't/don't want to deal with, do a fresh install.  

You have nothing to lose but a little time.

---

### Post by lashram on 2010-05-07
**I was using Ubuntu 9.04 and I use the update-manager -d  to upgrade to Lucid and the upgrade went smoothly. However I can relate my experience with this distro so far I have not had any major issues with this distro. I am very pleased with it thus far and all of my components worked out the box in this version of Ubuntu. In past distros I had to research and compile some of my drivers to get everything working. I did not mind having to do that because it is a learning experience and it helps you to get more familiar with Ubuntu and using the command line. I was a long time Windows user myself and a few years ago i started playing around with Ubuntu and I also purchased a Macbook and started using OSX. I would say give it a try using the Live CD first and see if you like it and feel comfortable using it. That way you will not have to reinstall your distro if something goes wrong or if you experience issues with it.  :guitar: **

---

### Post by itsols on 2010-05-07
I really appreciate all your views and experiences being shared.

Personally, I've had no hiccups upgrading so far - I've moved from 7.10 and so far on 8.04. Now I needed to move to 10.04 for several reasons and the main thing being that I need to run monodvelop just like it is on visual c# and move files between my ubuntu and other Windows boxes. Perhaps you know that monodevelop on 8.04 runs c# projects in a different format.

Now here are my other thoughts...

1. It is true that a fresh install is convenient in CERTAIN cases. But for me, I can't afford to put a whole day - I've got to install, configure all my settings (LAMP and the works), move my files/projects... It's too much. So upgrading is the best option.

2. I have so many custom settings and additional drivers - for example, my network settings, broadband connections, fonts, other applications... I certainly hope I'll not have to go through all those installation procedures just for an upgrade :)

3. Finally, I think it's great to see version 10.4 around. I remember how I was first introduced to version 5.05 some years ago!!! How time flies!

4. About the ext3 to ext4... After all these years of using Ubuntu, I still feel like a newbie! I really don't know much of the inner workings of this OS unlike my old Win XP (that sits on the other partition)... Windows stays there since it's been there with my laptop and occasionally I need to do some stuff on VB. Other than that, Ubuntu has been my main development machine and multi-purpose companion :)

So, I hope I can get this right the first time without disrupting everything else. I think in summary, I'll burn the ISO and try the CD.

Thank you everyone for your superb advice!

---

### Post by madjr on 2010-05-07
DONT UPGRADE

install side by side :)

[http://dedoimedo.com/computers/ubuntu-install.html](http://dedoimedo.com/computers/ubuntu-install.html)

[http://youtube.com/watch?v=Z0tNpt5RZYI](http://youtube.com/watch?v=Z0tNpt5RZYI)

---

### Post by itsols on 2010-05-07
Those who upgraded, did you have any issue? From what version did you upgrade (or move to 10.4)?

---

### Post by Calash on 2010-05-07
> **itsols said:**
> Those who upgraded, did you have any issue? From what version did you upgrade (or move to 10.4)?

9.10 -> 10.04 on 3 systems total.

Work PC has issues due to being behind a proxy that caused some of the updates not to download combined with letting the computer go to sleep.  Fixed the issues and the system is running fine.

Laptop had no issues and works great

Personal Desktop went fine as well.  Did a reload during Beta2 for ISO testing.

---

### Post by itsols on 2010-06-06
Ok, first, say hi to me - NEAR DEATH EXPERIENCE :)

Initially, I had downloaded the iso to do a fresh install. At that time I wasn't sure about the actual difference between that and the alternate install. So I waited... until, yesterday.

I got this urge to upgrade. So I followed the instructions [HERE]("http://www.ubuntu.com/desktop/get-ubuntu/upgrade") and the journey began...

After about 11 (yes, eleven) hours of downloading on my Wimax link, the installation began... Everything went off well and around 99% of completion, I got an alert. It was something about the 'flashplugin' being in a 'very bad condition'. As a gesture of appreciation, I decided to report the error. The moment I hit send, the installation came to an abrupt halt.

I wasn't sure if the setup was complete. So I tried changing the desktop themes to see if things had gone ahead but nothing showed differently.

Then came bigger trouble. I restarted. This time round, I noticed that the kernel had in fact got updated. But the system wouldn't boot beyond the initial splash screen.

After much digging and assistance from 'an expert', I learnt that THREE issues kept this from working right.

1. The graphics card on my Inspiron 1150 laptop had issues with 10.04
2. The kernel of the upgrade was incompatible
3. The flashplugins were interfering with the setup as well.

I can't explain all steps here but you have to deal with each of them one at a time.

Well, in all, I think the entire process took around 20 hours (i.e., from the first commands to upgrade).

And voila! I'm back, with no data loss!

---

