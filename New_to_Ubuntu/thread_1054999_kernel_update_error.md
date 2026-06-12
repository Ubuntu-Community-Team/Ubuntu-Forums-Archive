---
title: "kernel update error"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by andr3w on 2009-01-30
Hi.
```
aji@coffee:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.27-11-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/23.1MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
(Reading database ... 128132 files and directories currently installed.)
Preparing to replace linux-image-2.6.27-11-generic 2.6.27-11.26 (using .../linux-image-2.6.27-11-generic_2.6.27-11.27_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.27-11-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.27_amd64.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./lib/modules/2.6.27-11-generic/kernel/drivers/gpu/drm/radeon/radeon.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.27-11-generic
Found kernel: /vmlinuz-2.6.27-7-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.27_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
aji@coffee:~$ 


```

Um, I don't know why I'm getting this.

Here is my repository list:
```
# 
# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main restricted
deb-src http://archive.ubuntu.com/ubuntu/ intrepid restricted main #Added by software-properties

# deb cdrom:[Ubuntu 8.10 _Intrepid Ibex_ - Release amd64 (20081028)]/ intrepid main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ intrepid main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid universe
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ intrepid multiverse
deb http://us.archive.ubuntu.com/ubuntu/ intrepid-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb-src http://us.archive.ubuntu.com/ubuntu/ intrepid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu intrepid partner
deb-src http://archive.canonical.com/ubuntu intrepid partner

deb http://security.ubuntu.com/ubuntu intrepid-security main restricted
deb-src http://security.ubuntu.com/ubuntu intrepid-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu intrepid-security universe
deb http://security.ubuntu.com/ubuntu intrepid-security multiverse
deb http://wine.budgetdedicated.com/apt intrepid main
deb http://wine.budgetdedicated.com/apt intrepid main
deb http://download.virtualbox.org/virtualbox/debian intrepid non-free
deb http://deb.opera.com/opera/ lenny non-free
deb http://dl.google.com/linux/deb/ stable non-free
```

I tried fixing broken packages, but there are no packages to fix?

---

### Post by clive littlewood on 2009-01-30
Hi

Have you updated your system with the normal "sytem updates" using update manager.

The apt-get command you entered is "upgrade" not "update"

Clive

---

### Post by andr3w on 2009-01-30
> **clive littlewood said:**
> Hi

Have you updated your system with the normal "sytem updates" using update manager.

The apt-get command you entered is "upgrade" not "update"

Clive

Yes, I did update, then upgrade.

