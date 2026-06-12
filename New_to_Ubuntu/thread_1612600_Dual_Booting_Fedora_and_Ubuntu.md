---
title: "Dual Booting Fedora and Ubuntu"
date: 2010-11-03
forum: New to Ubuntu
---

### Post by oo1005 on 2010-11-03
I've managed to get Fedora 14, Ubuntu 10.10 & Win 7 installed, however when I'm in Fedora I can't get Ubuntu to boot, so I 'fixed' the mbr using the Ubuntu Live USB and now I'm back into Ubuntu, what do I need to do to be able to select Fedora from the boot menu?

I'm completely new to Linux and not sure which I'll end up using so would like to have the option of both for the time being...

Thanks!

Phil

---

### Post by Rubi1200 on 2010-11-03
What order did you install the systems?

```
sudo update-grub
``` should recognize and add all OS's to the boot menu and allow you to choose from them at startup (copy/paste from the terminal and post the output if you are not sure).

---

### Post by hot_rod_hippie on 2010-11-03
You need to make sure there is an entry in your boot loader configuration (/boot//grub/grub.cfg) for all OS's you want to boot.
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2) gives a bunch of info.

To make your life easier, I would recommend installing a virtual server (like VirtualBox) within Windows 7. You can then create individual virtual machines for any flavor of Linux you want to try without re-booting every time.

Best of luck,
Hippie

---

### Post by oo1005 on 2010-11-03
> **Rubi1200 said:**
> What order did you install the systems?

```
sudo update-grub
``` should recognize and add all OS's to the boot menu and allow you to choose from them at startup (copy/paste from the terminal and post the output if you are not sure).

Excellent - that looks like its worked!

Thanks..

---

### Post by Rubi1200 on 2010-11-03
> **oo1005 said:**
> Excellent - that looks like its worked!

Thanks..
You are more than welcome :)

---

### Post by beew on 2010-11-03
Good info, as I am also interested in setting up Ubuntu-Fedora dual boot.

hot_rod_hippie
> To make your life easier, I would recommend installing a virtual server  (like VirtualBox) within Windows 7. You can then create individual  virtual machines for any flavor of Linux you want to try without  re-booting every time.
I don't think running Linux within Windows is what the OP wants. This is not really giving Linux its due as it would be dependent on Windows. Besides virtualization can be slow so running Linux in a virtual environment may not give a true picture of what it is capable of. If s/he wants to try different Linux flavour it is probably best to install into an external hard drive.

---

### Post by Rubi1200 on 2010-11-03
> **beew said:**
> Good info, as I am also interested in setting up Ubuntu-Fedora dual boot.

Hi beew,
in my experience it is better to install Fedora first and then Ubuntu. But, it probably works the other way as well.

Hope this helps.

---

### Post by beew on 2010-11-03
> **Rubi1200 said:**
> Hi beew,
in my experience it is better to install Fedora first and then Ubuntu. But, it probably works the other way as well.

Hope this helps.


Hi, I have already installed Ubuntu, so it has to be the other way around.

---

### Post by Rubi1200 on 2010-11-03
If you like your current setup, install Fedora and tell it to NOT install its bootloader.

When finished, boot back into Ubuntu and run ```
sudo update-grub 
```which should then pick it up and allow you to choose between them at the GRUB menu.

---

### Post by amjjawad on 2010-11-03
I have 9 OS's installed on my PC.
IMHO and from a personal experience, the best thing is to:

1) Install Windows
2) Install Ubuntu
3) Install Fedora

Fedora has a nice feature during the installation process. It asks you which OS do you want to keep as the default one. Same like Ubuntu, it also gives you an option to install its boot loader either in the MBR or the same partition where Fedora is installed.
As per Fedora's installation Guide and from my own experience, it's always recommended to install Fedora's boot loader in the same partition where Fedora is installed. For example, if you want to install it in sda6, then the boot loader of Fedora should be there AS LONG AS Fedora is not the only OS on your machine. That's what the Installation Guide said. I read it all before installing Fedora. It's so nice and very helpful.

In my machine, I set Ubuntu's GRUB2 to be the main boot loader. Now, if I want to do anything, I can simply update the GRUB2 menu with a single command:

```
sudo update-grub

```

Fedora 13 was using GRUB Legacy not GRUB2 but honestly I didn't read about Fedora 14 yet. Perhaps I need to boot into Fedora and update it :)

All the best :)

---

### Post by beew on 2010-11-03
Thanks my friend. 9 OSes ? Wow.

I currently have a machine with windows xp and ubuntu dual boot.  I need to do the following:

1) Back up the Ubuntu partition

2) Check that the backup works

3) Get rid of XP

4) Install Fedora in the partition where XP was installed.

I am still looking for ways to do 1) and 2), actually mainly 2) I don't know how I can test that a backup works without actually trying to restore it. But to where?

