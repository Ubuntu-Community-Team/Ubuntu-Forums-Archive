---
title: "I cannot connect to the Internet in Ubuntu-"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by andreaborman on 2011-05-11
I have just installed Ubuntu 11 a few hours ago. I have installed it alongside Windows 7 on the same computer. I installed Ubuntu by mounting the iso file which I downloaded from the Ubnutu website and mounting it on virtual clone drive. Then Waubi installer finished the installation. 

But on Ubuntu I cannot connect to the Internet at all. On both wired broadband and wireless broadband it does not connect to the Internet. It connects for about 1 second then disconnects and it just keeps doing that.

So I have not been able to connect to the Internet at all on Ubuntu.

But when I log into Windows 7 which is also installed on my computer I don't have any problems at all connecting to the Internet. So both my wired and wirless broadband connection are working fine on Windows 7 but not on Ubuntu.

I have tried uninstalling Ubuntu and reinstalling it again but this did not work either. And I still have the same problem.

And I phoned my Internet service provider and asked them if they are blocking any Internet connections or ports to connect to Ubuntu or Linux and they said they are not.

So what is the problem? Why can't I connect to the Internet by wired or wirless broadband on Ubuntu. And yet on Windows my Internet connection is working good. But on Ubnutu nothing,no Internet connection. How can I solve this problem.?

I have limited experience with Linux. But I have read that some people install drivers from the package manager. But I can't do this because you need to be connected to the Internet to use package manager. And I cannot connect to the Internet! 

So how do I solve this problem? Andrea.

---

### Post by Dondermans on 2011-05-11
If I were you, I would verify the checksum of the .iso file you downloaded (hashes: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)). If it checks out, I would try creating a LiveCD by burning the .iso file to a CD or DVD following this guide:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Then I would boot my computer from the LiveCD. Whatever happens, you would be able to narrow down the cause of the problem. From there we could suggest further steps.

---

### Post by taseedorf on 2011-05-11
try opening a terminal or "command line" and running sudo ifconfig

see what shows up

try this command

sudo ifconfig eth0 up for wired
sudo ifconfig wlan0 up for wireless

see if that works...?

---

### Post by grahammechanical on 2011-05-11
Hi

Please remember that you have installed Ubuntu using wubi. That means that Ubuntu is working just like any other program in the Windows 7 operating system. It is accessing the computer's hardware through the Windows 7 operating system.

Is it possible to switch off networking when you are using Windows 7? Are you doing that? If so, then this will surely prevent Ubuntu from using the ethernet (wired) and wireless adapters in your computer.

You should not need drivers to use a wired (ethernet) connection. They are built into Ubuntu. You may need drivers to use a wireless connection. On my system I do not need to install additional drivers to use a wireless connection. The drivers for my wireless adapter are built in.

To make a wireless connection you will need to select a wireless network, select an encryption method, and enter a pass phrase. This is not your login password but a special code that allows access to the router/modem. It is usually printed on a label stuck on the bottom of the router.

When you are in Ubuntu do you see a network manager icon? Is there a red exclamation mark against it? When you click on the icon do you see a list of available wireless networks? Is there a tick mark against the lines Enable Networking and Enable Wireless? If not put the tick mark there by clicking on those lines. The exit Ubuntu and re-load Ubuntu.

You might want to look through the wubi megathread in the Installation and Upgrades part of this forum.

Regards.

---

### Post by rkillcrazy on 2011-05-11
I've also seen rare cases where a setting you tweak in Windows will break something in Linux.  It's been a while since I ran into it but in my case, I think it was the option to allow the NIC to sleep to save energy.  You can tweak that setting in Windows and, in my case, the option was allowed.  Evidently, that was bad...  Once I turned off that option, all was well again.  The rest of my guys in my IT shop couldn't believe it but I could reproduce it and I had also sent them the link to the page on a forum that helped me figure it out....  I'm not saying this is the issue but it's one worth looking into as settings in Windows are often overlooked when troubleshooting Linux.

---