```
aji@coffee:~$ sudo apt-get update
Hit http://download.virtualbox.org intrepid Release.gpg
Ign http://download.virtualbox.org intrepid/non-free Translation-en_US         
Hit http://download.virtualbox.org intrepid Release                            
Hit http://download.virtualbox.org intrepid/non-free Packages                  
Get:1 http://dl.google.com stable Release.gpg [189B]                           
Hit http://archive.canonical.com intrepid Release.gpg                          
Ign http://archive.canonical.com intrepid/partner Translation-en_US            
Hit http://security.ubuntu.com intrepid-security Release.gpg                   
Ign http://security.ubuntu.com intrepid-security/main Translation-en_US        
Ign http://dl.google.com stable/non-free Translation-en_US                     
Hit http://wine.budgetdedicated.com intrepid Release.gpg                       
Ign http://wine.budgetdedicated.com intrepid/main Translation-en_US            
Hit http://deb.opera.com lenny Release.gpg                                     
Ign http://deb.opera.com lenny/non-free Translation-en_US                      
Hit http://packages.medibuntu.org intrepid Release.gpg                         
Hit http://us.archive.ubuntu.com intrepid Release.gpg                          
Ign http://us.archive.ubuntu.com intrepid/main Translation-en_US               
Ign http://us.archive.ubuntu.com intrepid/restricted Translation-en_US         
Hit http://archive.ubuntu.com intrepid Release.gpg                             
Get:2 http://dl.google.com stable Release [1300B]                              
Hit http://archive.canonical.com intrepid Release                              
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_US  
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_US    
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_US  
Hit http://security.ubuntu.com intrepid-security Release                       
Hit http://wine.budgetdedicated.com intrepid Release                           
Get:3 http://dl.google.com stable/non-free Packages [966B]                     
Hit http://deb.opera.com lenny Release                                         
Ign http://us.archive.ubuntu.com intrepid/universe Translation-en_US           
Ign http://us.archive.ubuntu.com intrepid/multiverse Translation-en_US         
Hit http://us.archive.ubuntu.com intrepid-updates Release.gpg                  
Ign http://us.archive.ubuntu.com intrepid-updates/main Translation-en_US       
Ign http://us.archive.ubuntu.com intrepid-updates/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com intrepid-updates/universe Translation-en_US   
Ign http://us.archive.ubuntu.com intrepid-updates/multiverse Translation-en_US 
Hit http://archive.ubuntu.com intrepid Release                                 
Hit http://us.archive.ubuntu.com intrepid Release                              
Hit http://archive.canonical.com intrepid/partner Packages                     
Hit http://security.ubuntu.com intrepid-security/main Packages                 
Ign http://wine.budgetdedicated.com intrepid/main Packages                     
Ign http://packages.medibuntu.org intrepid/free Translation-en_US              
Ign http://deb.opera.com lenny/non-free Packages                               
Hit http://archive.ubuntu.com intrepid/restricted Sources                      
Hit http://us.archive.ubuntu.com intrepid-updates Release                      
Hit http://archive.canonical.com intrepid/partner Sources                      
Hit http://security.ubuntu.com intrepid-security/restricted Packages           
Hit http://security.ubuntu.com intrepid-security/restricted Sources            
Hit http://security.ubuntu.com intrepid-security/main Sources                  
Hit http://security.ubuntu.com intrepid-security/multiverse Sources            
Hit http://wine.budgetdedicated.com intrepid/main Packages                     
Hit http://archive.ubuntu.com intrepid/main Sources                            
Hit http://us.archive.ubuntu.com intrepid/main Packages                        
Hit http://us.archive.ubuntu.com intrepid/restricted Packages                  
Hit http://us.archive.ubuntu.com intrepid/restricted Sources         
Hit http://us.archive.ubuntu.com intrepid/main Sources               
Hit http://deb.opera.com lenny/non-free Packages                     
Hit http://us.archive.ubuntu.com intrepid/multiverse Sources         
Hit http://security.ubuntu.com intrepid-security/universe Sources    
Hit http://security.ubuntu.com intrepid-security/universe Packages   
Hit http://security.ubuntu.com intrepid-security/multiverse Packages 
Ign http://packages.medibuntu.org intrepid/non-free Translation-en_US
Hit http://us.archive.ubuntu.com intrepid/universe Sources                     
Hit http://us.archive.ubuntu.com intrepid/universe Packages                    
Hit http://us.archive.ubuntu.com intrepid/multiverse Packages                  
Hit http://us.archive.ubuntu.com intrepid-updates/main Packages                
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Packages          
Hit http://us.archive.ubuntu.com intrepid-updates/restricted Sources           
Hit http://us.archive.ubuntu.com intrepid-updates/main Sources                 
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Sources           
Hit http://us.archive.ubuntu.com intrepid-updates/universe Sources             
Hit http://us.archive.ubuntu.com intrepid-updates/universe Packages            
Hit http://us.archive.ubuntu.com intrepid-updates/multiverse Packages          
Hit http://packages.medibuntu.org intrepid Release
Hit http://packages.medibuntu.org intrepid/free Packages
Hit http://packages.medibuntu.org intrepid/non-free Packages
Hit http://packages.medibuntu.org intrepid/free Sources
Hit http://packages.medibuntu.org intrepid/non-free Sources
Fetched 2455B in 2s (1025B/s)
Reading package lists... Done
aji@coffee:~$ 

```

---

### Post by caljohnsmith on 2009-01-30
Maybe that kernel deb package that gave the error is somehow corrupt, so I would try:
```
sudo rm /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.27_amd64.deb
```
That just deletes the linux-image deb file from your apt cache, so if you do the "sudo apt-get upgrade" again, it should force apt-get to download a fresh linux-image deb file. How about trying that and let me know if it helps at all.

---

### Post by andr3w on 2009-01-30
> **caljohnsmith said:**
> Maybe that kernel deb package that gave the error is somehow corrupt, so I would try:
```
sudo rm /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.27_amd64.deb
```
That just deletes the linux-image deb file from your apt cache, so if you do the "sudo apt-get upgrade" again, it should force apt-get to download a fresh linux-image deb file. How about trying that and let me know if it helps at all.