---

### Post by amjjawad on 2010-11-03
> **beew said:**
> Thanks my friend. 9 OSes ? Wow.

I currently have a machine with windows xp and ubuntu dual boot.  I need to do the following:

1) Back up the Ubuntu partition

2) Check that the backup works

3) Get rid of XP

4) Install Fedora in the partition where XP was installed.

I am still looking for ways to do 1) and 2), actually mainly 2) I don't know how I can test that a backup works without actually trying to restore it. But to where?

Are you trying to backup /home or everything including / as well?
Installing Ubuntu doesn't take much time IMHO so the easiest thing to backup /home. I would do that instead of doing more steps :)

For me, I don't have much settings and stuff so I would just copy /home to another partition and that's all. Perhaps I missed something but I don't need to do it right now.
Only with Ubuntu I have /home partition. As for the other OS's, I don't have /home. I keep XP just in case but I've never used it for a month or so.

---

### Post by coffeecat on 2010-11-03
> **amjjawad said:**
> I have 9 OS's installed on my PC.
IMHO and from a personal experience, the best thing is to:

1) Install Windows
2) Install Ubuntu
3) Install Fedora

Fedora has a nice feature during the installation process. It asks you which OS do you want to keep as the default one.

Unfortunately, the Fedora devs in their infinite wisdom do not give the Fedora installer the ability to detect any other OS apart from Windows. So that feature of choosing the default OS in the grub menu is merely a choice between Fedora and Windows. Other distros might just as well not exist. I installed Fedora 14 this morning and I can confirm that this unsocial behaviour is unchanged from what I previously experienced in Fedora 13, Fedora 12, 11, 10, 9.... :yawn:.... 8, 7, 6, 5.....  ZZzzz.

So, if you install Fedora last in a Fedora, Ubuntu, Windows tri-boot you have to either....

Manually add an Ubuntu entry to the grub menu during the Anaconda setup. Or...

Leave the grub settings in Anaconda as they are, install Fedora's legacy grub to the mbr and manually edit menu.lst to include Ubuntu after you have finished installing. Or...

Install Fedora's grub to the partition boot sector of Fedora's root or boot partition and then run 'sudo update-grub' in Ubuntu to get a Fedora menu entry in Ubuntu's grub.

Anaconda, by the way, is the name of Fedora's installer and what I want to know is: if the installers for Ubuntu, Mepis, Suse, Mandriva, and some other distros I have probably forgotten can detect other Linux distros and set up a multi-boot boot menu, what problem do the Fedora devs have? Not a technical one, I am sure.

---

### Post by beew on 2010-11-03
> **amjjawad said:**
> Are you trying to backup /home or everything including / as well?
Installing Ubuntu doesn't take much time IMHO so the easiest thing to backup /home. I would do that instead of doing more steps :)

For me, I don't have much settings and stuff so I would just copy /home to another partition and that's all. Perhaps I missed something but I don't need to do it right now.
Only with Ubuntu I have /home partition. As for the other OS's, I don't have /home. I keep XP just in case but I've never used it for a month or so.


I am trying to back up everything, basically cloning the partition.

---

### Post by beew on 2010-11-03
coffeecat

Hmmm.. good to keep that in mind.

---

### Post by garvinrick4 on 2010-11-03
If you have a Ubuntu install with grub2 installed already when you install Fedora just choose not to install grub-legacy when installing Fedora. I believe their install system is called anaconda if I remember right like most offshoots of RedHat . Once installed go into your grub2 install at first boot and sudo update-grub and os-prober will find and you are set will be in grub-config now and boot menu. I found same with RedHat beta 6 and same with OpenSUSE any of the major grub-legacy Operating Systems has a way on not installing their grub. Sure makes things a whole lot easier on mbr than installing grub-legacy and then overwriting it with grub2. This is not theory but in practical application.

---

### Post by amjjawad on 2010-11-03
> **coffeecat said:**
> Unfortunately, the Fedora devs in their infinite wisdom do not give the Fedora installer the ability to detect any other OS apart from Windows. So that feature of choosing the default OS in the grub menu is merely a choice between Fedora and Windows. Other distros might just as well not exist. I installed Fedora 14 this morning and I can confirm that this unsocial behaviour is unchanged from what I previously experienced in Fedora 13, Fedora 12, 11, 10, 9.... :yawn:.... 8, 7, 6, 5.....  ZZzzz.

So, if you install Fedora last in a Fedora, Ubuntu, Windows tri-boot you have to either....

Manually add an Ubuntu entry to the grub menu during the Anaconda setup. Or...

Leave the grub settings in Anaconda as they are, install Fedora's legacy grub to the mbr and manually edit menu.lst to include Ubuntu after you have finished installing. Or...

Install Fedora's grub to the partition boot sector of Fedora's root or boot partition and then run 'sudo update-grub' in Ubuntu to get a Fedora menu entry in Ubuntu's grub.