### Post by andreaborman on 2011-05-11
Thank you for your reply. As I explained, I downloaded VIRTUAL CLONE DRIVE from the website and mounted the Ubuntu iso file which I downloaded from the Ubnuntu website onto the virtual clone drive. I got the idea to install Ubuntu in this way from the How To Geek website see here [http://www.howtogeek.com/howto/20079/install-linux-mint-on-your-windows-computer-or-netbook/](http://www.howtogeek.com/howto/20079/install-linux-mint-on-your-windows-computer-or-netbook/)

That is the iso file is mounted on the clone drive and then the Waubi installer finishes the installation. So Ubnutu is installed inside Windows. And can be uninstalled again the same way the other Windows programs are.

And 2 days ago, before I installed Ubnuntu,I installed Linux Mint 11 RC Katya on the same computer. The Linux Mint 11 was installed the same way the Ubuntu was. It was mounted on virtual clone drive and Mint 4 Windows installer finished the install. And on Linux Mint too I had the same problem as I have got in Ubuntu, and could not connect to the Internet. So I uninstalled the Linux Mint(I am experimenting or trying out different brands of Linux)and I tried Ubuntu. But I have the same problem with Ubuntu.I cannot connect to the Internet.

I then, thought I might have a fault on my computer so I tried restoring my computer back to factory condition. Which puts the computer back to the way it was before I bought it. And as I installed Ubuntu inside Windows. That got uninstalled along with my other Windows programs.So after the factory restore was complete I reinstalled Ubuntu again.

 But I still have the same problem as before I did the factory restore to my computer.But I do not have this problem on Windows where I can and I am connected to the Internet on Windows 7. But I cannot connect to the Internet on Ubuntu, or it seems any brand of Linux now. The Internet connection is only working on Windows. I do not know why.

I now think but I do not know,that my previous install of Linux Mint 11 Katya may have some how corrupted some thing in the Linux network files or caused the problem I have got now with Ubnuntu. Because Linux Mint 11 is an RC release so it is only in the beta stage. So it could have corrupted my computer or files on the Linux side. But I have scanned my Windows 7 and I do not have a computer virus on Windows 7, so it is not that.

And please also note that I have used Ubuntu and Linux Mint 9 in the past and I did not have this problem connecting to the Internet before.But I do now since I installed the Linux mint 11 which I removed and replaced with Ubuntu.

The reason I removed the Linux Mint 11 Katya,their new release was because of the same reason,I could not connect to the Internet on that either. It kept disconnecting my wired and wirless network after 1 second. Just like Ubuntu is doing now.

So I think the Linux Mint 11 RC which is a bata release may have corrupted or messed up some thing, but I do not know what. Am I right? Andrea,

---

### Post by ravikanth.vva on 2011-05-11
im new to ubuntu or linux...but initially i had the same problem......i clicked a button on the top pannel on the right which connectd my system to internet.....this is too simple u might hav tried it but mentiond
anyway

---

### Post by andreaborman on 2011-05-11
I telephoned my Internet service provider after I found this page on the Internet. Read this-


"BT Website- [http://btybb.custhelp.com/app/answers/detail/a_id/8629/~/which-operating-systems-does-the-bt-home-hub-support%3F](http://btybb.custhelp.com/app/answers/detail/a_id/8629/~/which-operating-systems-does-the-bt-home-hub-support%3F)

Which operating systems does the BT Home Hub support?
  

We provide technical support for the BT Home Hub on Microsoft Windows 98SE, ME, 2000 and XP, as well as MAC OS 9 and MAC OS X. We are unable to provide technical support to customers using the Linux family of Operating Systems." 



So I phoned BT, my ISP to ask them again if they are blocking any of my Internet connections to Linux.They said that they are not blocking or stopping me connecting to the Internet on Linux. But they do not give technical advice or support for the Linux operating system.Which means that I can connect to Linux through BT, my internet connection, but they will not advise me if things go wrong.

Which is not exactly very helpful.But at least I know now that BT my ISP is not blocking my Internet connection on Linux. And I am sure that there are other people in England who have got BT as their Internet service provider. And that other BT customers like me are using Linux like I am. Indeed my next door neighbours are using Linux and they have got BT. So it cannot be my network service provider that is stopping me from connecting. 

And yes,I did check my network in Windows 7 and nothing is disabled so that is not the problem either. And as I said,I have connected to the Internet on Ubuntu and Linux Mint. Through BT my network service provider before, when I used Linux in the past. I just cannot now and I do not know why. 

In the past,when I used Linux Mint,the earlier versions,I found that at first I had to plug into wired broadband. And then I clicked configured hardware drivers and clicked activate drivers. And then after I restarted my computer all of the wireless networks were displayed. And then I just connected to my one by entering my wireless network key.

But this is not happening now. The first time I installed Ubuntu,it did display the wireless networks. But I could not connect to them and could not connect to wired broadband either.

So I reinstalled Ubuntu as I explained and now only the wired network is displayed. But I cannot even connect to that. I really do not know how to solve this problem.I cannot connect to the Internet at all on Ubuntu or even on Linux Mint.Yes,I tried that too before I installed Ubuntu. Yet on Windows I can connect to the Internet. But not on Linux.

I just do not know what to do as I do not have any experience in Linux. To be able to fix this problem.
Andrea.

---

### Post by andreaborman on 2011-05-11
> **taseedorf said:**
> try opening a terminal or "command line" and running sudo ifconfig

see what shows up

try this command

sudo ifconfig eth0 up for wired
sudo ifconfig wlan0 up for wireless

see if that works...?

Update-I have just tried using those commands you told me about in the terminal. And all I got was a message saying- ifconfig'--help' gives usage information. But when I typed in the command-ifconfig--help like the terminal said,nothing happened. The only thing that came up in the terminal was >

Also I clicked on the above weblinks that you gave me and I got redirected to a blank page.

So what do I do now? The commands you gave me just do not work. And I still have the same problem. Andrea.

---

### Post by BertN45 on 2011-05-11
You connect to the Internet by an Ethernet cable. You probably have a missing driver, a wrong driver or one that did not start automatically for some reasons.. You select Ubuntu during the boot process, so it will need its own set of drivers for the Internet connection.

First check the network icon in the top right corner, make sure  that the networking is enabled.  Try clicking on Auto-eth0.

How does windows connect to the Internet? What does the Device Manager in System tell about the network cards and drivers. 

Or alternatively in Ubuntu type **lspci** in the terminal and copy/paste the result back into your reply, that command will list all PCI devices that are connected to the machine.

---

### Post by K_45 on 2011-05-11
If you are using DHCP all you should need to do is insert the Ethernet cable into your PC from the router and wait a few secs. Otherwise try:

```
sudo dhclient eth0
```

---

### Post by andreaborman on 2011-05-11
Thank you for your reply. Windows just sets the settings itself and connects to the Internet automatically. All I have to do is plug in my router and turn it on. And my Internet connection comes from my telephone line. And I can connect to the Internet on wired or wireless broadband. But it is not working on Linux. BT provides both my telephone line and my Internet connection.

And if I want to check my network settings Windows will scan and troubleshoot and change the settings to the correct ones. If need be. I don't know if you have got Windows but on Windows 7,it does it all for you.

But on Linux it is obviously different. I just want to ask-I use Linux generic recover mode quite a lot, and one of the options I selected was drop root network with shell prompting. Could this be the cause of my problem? Andrea.

---

### Post by BertN45 on 2011-05-11
> **andreaborman said:**
> Thank you for your reply. Windows just sets the settings itself and connects to the Internet automatically. All I have to do is plug in my router and turn it on. And my Internet connection comes from my telephone line. And I can connect to the Internet on wired or wireless broadband. But it is not working on Linux. BT provides both my telephone line and my Internet connection.

And if I want to check my network settings Windows will scan and troubleshoot and change the settings to the correct ones. If need be. I don't know if you have got Windows but on Windows 7,it does it all for you.

But on Linux it is obviously different. I just want to ask-I use Linux generic recover mode quite a lot, and one of the options I selected was drop root network with shell prompting. Could this be the cause of my problem? Andrea.

Windows does it all for you and Ubuntu does it all for you, unless there is some hardware or software problem. And yes I have used all windows releases since windows 3.1 around 1993.  If you "drop the network" in recovery mode, like in windows, it will not.load the network stack, but if you reboot everything should be back to normal.

If you have a problem with a computer you need a systematic step-by-step approach. Often the problem is caused by a driver, so if you want help we have to know which network interface is used in your computer. And the BT-Hub is outside your computer, we need to know what is inside your computer to support the network.

---

### Post by andreaborman on 2011-05-11
Well according to what it says in Windows device manager my 2 network drivers are- Broadcom 4313 802 11b/g/n  and Realtek pc IE FE family controller. And my wired broadband is connected by ethnet cable.

And you know when I boot into Ubuntu and select Ununtu generic recovery mode. There are several options-resume normal boot
try to free disk space and several over options and the very last option is to drop shell networking with root prompt. And when I selected that. It started giving various readings on the screen,that looked like terminal commands. But I turned off my computer and rebooted before it finished. Because it was just doing that for about 20 minutes. And I got fed up sitting at my computer,with just  text or readings pouring down my computer screen.I did that when I had the Linux Mint 11 RC Katya 3 days ago before I installed Ubuntu. And I think it is because I accidently selected the last option-shell networking with root prompt. That could have messed it up.

And since that time as well as ubuntu I tried Linux Mint on my second Windows 7 Netbook. And the same problem happens,I cannot connect to the Internet on that either. So my so I cannot connect to the Internet on any brand of Linux.Not wired or wireless broadband. But I can connect to the Internet on Windows.

I just don't understand why I now have this problem on Linux or what is causing it. It seems that my network or Internet connection, is messed up on Linux but not on Windows. Andrea.

---

### Post by davis.run on 2011-05-11
So i've been watching all of these different posts trying to figure it out for myself... i lose.  Everyone seems to be asking for the "lspci" copy/paste and then they get it figured out. As the originator of this thread seemed to figure it out. Instead of making another one. I'll just add it here.  I'm having same issue with connecting fine in windows... have to have ethernet cord for ubuntu 11.04 worked fine on 10.10. I'm on a inspiron E1505 and my results for lspci was:

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express PCI Express Root Port (rev 03)
00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 01)
00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 01)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility X1400
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
03:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
03:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01


