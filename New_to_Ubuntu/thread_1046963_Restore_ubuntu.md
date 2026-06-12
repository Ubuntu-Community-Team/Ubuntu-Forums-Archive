---
title: "Restore ubuntu"
date: 2009-01-21
forum: New to Ubuntu
---

### Post by steve228 on 2009-01-21
I am dual booting Vista[horrible p.o.s] and ubuntu... I tried to upgrade to open office 3.0 and wound up removing open office altogether... i tried every "how-to" trying to reinstall either version and nether will work... is there any way to restore back to defaults or how can I delete the ubuntu partition and just reinstall the ubuntu?

---

### Post by ridgeland on 2009-01-21
Did you try Synaptic to fully remove the old openoffice?  And try to install 2.4 again?

It's easy to reinstall Ubuntu over the same partition.  Hope it's not necessary.

---

### Post by emarkd on 2009-01-21
You can just reinstall Ubuntu on the same partition using the live cd.  But you should be able to get openoffice working again if you wanna try.  How are you trying to reinstall it?  Synaptic?  apt-get?  What sort of errors do you get?

---

### Post by steve228 on 2009-01-21
yes i used synaptic and it had a ton of different checkboxes and i went through everyone and marked for complete removal... when i try to install openoffice from synaptic it says that i am about to install software that is not authenticated, then brings up a list of what wasn't installed

---

### Post by steve228 on 2009-01-21
here is one output 

```

sudo apt-get install openoffice.org
The following packages have unmet dependencies:
  openoffice.org: Depends: openoffice.org-core (= 1:3.0.1~rc1-2ubuntu2~intrepid1) but it is not going to be installed
                  Depends: openoffice.org-writer but it is not going to be installed
                  Depends: openoffice.org-calc but it is not going to be installed
                  Depends: openoffice.org-impress but it is not going to be installed
                  Depends: openoffice.org-draw but it is not going to be installed
                  Depends: openoffice.org-math but it is not going to be installed
                  Depends: openoffice.org-base but it is not going to be installed
                  Depends: openoffice.org-report-builder-bin but it is not going to be installed
                  Depends: openoffice.org-officebean but it is not going to be installed
                  Depends: openoffice.org-writer2latex but it is not going to be installed
          

```

when i try to use synaptic i mark openoffice.org to be installed and it says im about to install unauthenticated software then:

```

openoffice.org:
 Depends: openoffice.org-core but it is not going to be installed
 Depends: openoffice.org-writer but it is not going to be installed
 Depends: openoffice.org-calc but it is not going to be installed
 Depends: openoffice.org-impress but it is not going to be installed
 Depends: openoffice.org-draw but it is not going to be installed
 Depends: openoffice.org-math but it is not going to be installed
 Depends: openoffice.org-base but it is not going to be installed
 Depends: openoffice.org-report-builder-bin but it is not going to be installed
 Depends: openoffice.org-officebean but it is not going to be installed
 Depends: openoffice.org-writer2latex but it is not going to be installed
 Depends: liblucene2-java but it is not going to be installed

```

---

### Post by ridgeland on 2009-01-21
Sometimes it's easier to reinstall than to troubleshoot.  What do you have to lose?  Data in Linux not in Windows?  A good back up system?

See
[http://www.linuxquestions.org/questions/debian-26/how-do-i-get-apt-get-to-completely-uninstall-a-package-237772/](http://www.linuxquestions.org/questions/debian-26/how-do-i-get-apt-get-to-completely-uninstall-a-package-237772/)
it talks about using apt-get to remove the old stuff.

---

### Post by inspriation26 on 2009-01-21
Dont worry about the non authenticated software. It did that to me too one time. Just install it and everything will be fine. No need to reinstall evertime you mess up. Alright?

---

### Post by steve228 on 2009-01-22
the problem is it won't install the unauthenticated even if i wanted to.. 

and i tried using

```

sudo apt-get --purge remove openoffice.org

```

and came back saying it isn't installed....

```

E: Broken packages
steve@steve-laptop:~$ sudo apt-get --remove purge openoffice.org-core
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package openoffice.org-core is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```



i wound up removing a few packages... but still cannot install open office 2.4 or 3.0.... 

any ideas

---

### Post by L1nchp1N on 2009-01-22
One thing you could try on the installation front is this:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml]("http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml")

I used it myself and it seems to work fine.

---

### Post by jimv on 2009-01-22
This will get you fixed.

Make sure that you have this repository enabled (it contains the OpenOffice 3 packages):

deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main

If you don't have that, you can follow the instructions on this site to get going:

[http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml](http://news.softpedia.com/news/How-To-Install-OpenOffice-org-3-0-in-Ubuntu-8-10-96449.shtml)

---

### Post by blackmail on 2009-01-22
Don't quite know how to help in the openoffice issue but if you want a clean reinstall when the partitioner starts after booting into the live cd, you can select that the partition on wich you install ubuntu will be deleted, but you can just simply format it.

---

### Post by ridgeland on 2009-01-22
My approach is to first try troubleshooting but if that is a dead end I just copy my "base" copy of Ubuntu from another partition, a few tweaks (fstab, menu.lst, grub-install for chain) and I'm running again daring to try other uncertain things.

You don't have a base copy so before reinstalling make sure you have a copy of all the data (mp3, jpg, odt etc) from your Linux partition, many would say copy /home/yourID for directories like .mozilla which holds your firefox bookmarks.

Also downloads from synaptics are saved in
/var/cache/apt/archives/
Copy that to a safe place.  Then the first thing after the new install is booting is copy in the archives.
sudo cp -a /mybackup/archives/* /var/cache/apt/archives/
That will save you the re-downloading in synaptic (FrozenBubble, smc Maryo, SuperTux, Fish Fillet even the non-game downloads).  In synaptic select the package like before and say apply. Synaptic finds the package is already in the archives and skips the download step saving you time.

Use gparted (synaptic if needed) to know your partitions before the reinstall then select manual partitioning during installation and tell it which partition to install to ( i.e. sda3 for "/" ).

---

### Post by handydan918 on 2009-01-22
You seem to have a package manager error. Try ```
sudo apt-get install -f
```

and post any errors it throws. 

Might also try ```
dpkg --configure -a
```

before going thru the drama of an unnecessary reinstall.

---

### Post by steve228 on 2009-01-22
Result of ```
apt-get install -f
```

```

steve@steve-laptop:~$ sudo apt-get install -f
[sudo] password for steve:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
steve@steve-laptop:~$

```

Result of ```
dpkg --configure
``` showed nothing

**I am also using hardy and not intrepid due to screen flicker problems in intrepid... maybe open office is only compatible on 8.10**

---

### Post by steve228 on 2009-01-22
**Thank you guys so much for the help...**

Here is what I did...

I added: 
[I]
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu](http://ppa.launchpad.net/openoffice-pkgs/ubuntu) intrepid main[/I]

which gave me a library compatible only with intrepid...

I changed the 'intrepid' to 'hardy' and used apt-get and gave me all the correct requirements...


Again, thank you for the help :-)

---

