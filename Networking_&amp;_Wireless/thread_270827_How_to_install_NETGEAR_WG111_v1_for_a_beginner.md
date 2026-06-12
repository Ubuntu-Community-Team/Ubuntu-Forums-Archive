---
title: "How to install NETGEAR WG111 v1 for a beginner"
date: 2006-10-03
forum: Networking &amp; Wireless
---

### Post by sankarj12 on 2006-10-03
Hello everyone.  I have a newbie to Linux, and I have a wireless network.  The computer that Ubuntu is installed on has a NETGEAR WG111v1 wireless USB adapter.  I am trying to make it work by using "ndiswrapper."  When I try to use the "make uninstall" command, it says that the command was not found.  Since the computer is not connected to the Internet (I use the wireless adapter, but I am trying to get it to work), I can't download packages.  Is there any way to import them?  How do I download them unto my USB drive (which DOES work).  I want a step-by-step guide, because I don't know what "source directory) is or anything like that.  Thanks in advance.](*,)

---

### Post by omarello on 2006-10-04
hey, i am a noob too but i think i can help u with this one as i have uninstalled and installed ndiswrapper from sources yesterday so i think i may have a clue on how to help you or at least guide u in the right direction.

first of u might want to check this link [Wifi Docs]("https://help.ubuntu.com/community/WifiDocs")

this site contains the ubuntu [packages tree]("http://archive.ubuntu.com/ubuntu/pool/main/")

as for installing and uninstalling ndiswrapper u can check the [wiki]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation")
[Ubuntu Specific]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu")

as for the command not found, i think u may have to be in the ndiswapper sources directory... check [Unistalling ndiswrapper]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Uninstall")

hope this helps, cause it frustrated me to a point where i was about to burst ](*,) , and yet i still couldn't get my internet to work :( ... bah hope u have better luck ...

---

### Post by omarello on 2006-10-04
ohh and this should help with installing the linux header

```

sudo apt-get install build-essential linux-headers-`uname -r`

```

the ` are not single quotes they are back tics found on the ~ key

---

### Post by sankarj12 on 2006-10-05
When I type in```
ndiswrapper -l
``` I get "driver present, hardware present", with eight numbers (four, a comma, and then four more).  When I remove and put in the adapter, the light comes on for a second, and then goes back off.  I got the packages by selecting the CD-ROM instead of the Internet.  Thanks for your help.  I think I'm almost there.  :-k

---

### Post by sankarj12 on 2006-10-07
It's working!  I followed the directions at [http://ubuntuforums.org/showthread.php?t=212321&highlight=netgear+wg111](http://ubuntuforums.org/showthread.php?t=212321&highlight=netgear+wg111), and it worked successfully.  Thank you for helping me and if I have any more Ubuntu problems I will always be back.:-D :KS

---

