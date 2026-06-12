---
title: "Apparently no proxy for downloads - cannot download updates for a few days"
date: 2015-10-05
forum: Networking &amp; Wireless
---

### Post by Todd in Berlin on 2015-10-05
Hi, I posted this previously under a different title a few days ago, but I think it has been overlooked because I knew less about the issue than I do now. 

When I get an update notification both for Ubuntu system or other applications, everything is fine but then it gets hung up at "Downloading". Under Synaptic Package Manager I got a notice about the inability to Fetch when I tried it that way. 

I assume that there are some commands to enter in Terminal which will help determine what the problem is. Please advise. Thanks.

****

Update, 6 October, 10am Pacific Time: New update notification is for almost 200 megs. I have never seen an update this big - it's an accumulation of the things I have not been able to download for the past days. Help!!!

---

### Post by v3.xx on 2015-10-07
There are two terminal commands to use for update and upgrade.

```
sudo apt-get update

```
and

```
sudo apt-get dist-upgrade
```

Please post any errors you get with these commands.

[https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands](https://help.ubuntu.com/community/AptGet/Howto#Maintenance_commands)

---

### Post by Todd in Berlin on 2015-10-07
[COLOR=#000000]Thanks!

I ran both commands in Terminal.... 

First sudo apt-get update got hung up

Then sudo apt-get dist-upgrade worked this time - it seemed like it got hung up before - but it suggested I run sudo apt-get update and it got hung up again....
[/COLOR]
[COLOR=#000000]```


```[/COLOR]```
todd@Dukla:~$ sudo apt-get update
[sudo] password for todd: 
Ign http://apt.spideroak.com release InRelease                                 
Ign http://APT.spideroak.com release InRelease                                 
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://apt.spideroak.com release Release.gpg                               
Hit http://APT.spideroak.com release Release.gpg                               
Hit http://ppa.launchpad.net trusty Release.gpg                                
Ign http://repos.cloudme.com ./ InRelease                                      
Hit http://apt.spideroak.com release Release                                   
Hit http://APT.spideroak.com release Release                                   
Hit http://ppa.launchpad.net trusty Release                                    
Hit http://apt.spideroak.com release/restricted amd64 Packages                 
Hit http://APT.spideroak.com release/restricted amd64 Packages                 
Ign http://repos.cloudme.com ./ Release.gpg                                    
Hit http://APT.spideroak.com release/restricted i386 Packages                  
Hit http://apt.spideroak.com release/restricted i386 Packages                  
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign http://repos.cloudme.com ./ Release                                        
Get:1 https://download.01.org trusty InRelease                                 
Ign https://download.01.org trusty InRelease                                   
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Get:2 https://download.01.org trusty/main amd64 Packages/DiffIndex             
Ign https://download.01.org trusty/main amd64 Packages/DiffIndex               
Ign http://repos.cloudme.com ./ Packages/DiffIndex                             
Ign https://download.01.org trusty/main i386 Packages/DiffIndex                
Ign http://apt.spideroak.com release/restricted Translation-en_US              
Ign http://APT.spideroak.com release/restricted Translation-en_US              
Ign http://apt.spideroak.com release/restricted Translation-en                 
Ign http://APT.spideroak.com release/restricted Translation-en                 
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://repos.cloudme.com ./ Packages                                       
Ign http://repos.cloudme.com ./ Translation-en_US                              
Ign http://repos.cloudme.com ./ Translation-en                                 
Hit https://download.01.org trusty/main amd64 Packages                         
Hit https://download.01.org trusty/main i386 Packages                          
Get:3 https://download.01.org trusty/main Translation-en_US                    
Ign https://download.01.org trusty/main Translation-en_US                      
Ign https://download.01.org trusty/main Translation-en                         
100% [Connecting to us.archive.ubuntu.com (2001:67c:1562::15)] [Connecting to s

```[COLOR=#000000]

******
[/COLOR][COLOR=#000000]```

[/COLOR]todd@Dukla:~$ sudo apt-get dist-upgrade
[sudo] password for todd: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  fonts-dejavu fonts-sil-gentium fonts-sil-gentium-basic kde-l10n-engb
  libgnome-keyring0:i386 libllvm3.4:i386 libqt4-gui
  libreoffice-report-builder-bin linux-image-3.13.0-32-generic
  linux-image-3.13.0-36-generic linux-image-extra-3.13.0-32-generic
  linux-image-extra-3.13.0-36-generic linux-signed-image-3.13.0-36-generic
Use 'apt-get autoremove' to remove them.
The following packages will be upgraded:
  chromium-codecs-ffmpeg-extra firefox firefox-locale-en liboxideqt-qmlplugin
  liboxideqtcore0 liboxideqtquick0 linux-headers-3.13.0-65
  linux-headers-3.13.0-65-generic linux-image-3.13.0-65-generic
  linux-image-extra-3.13.0-65-generic linux-libc-dev
  linux-signed-image-3.13.0-65-generic oxideqt-chromedriver
  oxideqt-codecs-extra thunderbird thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-us
18 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 198 MB of archives.
After this operation, 437 kB disk space will be freed.
Do you want to continue? [Y/n] Y
Get:1 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/universe chromium-codecs-ffmpeg-extra amd64 45.0.2454.101-0ubuntu0.14.04.1.1099 [860 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-signed-image-3.13.0-65-generic amd64 3.13.0-65.106 [3,980 B]
Get:3 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-extra-3.13.0-65-generic amd64 3.13.0-65.106 [36.8 MB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-image-3.13.0-65-generic amd64 3.13.0-65.106 [15.2 MB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main firefox amd64 41.0.1+build2-0ubuntu0.14.04.1 [41.5 MB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main firefox-locale-en amd64 41.0.1+build2-0ubuntu0.14.04.1 [667 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-65 all 3.13.0-65.106 [8,871 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-headers-3.13.0-65-generic amd64 3.13.0-65.106 [700 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main linux-libc-dev amd64 3.13.0-65.106 [773 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird-locale-en amd64 1:38.3.0+build1-0ubuntu0.14.04.1 [349 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird amd64 1:38.3.0+build1-0ubuntu0.14.04.1 [32.8 MB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird-gnome-support amd64 1:38.3.0+build1-0ubuntu0.14.04.1 [8,536 B]
Get:13 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main thunderbird-locale-en-us all 1:38.3.0+build1-0ubuntu0.14.04.1 [9,986 B]
Get:14 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main liboxideqt-qmlplugin amd64 1.9.5-0ubuntu0.14.04.1 [178 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main liboxideqtquick0 amd64 1.9.5-0ubuntu0.14.04.1 [256 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main oxideqt-chromedriver amd64 1.9.5-0ubuntu0.14.04.1 [32.9 MB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main liboxideqtcore0 amd64 1.9.5-0ubuntu0.14.04.1 [25.0 MB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ trusty-updates/main oxideqt-codecs-extra amd64 1.9.5-0ubuntu0.14.04.1 [866 kB]
Fetched 198 MB in 12min 43s (259 kB/s)                                         
W: Duplicate sources.list entry http://repos.cloudme.com/ ./ Packages (/var/lib/apt/lists/repos.cloudme.com_._Packages)
W: Duplicate sources.list entry http://repos.cloudme.com/ ./ Packages (/var/lib/apt/lists/repos.cloudme.com_._Packages)
W: Duplicate sources.list entry http://repos.cloudme.com/ ./ Packages (/var/lib/apt/lists/repos.cloudme.com_._Packages)
(Reading database ... 849404 files and directories currently installed.)
Preparing to unpack .../chromium-codecs-ffmpeg-extra_45.0.2454.101-0ubuntu0.14.04.1.1099_amd64.deb ...
Unpacking chromium-codecs-ffmpeg-extra (45.0.2454.101-0ubuntu0.14.04.1.1099) over (45.0.2454.85-0ubuntu0.14.04.1.1097) ...
Preparing to unpack .../linux-signed-image-3.13.0-65-generic_3.13.0-65.106_amd64.deb ...
Unpacking linux-signed-image-3.13.0-65-generic (3.13.0-65.106) over (3.13.0-65.105) ...
Preparing to unpack .../linux-image-extra-3.13.0-65-generic_3.13.0-65.106_amd64.deb ...
Unpacking linux-image-extra-3.13.0-65-generic (3.13.0-65.106) over (3.13.0-65.105) ...
Preparing to unpack .../linux-image-3.13.0-65-generic_3.13.0-65.106_amd64.deb ...
Done.
Unpacking linux-image-3.13.0-65-generic (3.13.0-65.106) over (3.13.0-65.105) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
Preparing to unpack .../firefox_41.0.1+build2-0ubuntu0.14.04.1_amd64.deb ...
Unpacking firefox (41.0.1+build2-0ubuntu0.14.04.1) over (41.0+build3-0ubuntu0.14.04.1) ...
Preparing to unpack .../firefox-locale-en_41.0.1+build2-0ubuntu0.14.04.1_amd64.deb ...
Unpacking firefox-locale-en (41.0.1+build2-0ubuntu0.14.04.1) over (41.0+build3-0ubuntu0.14.04.1) ...
Preparing to unpack .../linux-headers-3.13.0-65_3.13.0-65.106_all.deb ...
Unpacking linux-headers-3.13.0-65 (3.13.0-65.106) over (3.13.0-65.105) ...
Preparing to unpack .../linux-headers-3.13.0-65-generic_3.13.0-65.106_amd64.deb ...
Unpacking linux-headers-3.13.0-65-generic (3.13.0-65.106) over (3.13.0-65.105) ...
Preparing to unpack .../linux-libc-dev_3.13.0-65.106_amd64.deb ...
Unpacking linux-libc-dev:amd64 (3.13.0-65.106) over (3.13.0-65.105) ...
Preparing to unpack .../thunderbird-locale-en_1%3a38.3.0+build1-0ubuntu0.14.04.1_amd64.deb ...
Unpacking thunderbird-locale-en (1:38.3.0+build1-0ubuntu0.14.04.1) over (1:38.2.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird_1%3a38.3.0+build1-0ubuntu0.14.04.1_amd64.deb ...
Unpacking thunderbird (1:38.3.0+build1-0ubuntu0.14.04.1) over (1:38.2.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird-gnome-support_1%3a38.3.0+build1-0ubuntu0.14.04.1_amd64.deb ...
Unpacking thunderbird-gnome-support (1:38.3.0+build1-0ubuntu0.14.04.1) over (1:38.2.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../thunderbird-locale-en-us_1%3a38.3.0+build1-0ubuntu0.14.04.1_all.deb ...
Unpacking thunderbird-locale-en-us (1:38.3.0+build1-0ubuntu0.14.04.1) over (1:38.2.0+build1-0ubuntu0.14.04.1) ...
Preparing to unpack .../liboxideqt-qmlplugin_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqt-qmlplugin:amd64 (1.9.5-0ubuntu0.14.04.1) over (1.9.1-0ubuntu0.14.04.2) ...
Preparing to unpack .../liboxideqtquick0_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqtquick0:amd64 (1.9.5-0ubuntu0.14.04.1) over (1.9.1-0ubuntu0.14.04.2) ...
Preparing to unpack .../oxideqt-chromedriver_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking oxideqt-chromedriver (1.9.5-0ubuntu0.14.04.1) over (1.9.1-0ubuntu0.14.04.2) ...
Preparing to unpack .../liboxideqtcore0_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking liboxideqtcore0:amd64 (1.9.5-0ubuntu0.14.04.1) over (1.9.1-0ubuntu0.14.04.2) ...
Preparing to unpack .../oxideqt-codecs-extra_1.9.5-0ubuntu0.14.04.1_amd64.deb ...
Unpacking oxideqt-codecs-extra:amd64 (1.9.5-0ubuntu0.14.04.1) over (1.9.1-0ubuntu0.14.04.2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1) ...
Processing triggers for bamfdaemon (0.5.1+14.04.20140409-0ubuntu1) ...
Rebuilding /usr/share/applications/bamf-2.index...
Setting up chromium-codecs-ffmpeg-extra (45.0.2454.101-0ubuntu0.14.04.1.1099) ...
Setting up linux-image-3.13.0-65-generic (3.13.0-65.106) ...
Running depmod.
update-initramfs: deferring update (hook will be called later)
Not updating initrd symbolic links since we are being updated/reinstalled 
(3.13.0-65.105 was configured last, according to dpkg)
Not updating image symbolic links since we are being updated/reinstalled 
(3.13.0-65.105 was configured last, according to dpkg)
Examining /etc/kernel/postinst.d.
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-65-generic
Found initrd image: /boot/initrd.img-3.13.0-65-generic
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-62-generic
Found initrd image: /boot/initrd.img-3.13.0-62-generic
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-59-generic
Found initrd image: /boot/initrd.img-3.13.0-59-generic
Found linux image: /boot/vmlinuz-3.13.0-58-generic
Found initrd image: /boot/initrd.img-3.13.0-58-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-3.13.0-54-generic
Found initrd image: /boot/initrd.img-3.13.0-54-generic
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-image-extra-3.13.0-65-generic (3.13.0-65.106) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
update-initramfs: Generating /boot/initrd.img-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-65-generic
Found initrd image: /boot/initrd.img-3.13.0-65-generic
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-62-generic
Found initrd image: /boot/initrd.img-3.13.0-62-generic
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-59-generic
Found initrd image: /boot/initrd.img-3.13.0-59-generic
Found linux image: /boot/vmlinuz-3.13.0-58-generic
Found initrd image: /boot/initrd.img-3.13.0-58-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-3.13.0-54-generic
Found initrd image: /boot/initrd.img-3.13.0-54-generic
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Setting up linux-signed-image-3.13.0-65-generic (3.13.0-65.106) ...
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.13.0-65-generic
Found initrd image: /boot/initrd.img-3.13.0-65-generic
Found linux image: /boot/vmlinuz-3.13.0-63-generic
Found initrd image: /boot/initrd.img-3.13.0-63-generic
Found linux image: /boot/vmlinuz-3.13.0-62-generic
Found initrd image: /boot/initrd.img-3.13.0-62-generic
Found linux image: /boot/vmlinuz-3.13.0-61-generic
Found initrd image: /boot/initrd.img-3.13.0-61-generic
Found linux image: /boot/vmlinuz-3.13.0-59-generic
Found initrd image: /boot/initrd.img-3.13.0-59-generic
Found linux image: /boot/vmlinuz-3.13.0-58-generic
Found initrd image: /boot/initrd.img-3.13.0-58-generic
Found linux image: /boot/vmlinuz-3.13.0-57-generic
Found initrd image: /boot/initrd.img-3.13.0-57-generic
Found linux image: /boot/vmlinuz-3.13.0-55-generic
Found initrd image: /boot/initrd.img-3.13.0-55-generic
Found linux image: /boot/vmlinuz-3.13.0-54-generic
Found initrd image: /boot/initrd.img-3.13.0-54-generic
Found linux image: /boot/vmlinuz-3.13.0-53-generic
Found initrd image: /boot/initrd.img-3.13.0-53-generic
Found linux image: /boot/vmlinuz-3.13.0-52-generic
Found initrd image: /boot/initrd.img-3.13.0-52-generic
Found linux image: /boot/vmlinuz-3.13.0-51-generic
Found initrd image: /boot/initrd.img-3.13.0-51-generic
Found linux image: /boot/vmlinuz-3.13.0-49-generic
Found initrd image: /boot/initrd.img-3.13.0-49-generic
Found linux image: /boot/vmlinuz-3.13.0-48-generic
Found initrd image: /boot/initrd.img-3.13.0-48-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found linux image: /boot/vmlinuz-3.13.0-45-generic
Found initrd image: /boot/initrd.img-3.13.0-45-generic
Found linux image: /boot/vmlinuz-3.13.0-44-generic
Found initrd image: /boot/initrd.img-3.13.0-44-generic
Found linux image: /boot/vmlinuz-3.13.0-43-generic
Found initrd image: /boot/initrd.img-3.13.0-43-generic
Found linux image: /boot/vmlinuz-3.13.0-40-generic
Found initrd image: /boot/initrd.img-3.13.0-40-generic
Found linux image: /boot/vmlinuz-3.13.0-39-generic
Found initrd image: /boot/initrd.img-3.13.0-39-generic
Found linux image: /boot/vmlinuz-3.13.0-37-generic
Found initrd image: /boot/initrd.img-3.13.0-37-generic
Found linux image: /boot/vmlinuz-3.13.0-36-generic
Found initrd image: /boot/initrd.img-3.13.0-36-generic
Found linux image: /boot/vmlinuz-3.13.0-32-generic
Found initrd image: /boot/initrd.img-3.13.0-32-generic
Found Windows Boot Manager on /dev/sda1@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Setting up firefox (41.0.1+build2-0ubuntu0.14.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/firefox ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-locale-en (41.0.1+build2-0ubuntu0.14.04.1) ...
Setting up linux-headers-3.13.0-65 (3.13.0-65.106) ...
Setting up linux-headers-3.13.0-65-generic (3.13.0-65.106) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/dkms 3.13.0-65-generic /boot/vmlinuz-3.13.0-65-generic
Setting up linux-libc-dev:amd64 (3.13.0-65.106) ...
Setting up thunderbird (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Installing new version of config file /etc/apport/blacklist.d/thunderbird ...
Setting up thunderbird-locale-en (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Setting up thunderbird-gnome-support (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Setting up thunderbird-locale-en-us (1:38.3.0+build1-0ubuntu0.14.04.1) ...
Setting up oxideqt-codecs-extra:amd64 (1.9.5-0ubuntu0.14.04.1) ...
Setting up liboxideqtcore0:amd64 (1.9.5-0ubuntu0.14.04.1) ...
Setting up liboxideqtquick0:amd64 (1.9.5-0ubuntu0.14.04.1) ...
Setting up liboxideqt-qmlplugin:amd64 (1.9.5-0ubuntu0.14.04.1) ...
Setting up oxideqt-chromedriver (1.9.5-0ubuntu0.14.04.1) ...
Processing triggers for libc-bin (2.19-0ubuntu6.6) ...
W: Duplicate sources.list entry http://repos.cloudme.com/ ./ Packages (/var/lib/apt/lists/repos.cloudme.com_._Packages)
W: Duplicate sources.list entry http://repos.cloudme.com/ ./ Packages (/var/lib/apt/lists/repos.cloudme.com_._Packages)
W: Duplicate sources.list entry http://repos.cloudme.com/ ./ Packages (/var/lib/apt/lists/repos.cloudme.com_._Packages)
W: You may want to run apt-get update to correct these problems
todd@Dukla:~$ 

```

```

todd@Dukla:~$ sudo apt-get update
[sudo] password for todd: 
Ign http://apt.spideroak.com release InRelease
Ign http://APT.spideroak.com release InRelease                                 
Hit http://apt.spideroak.com release Release.gpg                               
Hit http://APT.spideroak.com release Release.gpg                               
Hit http://apt.spideroak.com release Release                                   
Hit http://APT.spideroak.com release Release                                   
Ign http://ppa.launchpad.net trusty InRelease                                  
Hit http://apt.spideroak.com release/restricted amd64 Packages                 
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://APT.spideroak.com release/restricted amd64 Packages                 
Ign http://repos.cloudme.com ./ InRelease                                      
Hit http://apt.spideroak.com release/restricted i386 Packages                  
Hit http://APT.spideroak.com release/restricted i386 Packages                  
Hit http://ppa.launchpad.net trusty Release                                    
Get:1 https://download.01.org trusty InRelease                                 
Ign https://download.01.org trusty InRelease                                   
Ign http://repos.cloudme.com ./ Release.gpg                                    
Get:2 https://download.01.org trusty/main amd64 Packages/DiffIndex             
Ign https://download.01.org trusty/main amd64 Packages/DiffIndex               
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Ign https://download.01.org trusty/main i386 Packages/DiffIndex                
Ign http://repos.cloudme.com ./ Release                                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://apt.spideroak.com release/restricted Translation-en_US              
Ign http://APT.spideroak.com release/restricted Translation-en_US              
Ign http://apt.spideroak.com release/restricted Translation-en                 
Ign http://APT.spideroak.com release/restricted Translation-en                 
Ign http://repos.cloudme.com ./ Packages/DiffIndex                             
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit https://download.01.org trusty/main amd64 Packages                         
Hit http://repos.cloudme.com ./ Packages                                       
Ign http://repos.cloudme.com ./ Translation-en_US                              
Hit https://download.01.org trusty/main i386 Packages                          
Get:3 https://download.01.org trusty/main Translation-en_US                    
Ign https://download.01.org trusty/main Translation-en_US                      
Ign https://download.01.org trusty/main Translation-en                         
Ign http://repos.cloudme.com ./ Translation-en                                 
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Hit http://extras.ubuntu.com trusty Release                                    
Hit http://extras.ubuntu.com trusty/main Sources                               
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Ign http://dl.google.com stable/main Translation-en                            
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Ign http://archive.canonical.com trusty InRelease                              
Hit http://archive.canonical.com trusty Release.gpg                            
Hit http://archive.canonical.com trusty Release                                
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://archive.canonical.com trusty/partner Translation-en                 
100% [Connecting to us.archive.ubuntu.com (2001:67c:1562::15)] [Connecting to s

```


[COLOR=#000000]
[/COLOR]

---

### Post by v3.xx on 2015-10-07
> W: Duplicate sources.list entry [http://repos.cloudme.com/](http://repos.cloudme.com/) ./ Packages (/var/lib/apt/lists/repos.cloudme.com_._Packages)
W: Duplicate sources.list entry [http://repos.cloudme.com/](http://repos.cloudme.com/) ./ Packages (/var/lib/apt/lists/repos.cloudme.com_._Packages)
W: Duplicate sources.list entry [http://repos.cloudme.com/](http://repos.cloudme.com/) ./ Packages (/var/lib/apt/lists/repos.cloudme.com_._Packages)

I would like to have a look at your sources list, please post the output of..

```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list

```
The update did not seem to finish or a few line were left out when you posted.  When the update finishes, it will return to todd@Dukla:~$.

You also need to remove those old kernels, please run..

sudo apt-get autoremove && sudo apt-get autoclean

See if that will remove them.  You can look at /boot to see if they have been removed.

---

### Post by Todd in Berlin on 2015-10-07
Thanks, v3! Following is the output you requested. I will check those other things, too.

But also after my last post it seems like everything could be downloaded and installed - e.g. I got a notice to restart Firefox as it had been updated - but a little while later I got a notification for a very small Ubuntu system update and that got hung up on Download just like before...

[COLOR=#000000]```
[/COLOR]todd@Dukla:~$ cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
# deb cdrom:[Ubuntu 14.04.1 LTS _Trusty Tahr_ - Release amd64 (20140722.2)]/ trusty main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty universe
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ trusty-backports main restricted universe multiverse


deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu trusty partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb http://archive.canonical.com/ trusty partner
# deb-src http://archive.canonical.com/ trusty partner
deb-src http://extras.ubuntu.com/ubuntu trusty main
deb http://repos.cloudme.com/ ./
deb http://repos.cloudme.com/ ./
deb http://repos.cloudme.com/ ./
deb http://repos.cloudme.com/ ./
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/intellinuxgraphics.list
/etc/apt/sources.list.d/mjblenner-ppa-hal-trusty.list
/etc/apt/sources.list.d/spideroak.com.sources.list
/etc/apt/sources.list.d/spideroakone.list
todd@Dukla:~$ [COLOR=#000000]
```[/COLOR]

---

### Post by Todd in Berlin on 2015-10-07
I ran autoremove and autoclean as suggested but not sure what Boot is supposed to look like now, so here is what it looks like: [https://db.tt/8G3kV69B](https://db.tt/8G3kV69B)

Thanks again!

---

### Post by v3.xx on 2015-10-07
Ok, to avoid confusion we will do a fix just one at a time.  So lets clean out all those old kernels first.  Run this command

```
dpkg -l linux-* | awk '/^ii/{ print $2}' | grep -v -e `uname -r | cut -f1,2 -d"-"` | grep -e [0-9] | grep -E "(image|headers)" | xargs sudo apt-get -y purge
```

[http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/](http://tuxtweaks.com/2010/10/remove-old-kernels-in-ubuntu-with-one-command/)

Now, with any luck, your /boot should be just about empty.

Follow that with

```
sudo update-grub
```

There is a problem with the new Trusty kernel, I have been reading about it today.  So do not reboot your system as that will upgrade the kernel if one is available.  And I want to know what kernel you are currently running after all this, so please post the output of..

```
uname -r
```

and also

```
ls /boot
```

---

### Post by Todd in Berlin on 2015-10-08
[COLOR=#000000]Great, thanks. Here goes nothin.....

```
[/COLOR]3.13.0-65-generic[COLOR=#000000]
```

and[/COLOR]

[COLOR=#000000]```
[/COLOR]abi-3.13.0-65-generic         memtest86+.elf
config-3.13.0-65-generic      memtest86+_multiboot.bin
efi                           System.map-3.13.0-65-generic
grub                          vmlinuz-3.13.0-65-generic
initrd.img-3.13.0-65-generic  vmlinuz-3.13.0-65-generic.efi.signed
memtest86+.bin[COLOR=#000000]
```[/COLOR]

---

### Post by v3.xx on 2015-10-09
Ok, that worked :)  Your /boot (old kernels) has been cleaned up.

Try another update in terminal, see if it still hangs.

```
sudo apt-get update
```

I suspect it will still hang up, so next we shall work on the sources.

> ## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
# deb-src [http://archive.canonical.com/](http://archive.canonical.com/) trusty partner
deb-src [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) trusty main
deb [http://repos.cloudme.com/](http://repos.cloudme.com/) ./
deb [http://repos.cloudme.com/](http://repos.cloudme.com/) ./
deb [http://repos.cloudme.com/](http://repos.cloudme.com/) ./
deb [http://repos.cloudme.com/](http://repos.cloudme.com/) ./
/etc/apt/sources.list.d/google-chrome.list
/etc/apt/sources.list.d/intellinuxgraphics.list
/etc/apt/sources.list.d/mjblenner-ppa-hal-trusty.list
/etc/apt/sources.list.d/spideroak.com.sources.list
/etc/apt/sources.list.d/spideroakone.list

You have multiple "cloudme" entries, you need to remove all but one, so open up your sources with..

```
software-properties-gtk
```

Go to "Other software" tab and either remove or just uncheck the duplicate cloudme entries.  And while your there, Go to the first tab and uncheck "Source Code".
Source code is used by developers and not needed by the standard user, so it can be unchecked without any issue.

Then close.  You will be asked to reload; do not.  Instead update (reload) using the terminal command.

You should no longer see the duplicate error entry.  Question is, will it complete the update or hang?

If it still hangs you need to temporary disable your third party software (PPAs).  So again open up the sources (software-properties-gtk) and just uncheck..

cloudme
google-chrome
intellinuxgraphics
mjblenner
spideroak

And again update in terminal.

I realize this is a lot for someone unfamiliar with terminal commands; please feel free to ask questions if my instructions are not clear.

Good luck :)

---

### Post by Todd in Berlin on 2015-10-09
Hi again. Thanks. With sudo apt-get it hung up temporarily but when I checked a little later it seemed to have worked it all out.

Do I still need to check out those other things? You're right: I don't fully understand your instructions. (Actually, I am not even using CloudMe and just checked with Synaptic Package Manager etc and it's not installed any longer - I thought I had unin stalled it some time ago.)

Here is the output from the last Terminal command:

```
 todd@Dukla:~$ sudo apt-get update[sudo] password for todd: 
Ign http://apt.spideroak.com release InRelease
Ign http://APT.spideroak.com release InRelease
Hit http://apt.spideroak.com release Release.gpg                               
Hit http://APT.spideroak.com release Release.gpg                               
Hit http://apt.spideroak.com release Release                                   
Hit http://APT.spideroak.com release Release                                   
Ign http://ppa.launchpad.net trusty InRelease                                  
Ign http://repos.cloudme.com ./ InRelease                                      
Hit http://ppa.launchpad.net trusty Release.gpg                                
Hit http://apt.spideroak.com release/restricted amd64 Packages                 
Hit http://APT.spideroak.com release/restricted amd64 Packages                 
Ign http://repos.cloudme.com ./ Release.gpg                                    
Hit http://apt.spideroak.com release/restricted i386 Packages                  
Hit http://APT.spideroak.com release/restricted i386 Packages                  
Get:1 https://download.01.org trusty InRelease                                 
Ign https://download.01.org trusty InRelease                                   
Hit http://ppa.launchpad.net trusty Release                                    
Get:2 https://download.01.org trusty/main amd64 Packages/DiffIndex             
Ign https://download.01.org trusty/main amd64 Packages/DiffIndex               
Ign http://repos.cloudme.com ./ Release                                        
Ign https://download.01.org trusty/main i386 Packages/DiffIndex                
Hit http://ppa.launchpad.net trusty/main amd64 Packages                        
Hit http://ppa.launchpad.net trusty/main i386 Packages                         
Ign http://repos.cloudme.com ./ Packages/DiffIndex                             
Ign http://apt.spideroak.com release/restricted Translation-en_US              
Ign http://APT.spideroak.com release/restricted Translation-en_US              
Ign http://apt.spideroak.com release/restricted Translation-en                 
Ign http://APT.spideroak.com release/restricted Translation-en                 
Ign http://ppa.launchpad.net trusty/main Translation-en_US                     
Ign http://ppa.launchpad.net trusty/main Translation-en                        
Hit http://repos.cloudme.com ./ Packages                                       
Hit https://download.01.org trusty/main amd64 Packages                         
Ign http://repos.cloudme.com ./ Translation-en_US                              
Hit https://download.01.org trusty/main i386 Packages                          
Ign http://repos.cloudme.com ./ Translation-en                                 
Get:3 https://download.01.org trusty/main Translation-en_US                    
Ign https://download.01.org trusty/main Translation-en_US                      
Ign https://download.01.org trusty/main Translation-en                         
Ign http://dl.google.com stable InRelease                                      
Hit http://dl.google.com stable Release.gpg                                    
Hit http://dl.google.com stable Release                                        
Hit http://dl.google.com stable/main amd64 Packages                            
Hit http://dl.google.com stable/main i386 Packages                             
Ign http://extras.ubuntu.com trusty InRelease                                  
Hit http://extras.ubuntu.com trusty Release.gpg                                
Ign http://dl.google.com stable/main Translation-en_US                         
Hit http://extras.ubuntu.com trusty Release                                    
Ign http://dl.google.com stable/main Translation-en                            
Hit http://extras.ubuntu.com trusty/main Sources                               
Hit http://extras.ubuntu.com trusty/main amd64 Packages                        
Hit http://extras.ubuntu.com trusty/main i386 Packages                         
Ign http://extras.ubuntu.com trusty/main Translation-en_US                     
Ign http://extras.ubuntu.com trusty/main Translation-en                        
Hit http://archive.canonical.com trusty InRelease                              
Hit http://archive.canonical.com trusty/partner amd64 Packages                 
Hit http://archive.canonical.com trusty/partner i386 Packages                  
Hit http://archive.canonical.com trusty/partner Translation-en                 
Ign http://us.archive.ubuntu.com trusty InRelease                              
Get:4 http://us.archive.ubuntu.com trusty-updates InRelease [64.4 kB]          
Get:5 http://us.archive.ubuntu.com trusty-backports InRelease [64.5 kB]        
Hit http://us.archive.ubuntu.com trusty Release.gpg                            
Get:6 http://us.archive.ubuntu.com trusty-updates/main Sources [238 kB]        
Get:7 http://us.archive.ubuntu.com trusty-updates/restricted Sources [4,722 B] 
Get:8 http://us.archive.ubuntu.com trusty-updates/universe Sources [140 kB]    
Get:9 http://us.archive.ubuntu.com trusty-updates/multiverse Sources [5,144 B] 
Get:10 http://us.archive.ubuntu.com trusty-updates/main amd64 Packages [629 kB]
Get:11 http://us.archive.ubuntu.com trusty-updates/restricted amd64 Packages [15.4 kB]
Get:12 http://us.archive.ubuntu.com trusty-updates/universe amd64 Packages [323 kB]
Get:13 http://us.archive.ubuntu.com trusty-updates/multiverse amd64 Packages [11.9 kB]
Get:14 http://us.archive.ubuntu.com trusty-updates/main i386 Packages [609 kB] 
Get:15 http://us.archive.ubuntu.com trusty-updates/restricted i386 Packages [15.1 kB]
Get:16 http://us.archive.ubuntu.com trusty-updates/universe i386 Packages [324 kB]
Get:17 http://us.archive.ubuntu.com trusty-updates/multiverse i386 Packages [12.1 kB]
Get:18 http://us.archive.ubuntu.com trusty-updates/main Translation-en [305 kB]
Get:19 http://us.archive.ubuntu.com trusty-updates/multiverse Translation-en [6,148 B]
Get:20 http://us.archive.ubuntu.com trusty-updates/restricted Translation-en [3,569 B]
Get:21 http://us.archive.ubuntu.com trusty-updates/universe Translation-en [170 kB]
Get:22 http://us.archive.ubuntu.com trusty-backports/main Sources [5,860 B]    
Get:23 http://us.archive.ubuntu.com trusty-backports/restricted Sources [28 B] 
Get:24 http://us.archive.ubuntu.com trusty-backports/universe Sources [28.8 kB]
Get:25 http://us.archive.ubuntu.com trusty-backports/multiverse Sources [1,898 B]
Get:26 http://us.archive.ubuntu.com trusty-backports/main amd64 Packages [6,288 B]
Get:27 http://us.archive.ubuntu.com trusty-backports/restricted amd64 Packages [28 B]
Get:28 http://us.archive.ubuntu.com trusty-backports/universe amd64 Packages [32.8 kB]
Get:29 http://us.archive.ubuntu.com trusty-backports/multiverse amd64 Packages [1,571 B]
Get:30 http://us.archive.ubuntu.com trusty-backports/main i386 Packages [6,293 B]
Get:31 http://us.archive.ubuntu.com trusty-backports/restricted i386 Packages [28 B]
Get:32 http://us.archive.ubuntu.com trusty-backports/universe i386 Packages [32.8 kB]
Get:33 http://us.archive.ubuntu.com trusty-backports/multiverse i386 Packages [1,552 B]
Get:34 http://us.archive.ubuntu.com trusty-backports/main Translation-en [3,645 B]
Get:35 http://us.archive.ubuntu.com trusty-backports/multiverse Translation-en [1,215 B]
Get:36 http://us.archive.ubuntu.com trusty-backports/restricted Translation-en [14 B]
Get:37 http://us.archive.ubuntu.com trusty-backports/universe Translation-en [29.7 kB]
Hit http://us.archive.ubuntu.com trusty Release                                
Hit http://us.archive.ubuntu.com trusty/main Sources                           
Hit http://us.archive.ubuntu.com trusty/restricted Sources                     
Hit http://us.archive.ubuntu.com trusty/universe Sources                       
Hit http://us.archive.ubuntu.com trusty/multiverse Sources                     
Hit http://us.archive.ubuntu.com trusty/main amd64 Packages                    
Hit http://us.archive.ubuntu.com trusty/restricted amd64 Packages             
Hit http://us.archive.ubuntu.com trusty/universe amd64 Packages                
Hit http://us.archive.ubuntu.com trusty/multiverse amd64 Packages              
Hit http://us.archive.ubuntu.com trusty/main i386 Packages                     
Hit http://us.archive.ubuntu.com trusty/restricted i386 Packages               
Hit http://us.archive.ubuntu.com trusty/universe i386 Packages                 
Hit http://us.archive.ubuntu.com trusty/multiverse i386 Packages               
Hit http://us.archive.ubuntu.com trusty/main Translation-en                    
Hit http://us.archive.ubuntu.com trusty/multiverse Translation-en              
Hit http://us.archive.ubuntu.com trusty/restricted Translation-en              
Hit http://us.archive.ubuntu.com trusty/universe Translation-en                
Ign http://us.archive.ubuntu.com trusty/main Translation-en_US                 
Ign http://us.archive.ubuntu.com trusty/multiverse Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/restricted Translation-en_US           
Ign http://us.archive.ubuntu.com trusty/universe Translation-en_US             
Get:38 http://security.ubuntu.com trusty-security InRelease [64.4 kB]          
Get:39 http://security.ubuntu.com trusty-security/main Sources [96.9 kB]
Get:40 http://security.ubuntu.com trusty-security/restricted Sources [3,357 B]
Get:41 http://security.ubuntu.com trusty-security/universe Sources [31.0 kB]
Get:42 http://security.ubuntu.com trusty-security/multiverse Sources [2,341 B]
Get:43 http://security.ubuntu.com trusty-security/main amd64 Packages [350 kB]
Get:44 http://security.ubuntu.com trusty-security/restricted amd64 Packages [12.4 kB]
Get:45 http://security.ubuntu.com trusty-security/universe amd64 Packages [117 kB]
Get:46 http://security.ubuntu.com trusty-security/multiverse amd64 Packages [3,691 B]
Get:47 http://security.ubuntu.com trusty-security/main i386 Packages [333 kB]
Get:48 http://security.ubuntu.com trusty-security/restricted i386 Packages [12.2 kB]
Get:49 http://security.ubuntu.com trusty-security/universe i386 Packages [117 kB]
Get:50 http://security.ubuntu.com trusty-security/multiverse i386 Packages [3,833 B]
Get:51 http://security.ubuntu.com trusty-security/main Translation-en [191 kB] 
Get:52 http://security.ubuntu.com trusty-security/multiverse Translation-en [1,679 B]
Get:53 http://security.ubuntu.com trusty-security/restricted Translation-en [3,076 B]
Get:54 http://security.ubuntu.com trusty-security/universe Translation-en [68.2 kB]
Fetched 4,507 kB in 14min 4s (5,339 B/s)                                       
Reading package lists... Done
W: GPG error: https://download.01.org trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A902DDA375E52366
W: Duplicate sources.list entry http://repos.cloudme.com/ ./ Packages (/var/lib/apt/lists/repos.cloudme.com_._Packages)
W: Duplicate sources.list entry http://repos.cloudme.com/ ./ Packages (/var/lib/apt/lists/repos.cloudme.com_._Packages)
W: Duplicate sources.list entry http://repos.cloudme.com/ ./ Packages (/var/lib/apt/lists/repos.cloudme.com_._Packages)
todd@Dukla:~$ 
```

---

### Post by v3.xx on 2015-10-10
> With sudo apt-get it hung up temporarily but when I checked a little later it seemed to have worked it all out.

Yes it has completed an update.  I am not sure how much of the above instructions you were able to complete, but whatever you have done is good.  You have updated.

I see the the duplicate sources are still there.  Is there a problem with the above instructions?  Is this any help?

[https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab](https://help.ubuntu.com/community/Repositories/Ubuntu#Third-Party_Software_Tab)

Let me know.

I also see that you have a GPG error.  Thats easy to take care of, so lets do it with the following code.

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys A902DDA375E52366

```
This will require another update, but before you do that I want to get the duplicate sources removed.  Let me know where you stand on this.

We are just about there :)

---

