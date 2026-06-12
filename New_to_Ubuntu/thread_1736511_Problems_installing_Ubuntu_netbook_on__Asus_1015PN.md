---
title: "Problems installing Ubuntu netbook on  Asus 1015PN"
date: 2011-04-22
forum: New to Ubuntu
---

### Post by HomusPensantis on 2011-04-22
[COLOR=black][FONT=Verdana]Hello,[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I am trying to install Ubuntu Netbook 10.10 on an Asus EeePc 1015PN. I have seen that this has been done sucessfully by other people, but I am now stuck.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]My goal is to have a dual boot windows 7 starter and Ubuntu. Windows is alreay installed.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Following the instructions in [_[COLOR=#0000ff]http://www.ubuntu.com/netbook/get-ubuntu/download[/COLOR]_]("http://www.ubuntu.com/netbook/get-ubuntu/download") [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I created an installation USB. I am able to run the trial version from the drive with about 80% functionality.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]For the dual boot installation I read a number of guides on this site such as the one in[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]https://help.ubuntu.com/community/DualBoot/WindowsFirst#Resizing Partitions Using the Ubuntu Installer [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]and external ones such as [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][_[COLOR=#0000ff]http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/[/COLOR]_]("http://www.hackourlife.com/dual-boot-windows-7-and-ubuntu-10-10-maverick-meerkat/") [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]The first issue that I encountered was that automatic partition option ("install alongside other operating systems") was not available as an option. So I had to go through the manual partition route.[/FONT][/COLOR]
[COLOR=black][FONT=Verdana] [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]The second problem was that the Gparted Partition Editor crashed. I had to shrink a partition using Windows Tools that left about 16GB of free space for Ubuntu[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]NOTE: I was able to get Gparted working later on when I created an installation disk on an 8GB USB drive with 4 GB of Persistence Space and then ran an Ubuntu Update [/FONT][/COLOR]
 
The final problem that has me stuck is that the free space that I allocated for Ubuntu is listed as unusable in the table that appears in the "Allocate drive space" window during the installation process and I cannot create the Ubuntu partition or the swap partition. The interesting part is that the area is listed as free space in the color coded bar in the same window...
 
Any help would be greatly appreciated.

---

### Post by madjr on 2011-04-22
hm, you mind attaching a screenshot of gparted showing the free space, maybe we can figure what is happening.

you can take a screen by pressing the PrtSc key

---

### Post by Blasphemist on 2011-04-22
This is a good script to download and run to give us information on your configuration. [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

This is a very good tutorial on dual boot configuration. [http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)

From what you've said so far it seems the space you're planning for ubuntu is quite small but the bootinfoscript will tell more.

---

### Post by HomusPensantis on 2011-04-22
madjr,
Thanks for your reply.
 
Since I posted I continued the investigation and I believe that the problem may be associated with the type of partitions that I have... 
Attached are the screen shots from Windows partition manager and from Gparted. I added the Windows one because it identifies the "unknown" partition in Gparted as an EFI partition. I believe it is where Asus stores their Express Gate OS
 
In the file GParted_2 there is an error message that appeared when I tried to partition the unallocated space with Gparted
 
Once again, thanks.

---

### Post by HomusPensantis on 2011-04-22
Blasphemist,
Thanks for reply.
However, it seems that you have not read my post carefully.
1) I have not been able to install ubuntu, so any script to analyze the boot info is irrelevant.
2) The site that you suggested does not have any additional information compared with the sites that I cited.
 
If you have any additional suggestions that align with the additional info that I posted, I would really appreciate it.

---

### Post by Elfy on 2011-04-22
The bootinfo script tells us more than just what boot you might have after an ubuntu install.

A quick look suggests that you'll need to remove one primary partition in order to create an extended which can nclude many logicals

What's on sda4? Please run the script - it might tell more about this one.

---

### Post by Blasphemist on 2011-04-22
The error message does tell you the issue. The install can't create an extended partition from the free space because you have the maximum primary partitions now. I'd also like to know what the red mark on the last partition shown in gparted says. 

The simple solution is to use windows to move everything from your d drive to your c drive, and then delete that partition. Ubuntu can then use that free space and the existing free space to create an extended partition and install on, with more than one logical partition if you desire (for swap, home, etc.).

Are you willing to give that much space to ubuntu? I would.

---

### Post by Blasphemist on 2011-04-22
I just saw you mention of the bootinfoscript. You can run it when booted to the live cd and using try ubuntu.

---

### Post by HomusPensantis on 2011-04-22
Forestpiskie,
Thanks for your reply.
As I mentioned before, the sd4 is an EFI area.
Attached is the results.txt output of boot_info_script

---

### Post by madjr on 2011-04-22
@HomusPensantis

thanks for the screenshots, they are very useful.

seems your case is very common and easy to solve.

is not an error, but a hard drive limitation.

you cant have more than 4 primary partitions.

you will need to make one of them an **extended** partition, that way you can have more sub partitions.

you will need to format one of them, which will become the extended, so you will need to **backup** your stuff somewhere else, create the extended and then create all the sub partitions you want. then place the stuff back.

seems, sda3 (3gb used) or sda4 are good candidates to become extended.

hope that makes sense :)

---

### Post by HomusPensantis on 2011-04-23
Thank you very much for your help.

---

