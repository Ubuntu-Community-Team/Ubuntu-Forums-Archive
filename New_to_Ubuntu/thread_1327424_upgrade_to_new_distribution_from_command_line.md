---
title: "upgrade to new distribution from command line"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by ant2ne on 2009-11-15
If I load the GUI update-manager, it says "New distribution release '09.04' is available" and it has an "upgrade" button.

but at the console ```
ant2ne@2ne-buntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ant2ne@2ne-buntu:~$ 
``` So I assume dist-upgrade upgrades my current distribution but doesn't upgrade me to the next distribution.

How can I upgrade distributions via command line.

I have one 8.04 box that I'm upgrading to 9.10 right now. I'd like to do it SSH, but I can pound it out via GUI for now.

I have several 8.04lts servers that I'm going to want to upgrade to 10.4 and they don't have a GUI.

---

### Post by sandyd on 2009-11-15
> **ant2ne said:**
> If I load the GUI update-manager, it says "New distribution release '09.04' is available" and it has an "upgrade" button.

but at the console ```
ant2ne@2ne-buntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ant2ne@2ne-buntu:~$ 
``` So I assume dist-upgrade upgrades my current distribution but doesn't upgrade me to the next distribution.

How can I upgrade distributions via command line.

I have one 8.04 box that I'm upgrading to 9.10 right now. I'd like to do it SSH, but I can pound it out via GUI for now.

I have several 8.04lts servers that I'm going to want to upgrade to 10.4 and they don't have a GUI.
run this
```

sudo nano /etc/apt/sources.list

```
change all distributions to karmic (from hardy)
then save it (press ctrl+x, select save)
then run this
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

---

### Post by Liolikas on 2009-11-15
Maybe you simply forgot apt-get update before dist upgrade?

---

### Post by ant2ne on 2009-11-15
> **Liolikas said:**
> Maybe you simply forgot apt-get update before dist upgrade?

```
ant2ne@2ne-buntu:~$ sudo apt-get update
[sudo] password for ant2ne: 
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release.gpg
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US
Hit http://security.ubuntu.com intrepid-security Release
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com intrepid Release
Hit http://us.archive.ubuntu.com intrepid-updates Release           
Hit http://security.ubuntu.com intrepid-security/main Packages      
Hit http://us.archive.ubuntu.com intrepid/main Packages             
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Packages
Hit http://us.archive.ubuntu.com intrepid/main Sources
Hit http://us.archive.ubuntu.com intrepid/restricted Sources
Hit http://us.archive.ubuntu.com intrepid/universe Packages
Hit http://us.archive.ubuntu.com intrepid/universe Sources
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources
Reading package lists... Done
ant2ne@2ne-buntu:~$ uname -r
2.6.27-15-generic
ant2ne@2ne-buntu:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ant2ne@2ne-buntu:~$ 

```Nope. Just didn't feel like spamming the thread

---

### Post by ant2ne on 2009-11-15
> **carlee said:**
> run this
```

sudo nano /etc/apt/sources.list

```
change all distributions to karmic (from hardy)
then save it (press ctrl+x, select save)
then run this
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

I'm trying this RIGHT now!  :p

> change all distributions to karmic (from hardy) shouldn't there be a replace string command that could substituted this data? It would make an easier script

---

### Post by Paqman on 2009-11-15
Changing your sources file as mentioned by carlee is not an officially recommended method of upgrading, as it doesn't actually invoke the very clever Ubuntu distribution upgrader.

The server method is:
```

sudo apt-get update
sudo apt-get install update-manager-core
sudo do-release-upgrade

``` 

...i've never used it, but I don't see why it shouldn't work on a desktop.

Using sudo apt-get dist-upgrade doesn't upgrade your distribution. It's just a slightly more edgy alternative to the normal sudo apt-get upgrade. The difference between the two is that upgrade will never remove a package due to a dependency issue, whereas dist-upgrade will. Dist-upgrade is a potential source of b0rkage because of that.

---

### Post by ant2ne on 2009-11-15
> **ant2ne said:**
> I'm trying this RIGHT now!  :p

Yup it b0rked on me. The upgrading to 9.10 did not detect my partitioning scheme. I have 1 disk with partitions...
```
Disk 1
/swap sda1
/ sda2
/home sda5
/data sda6
Disk 2
/backup sdb1

```
...It only detected the 2 disks and crashed unable to find the / or the /home. I popped in the 9.10 disk to do a clean install and the installer didn't detect the partitions either. It only found the entire disks. I popped in the 9.04 install disk and it did discover my partitions. I kicked off the install only / was to be formatted and the rest of the partitions are mounted on the correct locations without data loss

Well, I've upgraded from 8.04 to 9.04. I would like to be at 9.10. Any idea what went wrong? And advice? I guess I'll open a new thread.  ;-(

---

### Post by Lateralis on 2009-11-15
[Deleted: ooops.  I was talking nonsense!]

---

### Post by Paqman on 2009-11-16
> **ant2ne said:**
> Any idea what went wrong?

Yep, you were given some bad advice. Changing your sources list is an oldskool Linux way of doing upgrades, and not recommended on Ubuntu.

> And advice?

Either just use Update Manager, or try the CLI method I posted.

---

### Post by garvinrick4 on 2009-11-16
Did not know you could skip a version and upgrade. Always thought you had to
go from 8.04 to 8.10 to 9.04 ect. ect. ect. 
 I have learned something. Thank you folks.

---

### Post by slakkie on 2009-11-16
See the link in my sig. Several methods are explained.

---

### Post by ant2ne on 2009-11-21
I downed the alternate installer. Which during the setup process did detect my individual partitions. After the install on the first boot...
```
gave up waitn for root device. Common Problems:
Boot args (cat /proc/cmdline)
check root delay = (did the system wait long enough)
check root =  (did the system wait for the right device)
missing modules (cat /proc/modlules; ls /dev)
ALERT! /dev/disk/by-uuid/208966a2-4d52-4b41-a579-15d90b6e61c2 does not exist... ...dropping to a shell!
```

i tried changing my /etc/fstabs and removing the 208966a2-4d52-4b41-a579-15d90b6e61c2 and trying just /dev/sda2. That failed as well. 

ls /dev/sd* shows sda sdb sdc. But no partitions!

I dont' know if I should blame the new grub, or what. I've installed 9.10 on 4 or 5 systems now, and I have had no problems. (I'm using a 9.10 system to type this)

Once again... I'm installing 9.04 because I can't afford to be down.

---

### Post by abumaia on 2009-12-13
what about switching from one distro to another, such as from Ubuntu to Mandriva, or from SUSE to Mint?  I'm assuming based on the lack of any relevant search results that there's no special way to change from one to another other than install, try, wipe, install other, rinse, repeat.
****

---

### Post by zoogTHOMzoog on 2010-05-14
Thanks! This helped me upgrade to 10.04 from 8.04 from the command line!
> **Paqman said:**
> Changing your sources file as mentioned by carlee is not an officially recommended method of upgrading, as it doesn't actually invoke the very clever Ubuntu distribution upgrader.

The server method is:
```

sudo apt-get update
sudo apt-get install update-manager-core
sudo do-release-upgrade

``` 



---

