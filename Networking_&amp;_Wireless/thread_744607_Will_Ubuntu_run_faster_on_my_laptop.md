---
title: "Will Ubuntu run faster on my laptop?"
date: 2008-04-03
forum: Networking &amp; Wireless
---

### Post by mbenson111 on 2008-04-03
I have an older 1.3Ghz Celeron laptop running XP Pro. It works alright, but I was interested in moving to Ubuntu. I was wondering if, out of the box, Ubunto would be a performance improvement with it's GUI.

Any help is appreciated.

---

### Post by pseudo-random on 2008-04-03
Yes. It doesn't run as much 'helpful' crap in the background.

---

### Post by jaem on 2008-04-03
I would agree - at least in theory, it will likely run faster.  I have a 3-year old 1.73GHz Centrino laptop, with a lousy cheap Intel video card, and it runs great - even with as much eyecandy (or more) as Vista and OS X. Plus, it's not a RAM hog - and, in fact, this release runs much *more* smoothly for me than the last one.  And believe me, Vista wouldn't come close to running decently (if at all) on my machine, not to mention Aero, yet Ubuntu 8.04 works just as well, and looks better!
EDIT: as always, however, YMMV

---

### Post by dmizer on 2008-04-04
what video card do you have in your laptop?

you may think about using xubuntu (xfce) instead of ubuntu.  just as much usablity and eye candy capability, without the overhead that comes with gnome so it responds faster on older equipment.

---

### Post by ugm6hr on 2008-04-04
No definite way to find out without trying it.

Xubuntu is generally always faster than XP SP2.  Ubuntu can also be in most cases.

The more RAM you have, the less likely you are to notice the difference.

I have a Dell 500m with a Centrino (I think 1.3GHz too) and initially 256MB RAM: Ubuntu was easily faster (on a dual-boot).  Following addition of a further 512MB RAM (i.e. 768 total), the difference still exists, but XP benefits a lot more, so the relative difference seems less now.

---

### Post by mbenson111 on 2008-04-04
@ugm6hr - 

I also have 768, so you have a good point.
I saw xubuntu but am unsure of what it is exactly.

Another issue is my network card. I have a Dlink DWL G630 and I couldn't find drivers for it, from DLink, at least.

Argh.. I don't want to format, to try it.. Would I get a good idea if on the performance if I were to install the dual boot trial setup? (forget what it's called, but I will look at it)

---

### Post by ugm6hr on 2008-04-04
> **mbenson111 said:**
> @ugm6hr - 

I also have 768, so you have a good point.
I saw xubuntu but am unsure of what it is exactly.

Another issue is my network card. I have a Dlink DWL G630 and I couldn't find drivers for it, from DLink, at least.

Argh.. I don't want to format, to try it.. Would I get a good idea if on the performance if I were to install the dual boot trial setup? (forget what it's called, but I will look at it)

If you are just starting out, with 768MB, you may as well stick with Ubuntu rather than Xubuntu.  The difference is predominantly cosmetic since Gutsy (7.10), with Ubuntu using Gnome vs Xubuntu using XFCE as Desktop Environments.  Ubuntu is marginally easier to get support for, since it has more users; although the same support generally applies to Xubuntu too with minor modifications.

DWL G630 has a variety of chipsets depending on which version you have - I think the Atheros one works without any additional driver, while the RT61 will need a bit of work.  Not sure if there are others too.  You can check by downloading and burning a LiveCD, and entering the following command in Terminal:
```
lshw -C network
```

This explains how to get the LiveCD and install a dual-boot ([http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)), which can be done without formatting (although data backup prior to installation is a good idea).  And yes - dual-boot performance on both XP and Ubuntu are the same as single OS.

Good luck.

---

### Post by mbenson111 on 2008-04-04
I will try that out.. I am also downloading the server installation. I already use Apache/MySQL/PHP, so it's right in the ballpark.. Love it.

Thanks a lot.. I will post back with results.

---

### Post by mbenson111 on 2008-04-04
Everything seems to run fine out of the box, save the network cards. It even has the HP printer installer built in. That's great. I downloaded it yesterday, and noticed it was there in the "control panel" already. 


 I have the following using the lshw -C network command. 

ubuntu@ubuntu:~$ lshw -
ubuntu@ubuntu:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:5f:d1:63
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes



  *-network UNCLAIMED
       description: Ethernet controller
       product: Marvell W8300 802.11 Adapter
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 07
       width: 32 bits
       clock: 66MHz
       capabilities: cap_list
       configuration: latency=0
ubuntu@ubuntu:~$ 

 I am more concerned with getting the wireless card working. I just need to figure out how to find the driver, and then install it.

I must say that I like the look and feel  of the OS. It runs fine, even when  run from the CD. If I can get the network card running, I will likely use it.

---

### Post by dmizer on 2008-04-05
need to know the wireless card chipset.

post the output of:
```
lspci
```

---

### Post by ugm6hr on 2008-04-06
> **dmizer said:**
> need to know the wireless card chipset.