Anaconda, by the way, is the name of Fedora's installer and what I want to know is: if the installers for Ubuntu, Mepis, Suse, Mandriva, and some other distros I have probably forgotten can detect other Linux distros and set up a multi-boot boot menu, what problem do the Fedora devs have? Not a technical one, I am sure.

Hmmm, haven't tried that yet. I installed everything then installed Ubuntu 10.04 and chose to install GRUB2 in the MBR so that it could boot all the other and be the main boot loader.

This is really odd. I might post on Fedora's forum to discuss that issue but I don't have time with Fedora now :P

Thanks for the information, mate :)

---

### Post by amjjawad on 2010-11-03
> **beew said:**
> I am trying to back up everything, basically cloning the partition.

What I would do is just copy - paste my data in /home into another partition and that's all unless someone else might disagree with this process.

---

### Post by coffeecat on 2010-11-03
In fact, there's a fourth option. With my third one.... 

> **coffeecat said:**
> Install Fedora's grub to the partition boot sector of Fedora's root or boot partition and then run 'sudo update-grub' in Ubuntu to get a Fedora menu entry in Ubuntu's grub.

... you don't really need to install Fedora's legacy grub at all.

The fourth  is to install Fedora's grub to the partition boot sector of Fedora's root or boot partition - that is, elect to install grub to, say, sda6 if sda6 is your Fedora root partition (or boot if you've set up a separate boot partition). Then you add a chainloading stanza for Fedora in Ubuntu's /etc/grub.d/40_custom and run sudo update-grub. That's what I did this morning. You also need to comment out the 'hiddenmenu' line in Fedora's menu.lst and increase the timeout from the absurdly short default.

---

### Post by amjjawad on 2010-11-03
Fedora has two main options to install the boot loader of Fedora:

1- MBR
2- The first sector of the installation partition

As per their installation guide (so busy now to find the link :P), it's recommended to use option 1 in case Fedora is installed first or it's installed solo without any other OS.
The 2nd option is recommended in dual booting or to be more accurate when another OS is installed before Fedora.

I would always use GRUB2 as it's much easier for me. It's not that I'm lazy but why wasting so much time while I could do everything with 3 magical words? "sudo update-grub" :)

---

### Post by garvinrick4 on 2010-11-03
> **amjjawad said:**
> What I would do is just copy - paste my data in /home into another partition and that's all unless someone else might disagree with this process. I agree to just backing up /home or /data any of your personals. If by remote chance that you for some reason install new OS into the wrong partition or something should not have a problem. Only takes a jiffy to set up new Ubuntu install. But I do agree with always keeping backup of /home at all times. I keep my backups on external and update it every week or so.

---

### Post by amjjawad on 2010-11-03
> **garvinrick4 said:**
> But I do agree with always keeping backup of /home at all times. I keep my backups on external and update it every week or so.

That's why I have two external HDD (1TB and 250GB) both are WD :)

I bought the first (250GB) few years ago and I had to get new one because I have more than 500 movies and lots of other files so 1TB is a must :)

---

### Post by beew on 2010-11-03
> **amjjawad said:**
> What I would do is just copy - paste my data in /home into another partition and that's all unless someone else might disagree with this process.

Normally that would be the case. But let's say my / partition is a bit unusual. :) I have lots of PPAs and I am not averse to mixing repos once in a while to get the most update versions of some softwares (I got into dependencies problems but I always managed to get myself out of them so far.:)) 

 I also have some third party apps which are not installed in the /home folder (in /usr/local/bin)  

So my Lucid installation is highly tweaked and highly customized and that's why I would rather keep it than to make a fresh install of Maverick even though Maverick is very nice.
On the other hand I have very little personal data of value (I don't store them here knowing that I would make changes to the OSes) so I don't really care if the /home folder is wiped out.

---

### Post by amjjawad on 2010-11-03
> **beew said:**
> Normally that would be the case. But let's say my / partition is a bit unusual. :) I have lots of PPAs and I am not averse to mixing repos once in a while to get the most update versions of some softwares (I got into dependencies problems but I always managed to get myself out of them so far.:)) 

 I also have some third party apps which are not installed in the /home folder (in /usr/local/bin)  

So my Lucid installation is highly tweaked and highly customized and that's why I would rather keep it than to make a fresh install of Maverick even though Maverick is very nice.
On the other hand I have very little personal data of value (I don't store them here knowing that I would make changes to the OSes) so I don't really care if the /home folder is wiped out.

In that case, you need an advice from someone with more experience than me :)
I've never done a backup in Ubuntu as I did in Windows. In fact, the reason why I don't care much is I don't do any customizations in Linux at all. I keep these OS's to learn, that's all :)
Once I'll gain more experience, then the real fun will begin :)

---

