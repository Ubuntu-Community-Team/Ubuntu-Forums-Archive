---
title: "Broadcom 802.11 Linux STA driver"
date: 2010-01-03
forum: New to Ubuntu
---

### Post by onegallon on 2010-01-03
just downloaded 9.1 on acer 4420-5963 with optional Vista still aboard. Everything fine except BCM4312 802.11 not making wireless connection, although cable connection to ethernet gets internet fine (apparantly an age-old problem with many past recommended work-arounds). However, just found Broadcom's Sept 17, 2009 release for 802.11 Linux STA driver for BCM4312 based hardware (goto Broadcom.com-802.11 Linux STA driver), and downloaded same to my Ubantu desk top. Release appears to be for direct installation in linux (no wrap around of a Windows driver, etc. required ?). Is this new release the answer to the above problem; and if so, how should I go about installing it? Am brand new to Linux and don't want to mess up. Thanks

---

### Post by bkratz on 2010-01-04
Getting the STA driver can be done this way; however, it really can be easier. See this posting

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)


This actually installs the STA driver  ( bcmwl-kernel-source) in step 4.3.2

---

### Post by onegallon on 2010-01-04
> **bkratz said:**
> Getting the STA driver can be done this way; however, it really can be easier. See this posting
 
[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)
 
 
This actually installs the STA driver ( bcmwl-kernel-source) in step 4.3.2
 Thanks appreciate the help

---

### Post by bkratz on 2010-01-04
> **onegallon said:**
> Thanks appreciate the help



If it works for you don't forget to come back and use the thread tools to mark as solved.

---

### Post by onegallon on 2010-01-05
Ouch. Installed for dual system using downloaded Wubi without making installation disk-thought could make boot disk later and didn't want to make the disk and then find it to have no choice for the dual (with Vista) system and have to start over. Now appears may have to uninstall and re-install making an installation disk, unless there is an easier way. Regarding recommended solution: got to 3.2. and found no "bcmwl-kernal-source". No live cd available at this time, so step 2. was out. However, did note presence in synaptic pkg manager of bcmwi-modaleases {which was} "installed as version 5.10.91.9 + bdcom", which sounds related to the necessary driver. Any way to make an installation disk without uninstalling and re-installing using WUBI? Or does bcmwi-modaleases suggest there is another way of proceeding? Thanks again for the help.

---

### Post by bkratz on 2010-01-05
> **onegallon said:**
> Ouch. Installed for dual system using downloaded Wubi without making installation disk-thought could make boot disk later and didn't want to make the disk and then find it to have no choice for the dual (with Vista) system and have to start over. Now appears may have to uninstall and re-install making an installation disk, unless there is an easier way. Regarding recommended solution: got to 3.2. and found no "bcmwl-kernal-source". No live cd available at this time, so step 2. was out. However, did note presence in synaptic pkg manager of bcmwi-modaleases {which was} "installed as version 5.10.91.9 + bdcom", which sounds related to the necessary driver. Any way to make an installation disk without uninstalling and re-installing using WUBI? Or does bcmwi-modaleases suggest there is another way of proceeding? Thanks again for the help.


The file you mentioned seems to be intrinsically involved ( spent a lot of time with Google this AM) in discovering which driver is needed, but it is not all that is needed. 

Perhaps in this case the best method would be to go to 

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

and actually get the Broadcom source files and build. The instructions are within the file.

Hope this helps

---

### Post by onegallon on 2010-01-05
thanks will check it out. If I uninstall using WUBI, then use UBI's Live Installation disk burn option, will the disk still provide the dual (vista and ubuntu) choice, in which case I would re-install from the disk {best situation}? If not, I guess I could back up and re-install direct from UBI selecting the dual option, but still have the burned live disk available for fixes. What do you recommend?

---

### Post by onegallon on 2010-01-06
> **bkratz said:**
> The file you mentioned seems to be intrinsically involved ( spent a lot of time with Google this AM) in discovering which driver is needed, but it is not all that is needed. 
 
