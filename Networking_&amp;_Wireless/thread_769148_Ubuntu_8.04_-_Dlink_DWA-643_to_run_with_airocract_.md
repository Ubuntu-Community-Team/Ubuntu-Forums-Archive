---
title: "Ubuntu 8.04 - Dlink DWA-643 to run with airocract etc. Madwifi?"
date: 2008-04-26
forum: Networking &amp; Wireless
---

### Post by Infernox222 on 2008-04-26
Hello all, I am currently in day 3 of my first time of learning Linux and I am having a hell of a time with it. Yesterday I went out and got a DLink DWA-643 ExpressCard for my laptop mainly for airocrack and similar programs. I am under the impression that madwifi has to be used for such programs to run but I have no idea how to do this. So far I have followed instructions [here...]("http://ubuntuforums.org/archive/index.php/t-542773.html") [here...]("https://help.ubuntu.com/community/WifiDocs/NdiswrapperOnAMD64") [here...]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") [and here...]("https://help.ubuntu.com/community/ExpressCard") At the moment the DLink will not even turn on. The '*sudo modprobe pciehp pciehp_force=1*' command had no output when entered and if I use '*sudo modprobe netwrapper*' I get the error '*FATAL: Module netwrapper not found.*' even though '*ndiswrapper -l*' returns '*net5416 : driver installed device (168C:0024) present*' I am not sure if anyone can help but any suggestion would be appreciated. If you need to know my laptops internal wireless work and is connected no problem. 

On a side note: When every i try to do a make command to a folder recently unpacked (using tar xvvofp) the program finishes with an Error any ideas? Also is ./configure not supposed to work in Ubuntu? I try this command (it was said in the installation of programs) and it says its not valid.

Thank you,
Mike

---