Already given (lshw):
> product: Marvell W8300 802.11 Adapter
vendor: Marvell Technology Group Ltd.

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_c-f/) (No 34)
> Card: D-Link DWL-G630
Chipset: Marvell W8300
pciid: 11ab:1fa6
Driver: [http://www.asus.com.tw/support/download/item.aspx?ModelName=WL-138G](http://www.asus.com.tw/support/download/item.aspx?ModelName=WL-138G)
Other: Works with WEP and WPA with TKIP cipher.

Looks like this will work fine with ndiswrapper (as above).  However, I'm not sure that it is possible to try it without installing to HD.

EDIT: That link doesn't work - here is what appears to be the same file: [http://dlsvr01.asus.com/pub/ASUS/wireless/WL-138g/Driver.zip](http://dlsvr01.asus.com/pub/ASUS/wireless/WL-138g/Driver.zip) - this should work with 32-bit Ubuntu.

---

### Post by mbenson111 on 2008-04-06
This is good news. 

I apologize for all of the questions, but I am not a Linux guy. I have learned a bit about 10 years ago with a version of RedHat, but didn't retain anything, really. 

I will try to help myself, rather than just get you to walk me through this stuff.  I am now going to try to figure out how to go about installing the ndis wrapper for the wireless card, if possible without installing to the HD, and get the driver running. I hadn't noticed that the internal network card worked on startup, so that is a bonus. 

Can I assume that Ubuntu 7.10 doesn't have the ndis wrapper in the distro?

---

### Post by ugm6hr on 2008-04-06
> **mbenson111 said:**
> Can I assume that Ubuntu 7.10 doesn't have the ndis wrapper in the distro?

True.... Unfortunately Ubuntu doesn't include ndiswrapper unlike most other "new Linux user-friendly" distros.

If you open Synaptic Package Manager:
search and select *ndisgtk* for installation.

You should then be able to find "Windows Wireless Driver" somewhere in the menu.

You then select the correct .inf file (co-locted in same directory with .sys and any other important files).

Hopefully, it should then just work.  However, my experience with ndiswrapper in Ubuntu is very limited.... but there are lots of guides out there because of the difficulties.

---

### Post by mbenson111 on 2008-04-06
I'm not sure I follow you on the search. I opened the Synaptic Package Manager, and clicked the search icon.

Once that was up, I looked for anything regarding ndisgtk, but didn't see anything. I tried searching for wireless windows driver, under All, with Name, then Desciption and Name, etc. I also tried searching for "ndisgtk", but found nothing. 

I then decided to download the ndiswrapper from the link you provided. 

I didn't understand a couple of things. The prerequisites stated that I need at least a kernel of 2.6.6, or 2.4.26, with header files for the kernel. I saw that it was 2.6.2 (it wasn't 2.6.6).

I then proceede to use the tar zxvf ndiswrapper-1.52.tar.gz command. It created the proper directory.

I changed to that directory, and ran make uninstall with no errors.

I then ran make, then loged in as root, and rand make install, and got a bunch of errors.  A lot of those were implicit declaration of function 'XXX".

I am going to take a step back, relax, take a breath, and start over again later.  I appreciate your ear on this, as I am not trying to bother you. I just want to get this right..

---

### Post by ugm6hr on 2008-04-06
Need to check a couple of things:
1. What version of Ubuntu are you using?
2. Can you connect online with Ubuntu (wired ethernet)?
3. Have you enabled the repos (see link in my signature)?
4. Have you actually installed, or still using LiveCD?

Then try the instructions again.

You do not need to download ndiswrapper manually.

---

### Post by mbenson111 on 2008-04-06
1- I am using Ubutntu 7.10.
2- I am able to connect via wired ethernet. 
3- Not sure what that is, but I will check the link to be sure. :)
4- I have not done the installation because I want to make sure I am going to be able to use the wireless card. You know how much of a pain in the a$$ Windows is, right? ;)

One thing I did note was that Ubuntu seems to be using the hard drive for making system changes. Wether they are temporary files, I can't say as yet, but I am able to make system changes, so that would indicate that I should be able to use the packages from download, at least temporarily.

I will look into your links to see, and post back.

Thanks again.

---

### Post by ugm6hr on 2008-04-06
If you are online with wired, and repos all enabled, then ndisgtk is definitely in there.

I have never done this from a LiveCD, but don't see why it should be any different (in your case - since you don't have a default linux driver installed).

---

### Post by mbenson111 on 2008-04-07
Alright.

I enabled the repos properly and  installed the Wireless networking module. Thanks for the link, and the info on that, by the way. Once I got it installed, I was able to get the wireless -WinXP- driver installed.

After looking around in there, and setting up the wireless connection,  it recognized the hardware for what it is, and the SSID, but it didn't seem to work properly. I couldn't get an address. I unpluged the card, and inserted it again. I then went up to the network icon (top right), and went into the" wireless network", and connected to a "new wireless network". This allowed me to connect to the proper SSID, entered manually, and change the value of the WEP key to 64bit, and it seemed to connect. I got the signal bar, at 90%,  but then the machine froze.

That is a step in the right direction, for sure. Now I just need to figure out why it froze. I am going to reboot, and see if it retains the information. If not, I will need to contemplate wether or not to just go ahead and install to the HDD. 

Any thoughts on why it may have frozen? 

Thanks a LOT for all of the help too. I really appreciate it.

---

### Post by mbenson111 on 2008-04-07
Well friend, I would like to take this time to thank you for all of your help. I am coming to you from my laptop, wirelessly from my living room, 

I rebooted, and the info was not there. But when I reinstalled the wireless module, and the driver, I went right into the wireless networking, and this time it allowed me to make the connection, and setup the WEP type right off the hop.

With your help, I got it going. I thank you so very much for your time, effort, and patience with me. 

I am going to install to the HD this weekend once I have all my stuff backed up, and make the switch. 

I am also getting an old 2.4GHz P4 PC from a friend and am going to setup the Server version.  That will be an experience in and of itself. I will be back here, don't doubt. :)

Thanks again, and you are a great asset to this community.

-Mike

---

### Post by ugm6hr on 2008-04-07
> **mbenson111 said:**
> Thanks again, and you are a great asset to this community.

I knew that ;)

Seriously though - welcome aboard.

I've never done a server setup... but there are plenty of people more technically minded than I who will guide you through that too.

---

