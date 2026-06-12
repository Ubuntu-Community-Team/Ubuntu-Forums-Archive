---
title: "no more flash"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by kazinnud on 2010-02-18
flash player stopped working at all after the last update, and now I can't seem to uninstall/reinstall without some sort of error.

sudo apt-get install produces:
2010-02-17 20:54:14 (388 KB/s) - `./adobe-flashplugin_10.0.45.2.orig.tar.gz' saved [4028753/4028753]

Download done.
cp: cannot stat `WeiDU': No such file or directory
cp: cannot stat `WeiGUI': No such file or directory
cp: cannot stat `WeInstall': No such file or directory
cp: cannot stat `tisunpack': No such file or directory
cp: cannot stat `tolower': No such file or directory
ln: creating symbolic link `/home/vbigiani/bin/weidu': No such file or directory
ln: creating symbolic link `/home/vbigiani/bin/weigui': No such file or directory
ln: creating symbolic link `/home/vbigiani/bin/weinstall': No such file or directory
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                      Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

the series of cp's and ln's are from an install.sh for weidu-linux (for installing, writing, and managing modifications to the oh-so-popular baldur's gate).  i apparently compiled that quite wrong and now that business won't get out of what seems like 'make install' or checkinstall--every package i try to get runs through that bit of script and coughs up some error similar to the last line of paste.

Karmic Koala, I didn't mean to hurt you!

izak

Edit: also, this is for an attempt after successfully removing (without errors) cvs, but cvs would cough up errors whenever called by dpkg when it was installed...

---

### Post by kazinnud on 2010-02-18
that I've gone and broken my dpkg?  Should I reinstall it?  Or will even trying that break the system?

---

### Post by Satoru-san on 2010-02-18
All you have to do is try to remove it as best as you can then remove it from your installed package list, then reinstall it. I helped my brother do this. I will see if I can find the howto.

Just hold tight.

[https://answers.launchpad.net/ubuntu/+question/14619](https://answers.launchpad.net/ubuntu/+question/14619) <-- howto

[http://www.uluga.ubuntuforums.org/showthread.php?t=1394636](http://www.uluga.ubuntuforums.org/showthread.php?t=1394636) <-- my thread.

---

### Post by murderslastcrow on 2010-02-18
Ironic- that last update seemed to fix a plethora of long standing issues with several of my friends' installations. But yes, uninstall it through synaptic and see if you can't reinstall it, or even get the binary from the Flash website.

---

### Post by kazinnud on 2010-02-18
thanks satoru, murderslastcrow, for reading :)

i have tried to uninstall the offending flash, reinstall, and nothing brings it back.  always the same error.

have tried
sudo apt-get update
sudo apt-get upgrade
sudo apt-get autoremove
sudo apt-get clean
sudo dpkg audit
sudo dpkg --config flashplugin-installer
sudo apt-get install -f

have tried deleting what others have called "offending files" in var/lib/dpkg/info (some prerms and such) and var/cache/apt (the packages themselves).

have not tried getting the binary from flash website, but getting their tarball and following the instructions on adobe's website does nothing (unpack tarball to desktop, navigate terminal to desktop, type "./flashplugin-installer" and nothing happens).

thanks for your help :)

Edit: any thoughts on the weidu junk when apt calls dpkg?

---

### Post by kazinnud on 2010-02-18
frankie@frankie-desktop:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg                          
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Translation-en_US           
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                              
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg                     
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [871B]                         
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages          
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                  
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US      
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages  
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Fetched 3,600B in 1s (2,314B/s)
Reading package lists... Done
frankie@frankie-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up flashplugin-installer (10.0.45.2ubuntu0.9.10.1) ...
Downloading...
--2010-02-17 22:51:47--  [http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2.orig.tar.gz](http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2.orig.tar.gz)
Resolving archive.canonical.com... 91.189.90.142
Connecting to archive.canonical.com|91.189.90.142|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 4028753 (3.8M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.0.45.2.orig.tar.gz'

     0K .......... .......... .......... .......... ..........  1% 69.3K 56s
    50K .......... .......... .......... .......... ..........  2%  258K 35s
   100K .......... .......... .......... .......... ..........  3%  311K 27s
   150K .......... .......... .......... .......... ..........  5%  741K 21s
   200K .......... .......... .......... .......... ..........  6%  443K 19s
   250K .......... .......... .......... .......... ..........  7%  236K 18s
   300K .......... .......... .......... .......... ..........  8%  224M 15s
   350K .......... .......... .......... .......... .......... 10%  240M 13s
   400K .......... .......... .......... .......... .......... 11% 54.5K 18s
   450K .......... .......... .......... .......... .......... 12%  314K 17s
   500K .......... .......... .......... .......... .......... 13%  131K 18s
   550K .......... .......... .......... .......... .......... 15% 71.3K 20s
   600K .......... .......... .......... .......... .......... 16% 90.8K 21s
   650K .......... .......... .......... .......... .......... 17%  121K 21s
   700K .......... .......... .......... .......... .......... 19%  101K 22s
   750K .......... .......... .......... .......... .......... 20%  125K 21s
   800K .......... .......... .......... .......... .......... 21%  124K 21s
   850K .......... .......... .......... .......... .......... 22%  138K 21s
   900K .......... .......... .......... .......... .......... 24%  139K 21s
   950K .......... .......... .......... .......... .......... 25%  157K 20s
  1000K .......... .......... .......... .......... .......... 26%  150K 20s
  1050K .......... .......... .......... .......... .......... 27%  145K 20s
  1100K .......... .......... .......... .......... .......... 29%  194K 19s
  1150K .......... .......... .......... .......... .......... 30%  170K 19s
  1200K .......... .......... .......... .......... .......... 31%  200K 18s
  1250K .......... .......... .......... .......... .......... 33%  171K 18s
  1300K .......... .......... .......... .......... .......... 34%  199K 17s
  1350K .......... .......... .......... .......... .......... 35%  180K 17s
  1400K .......... .......... .......... .......... .......... 36%  241K 16s
  1450K .......... .......... .......... .......... .......... 38%  190K 16s
  1500K .......... .......... .......... .......... .......... 39%  198K 15s
  1550K .......... .......... .......... .......... .......... 40%  247K 15s
  1600K .......... .......... .......... .......... .......... 41%  207K 14s
  1650K .......... .......... .......... .......... .......... 43%  233K 14s
  1700K .......... .......... .......... .......... .......... 44%  211K 14s
  1750K .......... .......... .......... .......... .......... 45%  254K 13s
  1800K .......... .......... .......... .......... .......... 47%  229K 13s
  1850K .......... .......... .......... .......... .......... 48%  255K 12s
  1900K .......... .......... .......... .......... .......... 49%  240K 12s
  1950K .......... .......... .......... .......... .......... 50%  260K 11s
  2000K .......... .......... .......... .......... .......... 52%  263K 11s
  2050K .......... .......... .......... .......... .......... 53%  139K 11s
  2100K .......... .......... .......... .......... .......... 54%  182K 11s
  2150K .......... .......... .......... .......... .......... 55%  133K 10s
  2200K .......... .......... .......... .......... .......... 57% 92.0K 10s
  2250K .......... .......... .......... .......... .......... 58% 93.7K 10s
  2300K .......... .......... .......... .......... .......... 59%  111K 10s
  2350K .......... .......... .......... .......... .......... 61%  112K 10s
  2400K .......... .......... .......... .......... .......... 62%  135K 9s
  2450K .......... .......... .......... .......... .......... 63%  137K 9s
  2500K .......... .......... .......... .......... .......... 64%  139K 9s
  2550K .......... .......... .......... .......... .......... 66%  142K 8s
  2600K .......... .......... .......... .......... .......... 67%  142K 8s
  2650K .......... .......... .......... .......... .......... 68%  167K 8s
  2700K .......... .......... .......... .......... .......... 69%  180K 7s
  2750K .......... .......... .......... .......... .......... 71%  167K 7s
  2800K .......... .......... .......... .......... .......... 72%  172K 7s
  2850K .......... .......... .......... .......... .......... 73%  183K 7s
  2900K .......... .......... .......... .......... .......... 74%  139K 6s
  2950K .......... .......... .......... .......... .......... 76%  104K 6s
  3000K .......... .......... .......... .......... .......... 77% 85.0K 6s
  3050K .......... .......... .......... .......... .......... 78% 89.4K 5s
  3100K .......... .......... .......... .......... .......... 80% 84.3K 5s
  3150K .......... .......... .......... .......... .......... 81%  104K 5s
  3200K .......... .......... .......... .......... .......... 82% 97.5K 5s
  3250K .......... .......... .......... .......... .......... 83%  131K 4s
  3300K .......... .......... .......... .......... .......... 85%  133K 4s
  3350K .......... .......... .......... .......... .......... 86%  137K 4s
  3400K .......... .......... .......... .......... .......... 87%  139K 3s
  3450K .......... .......... .......... .......... .......... 88%  142K 3s
  3500K .......... .......... .......... .......... .......... 90%  137K 3s
  3550K .......... .......... .......... .......... .......... 91% 92.0K 2s
  3600K .......... .......... .......... .......... .......... 92% 98.8K 2s
  3650K .......... .......... .......... .......... .......... 94%  116K 2s
  3700K .......... .......... .......... .......... .......... 95%  106K 1s
  3750K .......... .......... .......... .......... .......... 96%  126K 1s
  3800K .......... .......... .......... .......... .......... 97%  132K 1s
  3850K .......... .......... .......... .......... .......... 99%  138K 0s
  3900K .......... .......... .......... ....                 100%  151K=27s

2010-02-17 22:52:15 (144 KB/s) - `./adobe-flashplugin_10.0.45.2.orig.tar.gz' saved [4028753/4028753]