ok.
I deleted it, and then:

```
aji@coffee:~$ sudo apt-get upgr
E: Invalid operation upgr
aji@coffee:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  linux-image-2.6.27-11-generic
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 23.1MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com intrepid-updates/main linux-image-2.6.27-11-generic 2.6.27-11.27 [23.1MB]
Fetched 23.1MB in 4min10s (92.2kB/s)                                           
(Reading database ... 128132 files and directories currently installed.)
Preparing to replace linux-image-2.6.27-11-generic 2.6.27-11.26 (using .../linux-image-2.6.27-11-generic_2.6.27-11.27_amd64.deb) ...
Done.
Unpacking replacement linux-image-2.6.27-11-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.27_amd64.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./lib/modules/2.6.27-11-generic/kernel/drivers/gpu/drm/radeon/radeon.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Running postrm hook script /sbin/update-grub.
Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /vmlinuz-2.6.27-11-generic
Found kernel: /vmlinuz-2.6.27-7-generic
Found kernel: /memtest86+.bin
Updating /boot/grub/menu.lst ... done

Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.27_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
aji@coffee:~$ 


```

---

### Post by caljohnsmith on 2009-01-30
> **andr3w said:**
> 
```
aji@coffee:~$ sudo apt-get upgr
....
Unpacking replacement linux-image-2.6.27-11-generic ...
dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.27_amd64.deb (--unpack):
[COLOR="Red"] failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./lib/modules/2.6.27-11-generic/kernel/drivers/gpu/drm/radeon/radeon.ko': No space left on device[/COLOR]
dpkg-deb: subprocess paste killed by signal (Broken pipe)

```
"No space left on device" is one of the errors it returned, so what do you get when you do:
```
df -h

```

---

### Post by avtolle on 2009-01-30
(Beat me too it). I'm hypothecating that you may have a separate /boot, which is full or nearly full. Run ```
df-h
```and post results. You may have to delete one or more of the older kernels.

---

### Post by andr3w on 2009-01-30
> **avtolle said:**
> (Beat me too it). I'm hypothecating that you may have a separate /boot, which is full or nearly full. Run ```
df-h
```and post results. You may have to delete one or more of the older kernels.

```
aji@coffee:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/mapper/sys-root  299M  289M     0 100% /
tmpfs                 1.5G     0  1.5G   0% /lib/init/rw
varrun                1.5G  244K  1.5G   1% /var/run
varlock               1.5G     0  1.5G   0% /var/lock
udev                  1.5G  2.8M  1.5G   1% /dev
tmpfs                 1.5G  384K  1.5G   1% /dev/shm
lrm                   1.5G  2.4M  1.5G   1% /lib/modules/2.6.27-11-generic/volatile
/dev/sda2             177M   28M  140M  17% /boot
/dev/mapper/sda3_crypt
                       14G  277M   13G   3% /home
/dev/mapper/sys-tmp   1.5G   35M  1.4G   3% /tmp
/dev/mapper/sys-usr   5.8G  3.2G  2.4G  58% /usr
/dev/mapper/sys-var   2.5G  724M  1.6G  31% /var
/dev/mapper/truecrypt1
                      290G  147G  129G  54% /media/truecrypt1

```


Umm, well whatever then.
No one's answering.

---

### Post by bettlebrox on 2009-01-30
Your root parition is full:

/dev/mapper/sys-root  299M  289M     0 100% /

It cannot install the new kernel packages because there's no room in / for the modules:

[INDENT]dpkg: error processing /var/cache/apt/archives/linux-image-2.6.27-11-generic_2.6.27-11.27_amd64.deb (--unpack):
 failed in buffer_write(fd) (10, ret=-1): backend dpkg-deb during `./lib/modules/2.6.27-11-generic/kernel/drivers/gpu/drm/radeon/radeon.ko': No space left on device
dpkg-deb: subprocess paste killed by signal (Broken pipe)[/INDENT]

You'll need to free up space, probably the easiest way is to remove any old kernels (and their associated modules) that your no longer using. Just make sure *not* to remove the kernel your currently running.

Also, do you have anything installed into /opt ? If you do, you could move /opt to /home/opt and then create a symbolic link to it.

---