Perhaps in this case the best method would be to go to 
 
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
 
and actually get the Broadcom source files and build. The instructions are within the file.
 
Hope this helps
Please ignore my last as I don't think it  will help using WUBI. Back to file building.
 
The package I have downloaded to my desktop from Broadcom is titled "hybrid-portsrc-x86_64-v5.10.91.9.3.tar.gz". It contains three folders: 1. "lib" with sub folders "license.txt" and "wic_hybrid.o_shipped"; 2. "SRC" with sub folders "include", "shared", and "wl"; 3. "makefile". 
 
"makefile" has a number of comments and then lists under the last comment the following command "$ ID: make file_kbuild_portssrc, v 1.1.2.4.84.1 2009/08/11 01: 19:20 EXP $" This looks to me to be a file builder routine for the updated driver,
although I don't think it's necessarily an ndiswrapper driver and am leery about
monkeying with something I don't understand, especially if it's not already on the UBUNTU radar screen, not authorized, and not useable under step 6 of WifiDocsDeviceBroadcom_BCM4311_rev__01_(ndiswrapper). Please advise. Thanks

---

### Post by bkratz on 2010-01-06
> **onegallon said:**
> Please ignore my last as I don't think it  will help using WUBI. Back to file building.
 
The package I have downloaded to my desktop from Broadcom is titled "hybrid-portsrc-x86_64-v5.10.91.9.3.tar.gz". It contains three folders: 1. "lib" with sub folders "license.txt" and "wic_hybrid.o_shipped"; 2. "SRC" with sub folders "include", "shared", and "wl"; 3. "makefile". 
 
"makefile" has a number of comments and then lists under the last comment the following command "$ ID: make file_kbuild_portssrc, v 1.1.2.4.84.1 2009/08/11 01: 19:20 EXP $" This looks to me to be a file builder routine for the updated driver,
although I don't think it's necessarily an ndiswrapper driver and am leery about
monkeying with something I don't understand, especially if it's not already on the UBUNTU radar screen, not authorized, and not useable under step 6 of WifiDocsDeviceBroadcom_BCM4311_rev__01_(ndiswrapper). Please advise. Thanks

Truthfully I don't totally understand your question. This driver is not used under ndiswrapper at all. Ndiswrapper is only used for Windows drivers (usually that is what you get on the disk with the card). Are these statements referring to what is said in the readme? I will download it and see if I can understand.


I have 0 experience with wubi having installed dual boot with XP in one and pure Ubuntu in two others. The dual boot system allows me to select either Windows or Ubuntu a power up.

 Carlee in post 6 of this thread mentions the build sequence.