Download done.
cp: cannot stat `WeiDU': No such file or directory
cp: cannot stat `WeiGUI': No such file or directory
cp: cannot stat `WeInstall': No such file or directory
cp: cannot stat `tisunpack': No such file or directory
cp: cannot stat `tolower': No such file or directory
ln: creating symbolic link `/home/vbigiani/bin/weidu': No such file or directory
ln: creating symbolic link `/home/vbigiani/bin/weigui': No such file or directory
ln: creating symbolic link `/home/vbigiani/bin/weinstall': No such file or directory
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
frankie@frankie-desktop:~$ 

i hope this is helpful?

---

### Post by Soul-Sing on 2010-02-18
```
gksudo nautilus
```

navigate to /var/lib/dpkg/info and deleting everything that has this name:
- flashplugin-installer/flashplugin-nonfree (there is a searchoption on the right corner)
remove it
close nautilus

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

---

### Post by kazinnud on 2010-02-18
Results:

frankie@frankie-desktop:~$ sudo apt-get update
Get:1 [http://dl.google.com](http://dl.google.com) stable Release.gpg [189B]
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release.gpg                          
Ign [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                         
Ign [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Translation-en_US           
Get:2 [http://dl.google.com](http://dl.google.com) stable Release [2,540B]                             
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic Release                              
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release.gpg                            
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Translation-en_US       
Get:3 [http://dl.google.com](http://dl.google.com) stable/main Packages [871B]               
Hit [http://download.virtualbox.org](http://download.virtualbox.org) karmic/non-free Packages                    
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg           
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_US
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) karmic-updates/universe Packages
Fetched 3,600B in 1s (2,233B/s)
Reading package lists... Done
frankie@frankie-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up flashplugin-installer (10.0.45.2ubuntu0.9.10.1) ...
Setting up flashplugin-nonfree (10.0.45.2ubuntu0.9.10.1) ...

everything stops there.  flash still does not work.

thanks for trying leoquant...  any other ideas?

synaptic still returns the following errors upon trying to install flashplugin-nonfree and flashplugin-installer:

E: flashplugin-installer: subprocess installed post-installation script returned error exit status 1
E: flashplugin-nonfree: dependency problems - leaving unconfigured

however, the offending packages don't show up in the "not installed--residual config" filter in synaptic.

iz

---

### Post by Soul-Sing on 2010-02-18
I must say, Karmic (on virtualbox) shows a greyed/inactive update option for flash....So I can't update the software.
kazinnud, no I have no idea how to solve this for you.

---

### Post by kazinnud on 2010-02-18
thanks for trying, leoquant.

i must say, though, that these problems all started (well, all these flash problems..dpkg clutter could have been there for a long time) yesterday when there was an update to the flashplugin-nonfree...

bumping for someone else to give it a shot--

izak

edit: i have found a lot of threads talking about being UNABLE to remove the flash plugin.  i don't seem to have a problem with this; synaptic and dpkg --purge seem to get rid of everything without error.  is there any way to check to make sure the package is really gone?

---

### Post by kazinnud on 2010-02-18
solved

the problem was a stray file named "install" from the weidu for linux pack which had made its way into /usr/local/sbin

when installing the flashplugin-installer, dpkg would call this broken install file and screw everything up.

i really suck at linux.

---

### Post by lhankins on 2010-05-29
I'm having the same problem on 9.10 64. 

I was trying to get Adobe Air installed, so I ran the script available in the first comment (from mla) on this post : 

[http://they.misled.us/archives/1311]("http://they.misled.us/archives/1311")

Unfortunately, that didn't work (and had the unfortunate side effect of completely hosing my flash support). 

All attempts to uninstall / reinstall flash (via synaptics) have failed.  Sample error below : 

```

2010-05-29 10:03:56 (198 KB/s) - `./adobe-flashplugin_10.0.45.2.orig.tar.gz' saved [4028753/4028753]

Download done.
Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


```


I looked for the same file that kazinnud removed to fix his problem (not present on my system).

Any ideas...?

---

### Post by sandyd on 2010-05-29
> **lhankins said:**
> I'm having the same problem on 9.10 64. 

I was trying to get Adobe Air installed, so I ran the script available in the first comment (from mla) on this post : 

[http://they.misled.us/archives/1311](http://they.misled.us/archives/1311)

Unfortunately, that didn't work (and had the unfortunate side effect of completely hosing my flash support). 

All attempts to uninstall / reinstall flash (via synaptics) have failed.  Sample error below : 

```

2010-05-29 10:03:56 (198 KB/s) - `./adobe-flashplugin_10.0.45.2.orig.tar.gz' saved [4028753/4028753]

Download done.
Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


```
I looked for the same file that kazinnud removed to fix his problem (not present on my system).

Any ideas...?
```

sudo dpkg --purge --force all nspluginwrapper
sudo apt-get install nspluginwrapper
```

---

### Post by lhankins on 2010-05-29
@carlee, thanks for the advice, but still no luck... 

I found this thread:

[https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/527273](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/527273)

Which talks about uninstalling google earth got rid of the problem for them.  I don't have google earth, but reasoned maybe something else installed on my machine which uses flash may be the root of the problem.  I uninstalled firefox and google chrome, still no dice.   

Here are the steps I just did : 
```

sudo dpkg --purge --force all nspluginwrapper
sudo dpkg --purge --force all flashplugin-installer

```Then to attempt reinstall :

```

sudo apt-get install nspluginwrapper > install_nspluginwrapper.txt 2>&1
sudo apt-get install flashplugin-installer > install_flashplugin-installer.txt 2>&1

```The nspluginwrapper goes on ok (output below) : 

```

Reading package lists...
Building dependency tree...
Reading state information...
The following NEW packages will be installed:
  nspluginwrapper
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/198kB of archives.
After this operation, 565kB of additional disk space will be used.
Selecting previously deselected package nspluginwrapper. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 171110 files and directories currently installed.) 
Unpacking nspluginwrapper (from .../nspluginwrapper_1.2.2-0ubuntu6_amd64.deb) ... 
Processing triggers for man-db ... 
Setting up nspluginwrapper (1.2.2-0ubuntu6) ... 
plugin dirs: 
Auto-update plugins from /usr/lib/mozilla/plugins 
Looking for plugins in /usr/lib/mozilla/plugins 
Auto-update plugins from /usr/lib64/mozilla/plugins 
Looking for plugins in /usr/lib64/mozilla/plugins 
Auto-update plugins from /usr/lib/firefox/plugins 
Looking for plugins in /usr/lib/firefox/plugins 
Auto-update plugins from /usr/lib64/firefox/plugins 
Looking for plugins in /usr/lib64/firefox/plugins 
Auto-update plugins from /root/.mozilla/plugins 
Looking for plugins in /root/.mozilla/plugins 
 

```But the flashplugin-installer still fails : 

```

Reading package lists...
Building dependency tree...
Reading state information...
Suggested packages:
  xulrunner-1.9 konqueror-nsplugins ttf-bitstream-vera ttf-dejavu
  ttf-xfree86-nonfree xfs
The following NEW packages will be installed:
  flashplugin-installer
Preconfiguring packages ...
0 upgraded, 1 newly installed, 0 to remove and 10 not upgraded.
Need to get 0B/19.6kB of archives.
After this operation, 188kB of additional disk space will be used.
Selecting previously deselected package flashplugin-installer. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 171140 files and directories currently installed.) 
Unpacking flashplugin-installer (from .../flashplugin-installer_10.0.45.2ubuntu0.9.10.1_amd64.deb) ... 
Setting up flashplugin-installer (10.0.45.2ubuntu0.9.10.1) ... 
Downloading... 
--2010-05-29 12:48:06--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.45.2.orig.tar.gz 
Resolving archive.canonical.com... 91.189.88.33 
Connecting to archive.canonical.com|91.189.88.33|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 4028753 (3.8M) [application/x-gzip] 
Saving to: `./adobe-flashplugin_10.0.45.2.orig.tar.gz' 
 
     0K .......... .......... .......... .......... ..........  1% 64.0K 61s 
    50K .......... .......... .......... .......... ..........  2%  421K 35s 
   100K .......... .......... .......... .......... ..........  3%  173K 30s 
   150K .......... .......... .......... .......... ..........  5%  179K 27s 
   200K .......... .......... .......... .......... ..........  6%  183K 26s 
   250K .......... .......... .......... .......... ..........  7%  192K 24s 
   300K .......... .......... .......... .......... ..........  8%  225K 23s 
   350K .......... .......... .......... .......... .......... 10%  122K 23s 
   400K .......... .......... .......... .......... .......... 11% 93.9K 25s 
   450K .......... .......... .......... .......... .......... 12%  127K 24s 
   500K .......... .......... .......... .......... .......... 13%  150K 24s 
   550K .......... .......... .......... .......... .......... 15%  132K 24s 
   600K .......... .......... .......... .......... .......... 16%  168K 23s 
   650K .......... .......... .......... .......... .......... 17%  177K 22s 
   700K .......... .......... .......... .......... .......... 19%  180K 22s 
   750K .......... .......... .......... .......... .......... 20%  177K 21s 
   800K .......... .......... .......... .......... .......... 21%  194K 21s 
   850K .......... .......... .......... .......... .......... 22%  203K 20s 
   900K .......... .......... .......... .......... .......... 24%  236K 19s 
   950K .......... .......... .......... .......... .......... 25%  207K 19s 
  1000K .......... .......... .......... .......... .......... 26%  230K 18s 
  1050K .......... .......... .......... .......... .......... 27%  237K 18s 
  1100K .......... .......... .......... .......... .......... 29%  243K 17s 
  1150K .......... .......... .......... .......... .......... 30%  262K 16s 
  1200K .......... .......... .......... .......... .......... 31%  238K 16s 
  1250K .......... .......... .......... .......... .......... 33%  272K 15s 
  1300K .......... .......... .......... .......... .......... 34%  275K 15s 
  1350K .......... .......... .......... .......... .......... 35%  274K 14s 
  1400K .......... .......... .......... .......... .......... 36%  282K 14s 
  1450K .......... .......... .......... .......... .......... 38%  287K 13s 
  1500K .......... .......... .......... .......... .......... 39%  297K 13s 
  1550K .......... .......... .......... .......... .......... 40%  289K 13s 
  1600K .......... .......... .......... .......... .......... 41%  303K 12s 
  1650K .......... .......... .......... .......... .......... 43%  294K 12s 
  1700K .......... .......... .......... .......... .......... 44%  310K 11s 
  1750K .......... .......... .......... .......... .......... 45%  299K 11s 
  1800K .......... .......... .......... .......... .......... 47%  327K 11s 
  1850K .......... .......... .......... .......... .......... 48%  306K 10s 
  1900K .......... .......... .......... .......... .......... 49%  314K 10s 
  1950K .......... .......... .......... .......... .......... 50%  308K 10s 
  2000K .......... .......... .......... .......... .......... 52%  309K 9s 
  2050K .......... .......... .......... .......... .......... 53%  309K 9s 
  2100K .......... .......... .......... .......... .......... 54%  310K 9s 
  2150K .......... .......... .......... .......... .......... 55%  315K 8s 
  2200K .......... .......... .......... .......... .......... 57%  304K 8s 
  2250K .......... .......... .......... .......... .......... 58%  317K 8s 
  2300K .......... .......... .......... .......... .......... 59%  308K 7s 
  2350K .......... .......... .......... .......... .......... 61%  316K 7s 
  2400K .......... .......... .......... .......... .......... 62%  305K 7s 
  2450K .......... .......... .......... .......... .......... 63%  158K 7s 
  2500K .......... .......... .......... .......... .......... 64% 1.67M 6s 
  2550K .......... .......... .......... .......... .......... 66%  187K 6s 
  2600K .......... .......... .......... .......... .......... 67%  221K 6s 
  2650K .......... .......... .......... .......... .......... 68%  213K 6s 
  2700K .......... .......... .......... .......... .......... 69%  226K 5s 
  2750K .......... .......... .......... .......... .......... 71%  232K 5s 
  2800K .......... .......... .......... .......... .......... 72%  238K 5s 
  2850K .......... .......... .......... .......... .......... 73%  257K 5s 
  2900K .......... .......... .......... .......... .......... 74%  249K 5s 
  2950K .......... .......... .......... .......... .......... 76%  259K 4s 
  3000K .......... .......... .......... .......... .......... 77%  263K 4s 
  3050K .......... .......... .......... .......... .......... 78%  281K 4s 
  3100K .......... .......... .......... .......... .......... 80%  277K 4s 
  3150K .......... .......... .......... .......... .......... 81%  292K 3s 
  3200K .......... .......... .......... .......... .......... 82%  289K 3s 
  3250K .......... .......... .......... .......... .......... 83%  303K 3s 
  3300K .......... .......... .......... .......... .......... 85%  287K 3s 
  3350K .......... .......... .......... .......... .......... 86%  309K 2s 
  3400K .......... .......... .......... .......... .......... 87%  311K 2s 
  3450K .......... .......... .......... .......... .......... 88%  296K 2s 
  3500K .......... .......... .......... .......... .......... 90%  316K 2s 
  3550K .......... .......... .......... .......... .......... 91%  296K 1s 
  3600K .......... .......... .......... .......... .......... 92%  329K 1s 
  3650K .......... .......... .......... .......... .......... 94%  307K 1s 
  3700K .......... .......... .......... .......... .......... 95%  317K 1s 
  3750K .......... .......... .......... .......... .......... 96%  304K 1s 
  3800K .......... .......... .......... .......... .......... 97%  316K 0s 
  3850K .......... .......... .......... .......... .......... 99%  309K 0s 
  3900K .......... .......... .......... ....                 100%  313K=17s 
 
2010-05-29 12:48:23 (234 KB/s) - `./adobe-flashplugin_10.0.45.2.orig.tar.gz' saved [4028753/4028753] 
 
Download done. 
Flash Plugin installed. 
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so 
dpkg: error processing flashplugin-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
Errors were encountered while processing: 
 flashplugin-installer 
E: Sub-process /usr/bin/dpkg returned an error code (1)

```I'm thinking that Adobe AIR install must've left something on my machine which is the root of the problem... now searching to figure out where it put stuff... grrrr...

---