anyhelp would be appreciated over pm or just this id even go chat. i just don't like have any idea on what to do at this point...

---

### Post by andreaborman on 2011-05-11
> **davis.run said:**
> So i've been watching all of these different posts trying to figure it out for myself... i lose.  Everyone seems to be asking for the "lspci" copy/paste and then they get it figured out. As the originator of this thread seemed to figure it out. Instead of making another one. I'll just add it here.  I'm having same issue with connecting fine in windows... have to have ethernet cord for ubuntu 11.04 worked fine on 10.10. 

Well at least you can connect to the Internet on Ubuntu on wired broadband-ethernet cable. I cannot even connect to the Internet on wired broadband on Ubuntu or as I explained on my other Windows 7 Netbook with the Linux Mint on it.I cannot connect to the Internet at all on Linux.

Could it be that when I was in Ubuntu generic recovery mode and selected root with shell networking. That by mistake the settings changed  and only some one with a Root account can connect to the Internet on Linux? Root is the administrator on Linux and my Ubuntu account is, I think, Sudo which is users. Is that right? Could I have accidently changed the settings so that only some one with a Root account can connect to the Internet?

I have again uninstalled Ubuntu and reinstalled it again. The same way as before. And I still have got the same problem. I don't understand this one either. 

As I thought that if Ubuntu is uninstalled and re installed again. If I did accidently mess up the operating system last time in the previous install. That if Ubuntu was reinstalled again. Then the previous settings also get deleted.And that the Internet problem would be resolved in the new installation.

But no. I still have the same problem in Ubuntu as before.And I have no idea how to fix it. Andrea.

---

### Post by vwebster on 2011-05-12
Hi there. I am having the exact same problem. 
 
1. Today I downloaded the 10.04 ISO binary. 
 
2. Burned it onto a CD successfully.
 
3. On my Dell Inspiron laptop I booted off the CD and choose the option to try it, rather than install it.
 
4. Seemed to come up okay. Was able to navigate to my main drive and it read Windows 7 generated jpgs okay. All USB ports were working just fine.
 
4. Tried Firefox and no access. The wireless icon on upper right had a red line through it. I right clicked (think it was right clicked) and all modes of access were checked marked. Left clicking told me wireless and wired connections were not working.
 
5. I entered connection names and as soon as I finished entering the names a bubble message came up near the network icon telling me I just disconnected. This happened with setting up names for wired and wireless connections. Somebody reported the same problem.
 
6. I connected an ethernet cable from the Insipron to my wireless router. No indication of any connection. Put in connection names with all information about names and MAC addresses from the bottom of the routers.
 
7. Went upstairs to a Dell Studio Vista OS. Booted off CD. Exact same results as with Inspiron.
 
8. Went back to the Inspiron and in Windows confirmed that the device drivers for both wireless and ethernet were working and latest, and they were.
 
I will try some of the suggestions here when I have time over the next few days, but just wanted to say I am having the same problem on multiple laptops...maybe I should try the 11.x version.

---

### Post by andreaborman on 2011-05-12
> **vwebster said:**
> Hi there. I am having the exact same problem. 
 
1. Today I downloaded the 10.04 ISO binary. 
 
2. Burned it onto a CD successfully.
 
3. On my Dell Inspiron laptop I booted off the CD and choose the option to try it, rather than install it.
 
4. Seemed to come up okay. Was able to navigate to my main drive and it read Windows 7 generated jpgs okay. All USB ports were working just fine.
 
4. Tried Firefox and no access. The wireless icon on upper right had a red line through it. I right clicked (think it was right clicked) and all modes of access were checked marked. Left clicking told me wireless and wired connections were not working.
 
5. I entered connection names and as soon as I finished entering the names a bubble message came up near the network icon telling me I just disconnected. This happened with setting up names for wired and wireless connections. Somebody reported the same problem.
 
6. I connected an ethernet cable from the Insipron to my wireless router. No indication of any connection. Put in connection names with all information about names and MAC addresses from the bottom of the routers.
 
7. Went upstairs to a Dell Studio Vista OS. Booted off CD. Exact same results as with Inspiron.
 
8. Went back to the Inspiron and in Windows confirmed that the device drivers for both wireless and ethernet were working and latest, and they were.
 
I will try some of the suggestions here when I have time over the next few days, but just wanted to say I am having the same problem on multiple laptops...maybe I should try the 11.x version.

That is exactly the same problem I am having. It is not just on one computer that I cannot connect to the Internet on wired or wireless broadband it is on both Netbooks. As I already explained I have got 1 Netbook with Windows 7 and Ubuntu installed mounted on virtual clone drive.After that Waubi installer finished the installation. And on Ubuntu I cannot connect to the Internet at all. But I can in windows 7.

On the second Netbook I have got Linux Mint installed alongside Windows 7. The Linux Mint is also installed mounted on virtual clone drive.And then Mint 4 Windows installer finished the Installation. And on Linux Mint I cannot connect to the internet either. But I can on Windows 7.

So I do not understand it. As I used Ubuntu and Linux Mint about 2 months ago and then I could connect to the Internet on both. But that was 2 months ago and then I uninstalled both Ubuntu and Linux Mint because I wanted a change. But reinstalled both a few days ago. But this time around,I cannot connect to the Internet on either.So it is not just happening on 1 computer. I have this problem on both computers. But on Windows I can connect to the Internet. But I can't on Linux.