[http://ubuntuforums.org/showthread.php?p=8488269](http://ubuntuforums.org/showthread.php?p=8488269)

I have only "built" one driver so I would feel uncomfortable trying to direct someone on the process. I don't mind screwing up my system but not someone elses.

The first way stated would sure be easier!

---

### Post by onegallon on 2010-01-06
> **bkratz said:**
> Truthfully I don't totally understand your question. This driver is not used under ndiswrapper at all. Ndiswrapper is only used for Windows drivers (usually that is what you get on the disk with the card). Are these statements referring to what is said in the readme? I will download it and see if I can understand.


I have 0 experience with wubi having installed dual boot with XP in one and pure Ubuntu in two others. The dual boot system allows me to select either Windows or Ubuntu a power up.

 Carlee in post 6 of this thread mentions the build sequence.
[http://ubuntuforums.org/showthread.php?p=8488269](http://ubuntuforums.org/showthread.php?p=8488269)

I have only "built" one driver so I would feel uncomfortable trying to direct someone on the process. I don't mind screwing up my system but not someone elses.

The first way stated would sure be easier!
Thought I already replied, but don't see it. I surmised that the Broadcom downloaded
file was not a windows file useable with ndswrapper, but hoped maybe it was a linex file that could
be used to make and install a linex driver directly; and since it was released in Sept. 09, use of it
might have been incorporated in the official UBUNTU documentation. Apparantly not. I think I better
consider uninstalling the WUBI version and downloading the UBUNTU version, making a disk, and reinstalling from same. That way If the card is then not recognized, I  could proceed on through the nallen00 solution. May not do this for awhile, since I would like to gain a little more UBUNTU
experience using my inconvenient but available ethernet cable connection. Thanks again for your patience and help, especially the reference to nallen00.

---

### Post by onegallon on 2010-01-07
> **bkratz said:**
> Truthfully I don't totally understand your question. This driver is not used under ndiswrapper at all. Ndiswrapper is only used for Windows drivers (usually that is what you get on the disk with the card). Are these statements referring to what is said in the readme? I will download it and see if I can understand.
 
 
I have 0 experience with wubi having installed dual boot with XP in one and pure Ubuntu in two others. The dual boot system allows me to select either Windows or Ubuntu a power up.
 
Carlee in post 6 of this thread mentions the build sequence.
[http://ubuntuforums.org/showthread.php?p=8488269](http://ubuntuforums.org/showthread.php?p=8488269)
 
I have only "built" one driver so I would feel uncomfortable trying to direct someone on the process. I don't mind screwing up my system but not someone elses.
 
The first way stated would sure be easier!
 
 
SUCCESS! Downloaded and burned Live installation disk. Uninstalled and reinstalled
using downloaded WUBI still resident on my desktop. While cabled to ethernet and with Live disk in E drive went SYSTEM>ADMINISTRATION>SYNAPTIC PKG MGR. Then Search. not much luck at first, and wasn't familiar with how search worked, but on one pass put in ndis and toggled search. Up came ndisgtk, ndiswrapper-utils-1.9, and ndiswrapper common. Selected one, and all three auto selected for installation.
toggled INSTALL. Then went to SYSTEM>ADMINISTRATION>HARDWARE DRIVERS and after a few seconds delay, up popped two  Broadcom drivers, neither of which were installed. Chose second one because it looked like the new the Broadcom STA Driver. Installed and activated it. Computer's Yellow driver light came on. Then established wireless network contact without further trouble. Once again, thank you for your patience and help.

---

### Post by onegallon on 2010-01-07
> **onegallon said:**
> Thought I already replied, but don't see it. I surmised that the Broadcom downloaded
file was not a windows file useable with ndswrapper, but hoped maybe it was a linex file that could
be used to make and install a linex driver directly; and since it was released in Sept. 09, use of it
might have been incorporated in the official UBUNTU documentation. Apparantly not. I think I better
consider uninstalling the WUBI version and downloading the UBUNTU version, making a disk, and reinstalling from same. That way If the card is then not recognized, I could proceed on through the nallen00 solution. May not do this for awhile, since I would like to gain a little more UBUNTU
experience using my inconvenient but available ethernet cable connection. Thanks again for your patience and help, especially the reference to nallen00.
 
Already wrote reply but must not have properly submitted, so here goes again.
 
SUCCESS! Downloaded UBUNTU and burned LIVE disk. Uninstalled and re-installed
using previously downloaded WUBI on desk top. Booted. With Live disk in E drive
and ethernet cable connected, went >SYSTEM>ADMINISTRATION>SYNAPTIC PKG MANAGER. Went looking for ndswrapper with out much success, but after several attempts entered ndis in SEARCH and up popped ndisgtk, hdiswrapper-utils-1.9, and ndiswrapper-common. Marked one for installation and the other two auto marked.
Toggled install and files installed. Then went to SYSTEM>ADMINISTRATION>HARDWARE DRIVERS. After a couple of seconds two
drivers popped up, neither of which was installed. One was a BROADCOM wireless B43
driver and the other a BROADCOM STA wireless driver. I selected the STA, installed and activated it. Computer's wireless light came on. Rebooted and then was able to connect to wireless network in normal fashion. Not used to the forum and may have
replied to the thread, but thank you bkratz for all your help . Have marked thread solved.

---

### Post by bkratz on 2010-01-07
Congratulations!

---