And I have been browsing the Internet,on Windows of course because I cannot get online through either Linux Mint or Ubuntu.(No Internet access on Linux.)And it is not just my Internet service provider that does not support Linux operating systems. A lot of other ISP do not either.I do not know why that is. Andrea.

---

### Post by BertN45 on 2011-05-12
> **davis.run said:**
> So i've been watching all of these different posts trying to figure it out for myself... i lose.  Everyone seems to be asking for the "lspci" copy/paste and then they get it figured out. As the originator of this thread seemed to figure it out. Instead of making another one. I'll just add it here.  I'm having same issue with connecting fine in windows... have to have ethernet cord for ubuntu 11.04 worked fine on 10.10. I'm on a inspiron E1505 and my results for lspci was:


0b:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01


anyhelp would be appreciated over pm or just this id even go chat. i just don't like have any idea on what to do at this point...

You do have the BCM4311 wireless.  By default the driver from the company Broadcom will be loaded, this driver however has some problems with some Ethernet drivers and does not work in that type of configuration (often used in Dell laptops). If you use the driver written by the Open Source Community, it will work.

I have the same wifi and you can solve your problem as follows:

If you do not have an Internet connection enable the Ubuntu CD in the  "Other Software" tab in the Settings -> Repository menu of the  Synaptic Package Manager first. That CD contains the driver, but it is preferable to download the Internet version. Don't forget to load the CD or USB memory.

1. De-activate the Broadcom STA driver using "Additional Drivers"
2. Go to the Synaptic Package Manager and type bcm in the filter box and unstall everything related to the bcm... wifi drivers, if there is anything still installed.
3. Type b43 in the filter box and install the firmware-b43-installer and b43-fwcutter. 

That was enough to get my BCM4311 working.

---

### Post by astex on 2011-05-12
If you are using wubi.exe to install, make sure you disable windows firewall during installation.

---

### Post by BertN45 on 2011-05-12
> **andreaborman said:**
> Well according to what it says in Windows device manager my 2 network drivers are- Broadcom 4313 802 11b/g/n  and Realtek pc IE FE family controller. And my wired broadband is connected by Ethernet cable.
.

With bcm4313 the problem is the same but there is no supporting alternative b43 driver, however some claim it works with the firmware-b43-lpphy-installer.

Looking at the Internet it seems that the driver used for Ubuntu 10.10 works. To install it, do as this guy did:

I downloaded the STA driver for Maverick(10.10) here (Use Windows)
:
[http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

AMD64 is for 64 bit computers, i386 is for all the others, but if your Ubuntu version is 32 bits use the i386 version.
After copying try to double click the driver, the Ubuntu Software center will complain about the quality, but probably you can use the button that overrules it, 
If not 
-------------------------
Go into terminal, switch (cd) to the directory where you put the driver, and type:

**sudo gdebi  bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb**

You can copy and paste the command, but you might have to change the i386 part of the long filename bcmwl.....i386.deb, if you have a 64 bit Ubuntu, see the filename you have downloaded.
-----------------------

Then search for the Additional Drivers application and just activate the STA driver.

If it works you have to ensure that this older driver is not overwritten again during an update as follows:
Run synaptic package manager, search for the driver package, select the package and choose menu Package -> lock version

It works according to most owners of the BCM4313

---

### Post by The Cog on 2011-05-12
I can't help with your internet problems other than to say that there is no general compatibility problem between Linux and a BT Home Hub - my mother has a Home Hub and I have used it both wired and wirelessly from several different versions of Ubuntu on 3 different machines. No special action needed. So I have to wonder if you have problems with the drivers for your specific hardware.


> **grahammechanical said:**
> Hi

Please remember that you have installed Ubuntu using wubi. That means that Ubuntu is working just like any other program in the Windows 7 operating system. It is accessing the computer's hardware through the Windows 7 operating system.

Is it possible to switch off networking when you are using Windows 7? Are you doing that? If so, then this will surely prevent Ubuntu from using the ethernet (wired) and wireless adapters in your computer.

I cannot let this go un-corrected. When you launch Linux from WUBI, you are merely using the Windows bootloader to launch Linux. Windows is not involved in this other than provding the bootloader and some disk space. Windows is not running at all when Linux is running, even with a WUBI installation.

---

### Post by andreaborman on 2011-05-12
The Netbook I have,well actually I have 3 Netbooks. And all of them are HP Mini 210 1GB. All Windows 7. But I have been able to connect to the Internet in the past,2 months ago when I was using Linux Mint 9.

What I had to do first was to start off on wired broadband and then activate the wireless drivers. While plugged into wired broadband and then restart the computer. And then after I restarted,the wireless networks were all visible. And I just connected to my one,BT Home Hub.

But my other Netbook already has Linux Mint 9 and this one has Ubuntu. And 2 months ago I connected to the Internet on Linux Mint 9. But I cannot now and I still cannot on Ubuntu either. But other people here in this thread say they have got this problem too. But like me their Internet connection on Windows is fine but  on Linux it is not working.

So maybe it is not our computers, but it could be there is a fault in the Linux severs, or operating systems. That is stopping me and other users from connecting to the Internet, in Linux.

But I am not that experienced in computers,so I don't know. I am just guessing. Andrea.

---

### Post by davis.run on 2011-05-13
well, mine worked thank you! just in time for the bday

---

### Post by andreaborman on 2011-05-13
> **BertN45 said:**
> With bcm4313 the problem is the same but there is no supporting alternative b43 driver, however some claim it works with the firmware-b43-lpphy-installer.

Looking at the Internet it seems that the driver used for Ubuntu 10.10 works. To install it, do as this guy did:

I downloaded the STA driver for Maverick(10.10) here (Use Windows)
:
[http://packages.ubuntu.com/maverick/bcmwl-kernel-source](http://packages.ubuntu.com/maverick/bcmwl-kernel-source)

AMD64 is for 64 bit computers, i386 is for all the others, but if your Ubuntu version is 32 bits use the i386 version.
After copying try to double click the driver, the Ubuntu Software center will complain about the quality, but probably you can use the button that overrules it, 
If not 
-------------------------
Go into terminal, switch (cd) to the directory where you put the driver, and type:

**sudo gdebi  bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu5_i386.deb**

You can copy and paste the command, but you might have to change the i386 part of the long filename bcmwl.....i386.deb, if you have a 64 bit Ubuntu, see the filename you have downloaded.
-----------------------

Then search for the Additional Drivers application and just activate the STA driver.

If it works you have to ensure that this older driver is not overwritten again during an update as follows:
Run synaptic package manager, search for the driver package, select the package and choose menu Package -> lock version

It works according to most owners of the BCM4313

Well BertN45,about that download link you gave me for those drivers-it is a Linux download. So I could not downloaded it on Windows as it was a deb file.I have tried to download it on Windows. Which means you have to be on Linux to download and extract the files. And of course I cannot get onto the Internet in Ubuntu,because the Internet connection is not working on Linux, only on Windows. As you know. So I tried using the command in the terminal you gave me in the above post, and it says no such command or file exists.

So it looks like I am not going to be able to connect to the Internet at all, on Ubuntu or any other brand of Linux. Yes,I uninstalled Ubuntu yet again and tried with Linux Mint. But it is the same problem as it is with Ubuntu. So I have reinstalled Ubuntu again. But I still have the same problem. Nothing has changed.I still cannot connect to the Internet on Ubuntu or any other Linux brand,only on Windows.Andrea.

---

### Post by rkillcrazy on 2011-05-13
> **andreaborman said:**
> 

So it looks like I am not going to be able to connect to the Internet at all, on Ubuntu or any other brand of Linux. Yes,I uninstalled Ubuntu yet again and tried with Linux Mint. But it is the same problem as it is with Ubuntu. So I have reinstalled Ubuntu again. But I still have the same problem. Nothing has changed.I still cannot connect to the Internet on Ubuntu or any other Linux brand,only on Windows.Andrea.

What was the last version of Linux that DID have network access?

---

### Post by andreaborman on 2011-05-13
Thank you for your reply. As I mentioned I used Linux Mint 9 in the past. But that was two months ago, but I have tried that again now, and I cannot connect to the Internet with any brand of Linux any more. I do not know why and I do not know how to solve this problem. I have tried everything that people here in this thread advised me to do. But nothing works. Unless I can some how solve this problem,which I cannot.It looks like I will have to give up. Andrea.

---

### Post by rkillcrazy on 2011-05-13
> **andreaborman said:**
> Thank you for your reply. As I mentioned I used Linux Mint 9 in the past. But that was two months ago, but I have tried that again now, and I cannot connect to the Internet with any brand of Linux any more. I do not know why and I do not know how to solve this problem. I have tried everything that people here in this thread advised me to do. But nothing works. Unless I can some how solve this problem,which I cannot.It looks like I will have to give up. Andrea.

If it was an older version, perhaps you can install it and then follow an upgrade path to get to the newer version.  I used to have to do that with an old craptop and Ubuntu 6.06.  The thought here is that maybe the version of the kernel and/or driver worked and the version on the new installation media does not.  Perhaps you can download all the current (updated) versions during an upgrade.

---

### Post by andreaborman on 2011-05-13
> **rkillcrazy said:**
> If it was an older version, perhaps you can install it and then follow an upgrade path to get to the newer version.  I used to have to do that with an old craptop and Ubuntu 6.06.  The thought here is that maybe the version of the kernel and/or driver worked and the version on the new installation media does not.  Perhaps you can download all the current (updated) versions during an upgrade.

But I have already tried the old version I was using two months ago, that I told you about. It worked then, two months ago I could connect to the Internet, but not now. And I tried the new version of Linux Mint before I reinstalled Ubuntu, But nothing,no Internet connection.

I know I have asked this question before,but could it be because on generic recovery mode. Which is on the bootloader when I select Ubnuntu to boot into. I selected the last recovery option,drop root shell with networking,by mistake. Could that be the cause of my problem? Andrea.

---

### Post by rkillcrazy on 2011-05-13
> **andreaborman said:**
> But I have already tried the old version I was using two months ago, that I told you about. It worked then, two months ago I could connect to the Internet, but not now. And I tried the new version of Linux Mint before I reinstalled Ubuntu, But nothing,no Internet connection.

I know I have asked this question before,but could it be because on generic recovery mode. Which is on the bootloader when I select Ubnuntu to boot into. I selected the last recovery option,drop root shell with networking,by mistake. Could that be the cause of my problem? Andrea.

I'm not familiar with the recovery options.  However, I figured if it's a new install of the OS, things should just work.  If the known-good version doesn't work and the new version doesn't work, then I'd lean towards hardware or some quirky incompatibility being caused but the dual-boot/wubi setup you have.  Have you tried booting to a Live CD to take Windows and its quirks out of the mix?  Like I said before, I've only seen this with hardware issues, weird settings in Windows that do bad things to Linux or some form of corruption.  Just seems odd that known-good stuff stopped working for no apparent reason.

---

### Post by andreaborman on 2011-05-13
> **rkillcrazy said:**
> I'm not familiar with the recovery options.  However, I figured if it's a new install of the OS, things should just work.  If the known-good version doesn't work and the new version doesn't work, then I'd lean towards hardware or some quirky incompatibility being caused but the dual-boot/wubi setup you have.  Have you tried booting to a Live CD to take Windows and its quirks out of the mix?  Like I said before, I've only seen this with hardware issues, weird settings in Windows that do bad things to Linux or some form of corruption.  Just seems odd that known-good stuff stopped working for no apparent reason.
 
I install Ubuntu and all the other brands of Linux that I tried on my Netbook using virtual clone drive. And mounting the ISO file onto it. Waubi installer or the Mint 4 Windows installer finishes the Installation. I even tried restoring my Windows 7 Netbook back to factory condition,the second time this week. In case it is some thing to do with Windows.

But of course it is not Windows, as I have a good Internet connection on there. Also I have a Netbook, so I do not have any CD drive. And I tried installing Linux on my other Netbook and I cannot connect to the Internet. On Linux, on that either, but on Windows there is no problem. It is just on Linux that I cannot connect to the Internet, not even on wired broadband. As you can read in my other posts here on this thread.I just cannot understand it. Andrea.

---

### Post by rkillcrazy on 2011-05-13
> **andreaborman said:**
> I have a Netbook, so I do not have any CD drive.

Do you have a thumb drive?  If so, you may be able to create a bootable thumb drive with the instructions [here]("http://www.ubuntu.com/download/ubuntu/download").  Frankly, I don't recall the last time I installed with an optical drive. :P

---

### Post by andreaborman on 2011-05-13
This is virtual clone drive see here- [http://www.slysoft.com/en/virtual-clonedrive.html](http://www.slysoft.com/en/virtual-clonedrive.html)

Downloaded from the Internet and then the Ubuntu or Linux Mint ISO file is mounted on top of it. But I don't have a CD drive or a thumb drive.

And I also think that even if I did boot from a real CD I will have the same problem. Maybe the Linux servers are corrupted or there is a fault on them. As I am not the only one in this thread who is having problems,connecting to the Internet. Other people have too. Andrea.

---

### Post by BertN45 on 2011-05-13
> **andreaborman said:**
> Well BertN45,about that download link you gave me for those drivers-it is a Linux download. So I could not downloaded it on Windows as it was a deb file.I have tried to download it on Windows. Which means you have to be on Linux to download and extract the files. And of course I cannot get onto the Internet in Ubuntu,because the Internet connection is not working on Linux, only on Windows. As you know. So I tried using the command in the terminal you gave me in the above post, and it says no such command or file exists.
.

Well andreaborman I said download that file using windows. I did not say execute that file in Windows or search for a windows program that can execute that file.

If Internet Explorer prompts you, after you clicked my link, you have to SAVE the file, so you can reboot and use that file in Ubuntu.

Probably it is the best for everybody, if you stick to Windows 7 or else try Open Suse or the older Ubuntu 10.10 , probably they work out of the box, After all Linux Mint is based on Ubuntu and will have the same problems with the Internet drivers.

---

### Post by wildmanne39 on 2011-05-13
> **andreaborman said:**
> But I have already tried the old version I was using two months ago, that I told you about. It worked then, two months ago I could connect to the Internet, but not now. And I tried the new version of Linux Mint before I reinstalled Ubuntu, But nothing,no Internet connection.

I know I have asked this question before,but could it be because on generic recovery mode. Which is on the bootloader when I select Ubnuntu to boot into. I selected the last recovery option,drop root shell with networking,by mistake. Could that be the cause of my problem? Andrea.

Hi I had a problem were when I booted ubuntu my net work cards would be turned off and I would have to turn them on manually. Have check to see if that is happening?

---

### Post by andreaborman on 2011-05-14
Thanks Bert N45 for your reply. And what you said about Linux Mint is right. Linux Mint,YLMF,Jolicloud and some other Linux operating systems are based on Ubuntu. So if Ubuntu won't work because of a fault with the network drivers,then Linux Mint and the others won't either.

Unless I tried a Linux that was not based on Ubuntu. But I think that even Kubuntu and Lubuntu, still have the same source code as Ubuntu has. According to what I read on the web.

I have checked my Windows 7 and I don't have any computer virus on Windows. But could there be a computer virus on Linux,on the network side? I am starting to think that, or is there no such thing as a Linux computer virus? And it only happens on Windows?

I don't know what is causing my problem and other users in this thread,have this problem too. With connecting to the Internet on Linux, but not on Windows.

So could it be a problem with the Linux network server or a Linux virus? I don't know I am just guessing. But it is very strange that I can no longer connect to the Internet on Linux. Not even on wired broadband. Andrea.

---

### Post by jtarin on 2011-05-14
Is this WUBI? Try turning off any firewall you have in Windows.

---

### Post by andreaborman on 2011-05-14
> **jtarin said:**
> Is this WUBI? Try turning off any firewall you have in Windows.
 No Windows firewall is not blocking any of my programs. I have checked that too.Also, when you are booted into Linux,Windows Firewall and any anti-virus you have installed on Windows,play no part on Linux.That is they are only active and working on Windows.

 But when I boot into Ubuntu on my Netbook and on my second Netbook with the Linux Mint 9 on it.Where it says network it twirls round and round, and it does when it is starting to connect.Then I get a message saying,ethnet disconnected you are now offline.

So I click on network icon and try again I have ticked enable both wireless and ethnet connection. It then trys to connect again, then same message-ethnet disconnected you are now offline. So I don't think I even got connected for one second.

But could my problem and other peoples in this thread, who also cannot connect to the Internet. Be because of a Linux virus on the network or server or some thing?

Maybe that is it. There is obviously a fault some where, but it is finding it. And fixing it.

I now think that there is a virus,not on my computer, but on the Linux network servers or some thing. Andrea.

---

### Post by jtarin on 2011-05-14
Post the result of the command in the terminal of the command ```
iconfig
```

---

### Post by andreaborman on 2011-05-14
> **BertN45 said:**
> Well andreaborman I said download that file using windows. I did not say execute that file in Windows or search for a windows program that can execute that file.

If Internet Explorer prompts you, after you clicked my link, you have to SAVE the file, so you can reboot and use that file in Ubuntu.

Probably it is the best for everybody, if you stick to Windows 7 or else try Open Suse or the older Ubuntu 10.10 , probably they work out of the box, After all Linux Mint is based on Ubuntu and will have the same problems with the Internet drivers.

Bert N45 I downloaded that file while I was on Windows and saved it like you said. All downloads are saved in downloads folder on Windows. I then booted into Linux and then tried that terminal command again. But it still did not work.I got the same message as before,no such command or file found. 

On Windows I noticed that there is a setting on both the wired and wireless network adapters to-allow the computer to turn off this device to save power. So I unticked that, so Windows would not do that.

But that did not work either. So I have tried all of the suggestions here, and nothing works.

But could there be a virus on the Linux network servers or Linux servers? It is strange that no matter what I do or try, I just cannot connect to the Internet on Linux. There is a folder on Ubuntu saying Windows network drivers. But when I opened it,it was empty, or it said nothing found.Andrea.

---

### Post by jtarin on 2011-05-14
> **The Cog said:**
> I can't help with your internet problems other than to say that there is no general compatibility problem between Linux and a BT Home Hub - my mother has a Home Hub and I have used it both wired and wirelessly from several different versions of Ubuntu on 3 different machines. No special action needed. So I have to wonder if you have problems with the drivers for your specific hardware.

Odd but only today on another post this very situation with the hub came up.......and it was the hub. [Here's the link to the post]("http://ubuntuforums.org/showthread.php?t=1753156&page=3") where you can find the link to the fix.

---

### Post by andreaborman on 2011-05-14
jtarin-
I have read that post and there is another link in that thread.To another post that says BT which is my ISP has updated their hub. And that is the reason,I and a lot of people cannot connect to the Internet on Linux.

Could that be the cause of the problem? It would explain a lot of things. Andrea.

---

### Post by rkillcrazy on 2011-05-14
> **andreaborman said:**
> jtarin-
I have read that post and there is another link in that thread.To another post that says BT which is my ISP has updated their hub. And that is the reason,I and a lot of people cannot connect to the Internet on Linux.

Could that be the cause of the problem? It would explain a lot of things. Andrea.

An "easy" way to test that would be to take your netbook elsewhere and test it on a line you know is not from the same ISP.  For instance, maybe you have a friend using another ISP and can take it over there and jack into their network.  Maybe you can go to a coffee shop or library and do something similar.

---

### Post by jtarin on 2011-05-14
> **andreaborman said:**
> jtarin-
I have read that post and there is another link in that thread.To another post that says BT which is my ISP has updated their hub. And that is the reason,I and a lot of people cannot connect to the Internet on Linux.

Could that be the cause of the problem? It would explain a lot of things. Andrea.It worked for the OP of that thread. You be the judge.

---

### Post by andreaborman on 2011-05-14
> **jtarin said:**
> It worked for the OP of that thread. You be the judge.
But he also said that when he booted into Windows,which is what I still want to do. The problem comes back again. So it may only be a temporary fix. But why won't BT just correct the fault that they caused by their update. It is not fair that we have to do it all by ourselves, if they caused it.

Fixing problems on Linux when things go wrong is very difficult for me. As I have limited experience. Andrea.

---

### Post by rkillcrazy on 2011-05-14
> **andreaborman said:**
> But he also said that when he booted into Windows,which is what I still want to do. The problem comes back again. So it may only be a temporary fix. But why won't BT just correct the fault that they caused by their update. It is not fair that we have to do it all by ourselves, if they caused it.

Fixing problems on Linux when things go wrong is very difficult for me. As I have limited experience. Andrea.

ISPs and software developers are much alike.  They only "support" a select number of platforms.  Although some users may find it works outside of their supported lists, their support teams can't promise anything they do won't break it in the future.  So, they may have pushed out an update that was tested with the number of platforms they "support" and it may have tested just fine.  As far as they are concerned, their work is done once they accomplish that bit of testing and fulfill their SLA (Service Level Agreement).  To put it plainly, not everything works all the time with everyone or everything.  They know this and will pick a target group to provide support for.

---

### Post by Swagman on 2011-05-14
[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9)

BT HomeHub firmware upgrade b0rked the network connection for Linux... create a static route cures it.. destructions in the link above

---

### Post by jtarin on 2011-05-14
Your not fixing Linux problems your overcoming diiculties of things your not familiar with. You will become more familiar as time goes on.
You need to read a little urther down the page in that link.....you give up too easy.

---

### Post by andreaborman on 2011-05-14
> **Swagman said:**
> [http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/9)

BT HomeHub firmware upgrade b0rked the network connection for Linux... create a static route cures it.. destructions in the link above
 Well,I tried that method above. I clicked on that link and followed the instructions exactly. But it did not work. So it is just hopeless. I am never going to be able to connect to the Internet on Linux.

It looks like Ubuntu and Linux Mint, which is on my other netbook cannot recognise my BT router or Internet connection. From what I read in that thread,it looks like BT did update their router. And that could be the cause of the problem. And as I am with BT on an 18 month contact. I cannot just go and get another ISP. Although that may solve the problem.

Some people have a second ISP as well as BT, but I cannot afford it. As then I will have to pay two Internet service providers,BT and the second Internet service provider. And I cannot afford to do that.

Also I have looked on the web and it is not just BT who do not support Linux operating systems. Many other Internet service providers do not either. In fact I looked at Sky broadband,Talk Talk,and Virgin and some others. And they all say on their websites, that they do not support Linux operating systems. They only support Windows and Mac. Which is stupid, because a lot of people do use Linux now. And also, if we are paying every month for our Internet service,then we are entitled to use what operating system we want to. 

And if it is true that BT have messed up our Internet connection on Linux. Then I am very angry about that, as a lot of other users are,if you read that thread. 

But I do not think that anything is going to get me connected to the Internet on Linux at the moment. I have tried everything. Andrea.

---

### Post by jtarin on 2011-05-15
Let me tell you.....that hub isn't the only game in town.....they just want you to think so.
Here's some interesting reads:
[http://baldric.net/category/linux-and-unix/page/6/](http://baldric.net/category/linux-and-unix/page/6/)
[http://baldric.net/problems-with-bt-total-broadband/](http://baldric.net/problems-with-bt-total-broadband/)
[http://www.btyahoo.com/broadband/adhoc_pages/gplcode.html](http://www.btyahoo.com/broadband/adhoc_pages/gplcode.html)

---

### Post by andreaborman on 2011-05-15
> **jtarin said:**
> Let me tell you.....that hub isn't the only game in town.....they just want you to think so.
Here's some interesting reads:
[http://baldric.net/category/linux-and-unix/page/6/](http://baldric.net/category/linux-and-unix/page/6/)
[http://baldric.net/problems-with-bt-total-broadband/](http://baldric.net/problems-with-bt-total-broadband/)
[http://www.btyahoo.com/broadband/adhoc_pages/gplcode.html](http://www.btyahoo.com/broadband/adhoc_pages/gplcode.html)
 
Yes,I have read all of those posts above,they are dated 2006,so it was a few years ago. But what can I do,my Internet service provider is BT. But even if I did change my Internet service provider, I may still have the same problem. With connecting to the Internet on Linux. It may not be anything to do with, if or not I am with BT, why I am having this problem. Which others in this thread are having too,connecting to the Internet.
 
Normally on Linux,when I have tried different brands,I find that I can connect on wired broadband. But some times it cannot activate or install the broadcom wireless drivers,to connect to wireless broadband. So I have to stay on wired broadband.
 
But now I can't even connect to wired broadband on Linux anymore as it does not even connect. I get mesage ethnet disconneted you are offline. And I try to conect again,by clicking the network icon,same mesage. It does not work. I cannot connect to the Internet not even on wired broadband.
 
And all of the terminal commands I have tried don't work either.
 
But my Internet connection is working fine on Windows, but not on Linux. On Linux it does not work at all. Andrea.

---

### Post by jtarin on 2011-05-15
If you want to connect without changing providers what  you need to understand there are ways to do that. Just because those articles are dated 2006 do you think the ways that you send and receive TCP/IP are so different today? There are many ways to manipulate the stack.

---

### Post by jtarin on 2011-05-15
> But now I can't even connect to wired broadband on Linux anymore as it does not even connect. I get mesage ethnet disconneted you are offline. And I try to conect again,by clicking the network icon,same mesage. It does not work. I cannot connect to the Internet not even on wired broadband.

And all of the terminal commands I have tried don't work either.I connect with broadband ADSL/PPPoE. I do not use Network Manager. You need to learn the relationship between the various parts of your network and try to look under the GUI sometimes. What commands are you issuing that don't work?

---

### Post by andreaborman on 2011-05-15
> **jtarin said:**
> If you want to connect without changing providers what  you need to understand there are ways to do that. Just because those articles are dated 2006 do you think the ways that you send and receive TCP/IP are so different today? There are many ways to manipulate the stack.

But I am just not clever enough to alter the settings on my BT Home Hub. And I am worried that if I did this,I may mess up my Internet connection all together.I looked at the home page of BT Home Hub, and there was an update to my Hub by BT on 8th May 2011.

But that should not stop me connecting to the Internet on Linux or any other operating system. I just don't know how to solve this problem.

But as BT and other Internet service providers said,they do not support the Linux operating system. They only support Windows,even the older versions of Windows and Mac.

What is the reason for that? Andrea.

---

### Post by jtarin on 2011-05-15
I'd find a way without that hub. Do you have a link to the technical specs and maybe some images?

---

### Post by karthik.k.nair on 2011-05-15
i am also new to ubuntu may i snuggest you one solution,instead of installing it through wubi . make a bootable cd of ubuntu. then delete a partition in windows. and boot your computer through ubuntu cd and install it in the new deleted partition. i think this may solve your problem.

---

### Post by Swagman on 2011-05-15
I am on BT internet but I haven't used BT's hubs at all.

Well, that's a bit of a porkie.... I tried one for 5 mins and thought it sucked compared to my netgear.

My history with BT is..

I signed up to BT on the last day of the upgrade to ADSL offer (about 11 years ago) for free installation and modem (Green USB frog). After a while I then purchased a wired Netgear router (wireless was new and expensive back then).

I upgraded to DG834 wireless router.

My brother.. Who coincidently (Mwahahaha) used to work for BT brought round BT's homehub for me to try.. He thought they were as c rap as I did !!

The point is.. I have never had an issue connecting with BT using Netgear routers (or similar) and I have connected some strange beasties to this !! (Even running an entire computer show, beamed from my wireless connection to the local community hall (about 50 machines) [**My show**](http://www.intuitionbase.com/reports/BB3))

Dunno how that will work if I ever upgrade to infinity though. We were just enabled for 21CN t'other day but speed has only increased by a few k's

Maybe you might be better off dumping BT's useless hub and getting a third party router as well ?

---

### Post by andreaborman on 2011-05-15
I have gone back to the BT Home Hub home page. And there is a setting where you can restore your home hub-router back to factory settings. This puts the hub or router back to the way it was when it was first installed in my home. And so I did this.

The result-nothing bad happened,the hub just took me offline for a few minutes to reset itself. And my chosen hub password was reset to the default one on the back of my router. And it then asked me to change it to my own password of my choice. Just like it did when I first set it up.

I am now back online again on Windows, but I do not know if this will solve the problem on Linux. But maybe the reset of the hub to factory settings removed BT's update. 

So will this solve the problem in Linux? Andrea.

---

### Post by andreaborman on 2011-05-16
> **Swagman said:**
> I am on BT internet but I haven't used BT's hubs at all.

Well, that's a bit of a porkie.... I tried one for 5 mins and thought it sucked compared to my netgear.

My history with BT is..

I signed up to BT on the last day of the upgrade to ADSL offer (about 11 years ago) for free installation and modem (Green USB frog). After a while I then purchased a wired Netgear router (wireless was new and expensive back then).

I upgraded to DG834 wireless router.

My brother.. Who coincidently (Mwahahaha) used to work for BT brought round BT's homehub for me to try.. He thought they were as c rap as I did !!

The point is.. I have never had an issue connecting with BT using Netgear routers (or similar) and I have connected some strange beasties to this !! (Even running an entire computer show, beamed from my wireless connection to the local community hall (about 50 machines) [**My show**](http://www.intuitionbase.com/reports/BB3))

Dunno how that will work if I ever upgrade to infinity though. We were just enabled for 21CN t'other day but speed has only increased by a few k's

Maybe you might be better off dumping BT's useless hub and getting a third party router as well ?

Well,I did reset my BT home hub back to factory settings and I did connect to the Internet on both Linux Mint and Ubuntu on wired broadband only. And because I was connected to wired broadband,I was able to activate the wireless drivers.

But my joy was short lived,because after I went back into Windows again. The next time I booted into Linux,the wired broadband stopped working again! On both Ubuntu and Linux Mint,although the wifi networks were now there. But even though I entered my wireless key to connect,it would not connect me. 

So now I am back where I started,with no Internet connection wired or wireless on Linux again.It seems that resetting the hub back to factory settings,is only a temporary solution.

 Because you can connect to the Internet on wired broadband on Linux after you do that. But if you boot back into Windows,when you go back into Linux,you are disconnected from the Internet again.

I don't understand it. Andrea.

---

### Post by Swagman on 2011-05-16
Good-ish News

> 

    BT have acknowledged this:

    PaddyB wrote:

    Hi All,

     

    The latest firmware version (4.7.5.1.83.3.18) included a fix to ensure disconnected devices are released from the Hubs DHCP table.

     

    As our requirements for the hub don’t specifically support multiple IP hosts with the same MAC address, this specific scenario with dual boot set-ups was not tested for this upgrade.  After your reports on the forum we are now working on a solution, thanks for flagging this to us. 

     

    In the meantime we have identified a work around that you can use. The network interface on the Ubuntu operating system needs to be configured to use a fixed IP address. This must be set in the operating system’s network settings and not the Hub’s GUI.

     

    Cheers

     

    Paddy,



[http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/11](http://community.bt.com/t5/BB-Speed-Connection-Issues/BT-HomeHub-firmware-upgrade-broken-network-connectivity-Ubuntu/td-p/176473/page/11)

Ubuntu Power !!

Whether the fix will be quick in arriving is another matter though.

---

### Post by andreaborman on 2011-05-16
swagman-
 So BT have accepted that there is a problem with their home hub and are going to correct the fault themselves? That's good news. And according to your post, they have read this thread here and are going to adapt the hub to work on Linux? If they do, that will be a big help to someone like me. Who does not know how to put right a problem like this on Linux. Thank you for the information. Andrea.

---

### Post by dineshs on 2011-05-18
Did you see post #12 [here]("http://ubuntuforums.org/showthread.php?t=1753698&page=2") ?

---

### Post by jsl90 on 2011-05-20
Hi I had the same problem its to do with updates to the BT Hub you have to change the network settings in ubuntu to get on the internet when i did the fix it worked, i'm pretty new to Linux my self, but now i'm up and running.

I started a thread on this same subject look under Absolute beginner talk "No Internet connection" its marked as solved

---

### Post by raed kandah on 2012-01-19
I have an ubuntu inside windows installed using wubi.exe, the problem is when i run the ubuntu i can't connect to internet but my SSID network is appear when I scan for networks and I have enter the passkey and the encryption type correctly I don't know what wrong why cannot connect to internet???????

---

