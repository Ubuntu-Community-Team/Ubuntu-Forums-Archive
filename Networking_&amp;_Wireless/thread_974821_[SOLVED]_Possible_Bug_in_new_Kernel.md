---
title: "[SOLVED] Possible Bug in new Kernel?"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by Kellemora on 2008-11-07
Hi Gang

Didn't want to post this in the Beginners section.

But I think we have a problem!

The new Kernel 2.6.24-21 generic downloaded onto this computer first.  Then the network dropped out.  Thank goodness its Friday!

I figured OK, no problem, I'll just reboot and double check that the new kernel is in Grub.  Yep, it's there!  Still no network.

SO, I went to the Host computer, downloaded the new kernel and bam, the rest of the network came crashing down.
Rebooted to the new kernel, double checking grub to make sure, figuring having the same kernel on both machines all would be OK.
No such luck!  Now the entire network went down completely.

YES, I can PING each IP, YES, doing smbtree shows ALL the shares, but Places Network is DEAD on all Ubuntu machines.

Rebooted all machines several times, waited the 15 minutes for everything to repopulate, still no luck.

Rolled BACK to kernel 2.6.24-19 generic, rebooted all the machines, network is back up and running fine.
Rebooted back into the new kernel 2.6.24-21 generic and BAM the entire network came down again.
Rolled back and rebooted to the old kernel again, network back again.

So at this point, it looks like the new kernel has a serious bug in it!

Just thought somebody should know about it!

TTUL
Gary

---

### Post by rhcm123 on 2008-11-07
I don't think it's a bug, as im on -21 generic and my network is still fine.
As a matter of fact.. all my machines are!
What's your distro and what's your computer's ethernet card?
(I have a sneaking suspuscion it's a problem with your computer)

---

### Post by Kellemora on 2008-11-08
Hi rhcm

It's almost midnight here and I have all of my computers and the network up and running fine on 19 now.

I'm using version 8.04.1 I think.  The Systems ABOUT UBUNTU is quite LAX in giving any useful system information.  Here is lsb_release -a:
> root@HPpav753nUbuntu:/home/gary# lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.1
Release:	8.04
Codename:	hardy
root@HPpav753nUbuntu:/home/gary# 


I've tried using 21 now at least 6 times with the same problem.

I have 8 computers here that came down on 21, all 8 came up on 19.
Through a little experimenting, I do have 4 that will work on 21, and the 5th can be seen by all the other 4, but it can't see them.
smbtree shows the shares from the 5th computer.  Ping works A-OK.

```
root@HPpav753nUbuntu:/home/gary# smbtree
Password: 
CLASSICHAUS
	\\HPPAV753NUBUNTU		HPpav753nUbuntu server (Samba, Ubuntu)
		\\HPPAV753NUBUNTU\public         	
		\\HPPAV753NUBUNTU\magicolor_2300W	KonicaMinoltaMagicolor2300W
		\\HPPAV753NUBUNTU\PDF            	PDF
		\\HPPAV753NUBUNTU\IPC$           	IPC Service (HPpav753nUbuntu server (Samba, Ubuntu))
		\\HPPAV753NUBUNTU\SharedStuffHPpav	
		\\HPPAV753NUBUNTU\print$         	Printer Drivers
	\\EMACHT4165UBUNTU		eMachT4165Ubuntu server (Samba, Ubuntu)
		\\EMACHT4165UBUNTU\PDF            	PDF
		\\EMACHT4165UBUNTU\IPC$           	IPC Service (eMachT4165Ubuntu server (Samba, Ubuntu))
		\\EMACHT4165UBUNTU\SharedStuffeMach	
		\\EMACHT4165UBUNTU\print$         	Printer Drivers
	\\DEBISCOMPAQ    		Compaq in Debi's Office
		\\DEBISCOMPAQ\Printer        	Quicken PDF Printer
		\\DEBISCOMPAQ\My Pictures    	
		\\DEBISCOMPAQ\EXTRA GAME STUFF	
		\\DEBISCOMPAQ\SharedDocs     	
		\\DEBISCOMPAQ\print$         	Printer Drivers
		\\DEBISCOMPAQ\IPC$           	Remote IPC
	\\CLASSIC        		Gary's Office
		\\CLASSIC\FTCOLOR        	
		\\CLASSIC\PaulPicturesMemorabilia	
		\\CLASSIC\DebiMachineBackup	
		\\CLASSIC\Debis2006CompaqBackup	
		\\CLASSIC\DEBI           	
		\\CLASSIC\E              	
		\\CLASSIC\Debi2009AutoBackup	
		\\CLASSIC\FinalEvents    	
		\\CLASSIC\Printer4       	Canon i250
		\\CLASSIC\Printer3       	Family Tree Maker Printer
		\\CLASSIC\ScannedDocumentsforCopying	
		\\CLASSIC\Shared Video   	
		\\CLASSIC\SheetMusic     	
		\\CLASSIC\Documents      	
		\\CLASSIC\ScannedMusicBooks	
		\\CLASSIC\print$         	Printer Drivers
		\\CLASSIC\IPC$           	Remote IPC
	\\10-E-C-CLASSIC 		Gary's Office II
		\\10-E-C-CLASSIC\Printer        	Microsoft Office Document Image Writer
		\\10-E-C-CLASSIC\C$             	Default share
		\\10-E-C-CLASSIC\Linux          	
		\\10-E-C-CLASSIC\N$             	Default share
		\\10-E-C-CLASSIC\H$             	Default share
		\\10-E-C-CLASSIC\ADMIN$         	Remote Admin
		\\10-E-C-CLASSIC\My Pictures    	
		\\10-E-C-CLASSIC\Printer4       	Canon i250
		\\10-E-C-CLASSIC\Printer3       	Family Tree Maker Printer
		\\10-E-C-CLASSIC\G$             	Default share
		\\10-E-C-CLASSIC\SharedDocs     	
		\\10-E-C-CLASSIC\print$         	Printer Drivers
		\\10-E-C-CLASSIC\D$             	Default share
		\\10-E-C-CLASSIC\IPC$           	Remote IPC
		\\10-E-C-CLASSIC\KONICA         	KONICA MINOLTA magicolor2300W (Copy 2)
root@HPpav753nUbuntu:/home/gary# 



```
I can get you the Ethernet card info tomorrow if you really think that's the problem.
However, if something was working fine on 19, stops working on 21, starts working again on 19, stops on 21, works again on 19.
I don't really think the ethernet cards are the problem here!

This machine I know has a Realtech RTL-8139/8139C/8139c+
using Driver 8139 I think.
I've really only kept track of the video cards, as the ethernet is on-board the motherboard on all of the computers.

I'm from the old skewl, if it ain't broke, don't fix it, hi hi.......

Networking has always been a nightmare in Ubuntu!

I'm hitting the horizontal for tonight!

EDIT:  Good Morning!

Here are the Network Cards normally on-line in the LAN.
Primary file storage computer - eMachT6524XPMCE:
 - Realtech RTL8139/810X Family Fast Ethernet NIC
 - 1394 Net Adapter
Main computer in my office - HPpav753nUbuntu:
 - Realtek RTL-8139/8139C/8139C+
Front Office - DebisCompaq:
 - Nvidia n Force Networking Controller
 - Nvidia Network Bus Enumerator
Client submissions computer C5420 - Classic:
 - SMC EZ card 10/100 PCI (SMC 1211 Series)
Client operations computer eMachT4165Ubuntu:
 - ADMtek NC100 Network Everywhere Fast Ethernet

The other 3 for the machines not normally on-line, except for internet when necessary, work fine on internet with either, I won't bother getting since they are not normally connected, one is in accounting, the other two are used for ancient archived data, eg accounting backups and correspondence from 1995 to 2000 on one and 2001 to 2006 on the other.

TTUL
Gary

---

### Post by Kellemora on 2008-11-08
If anybody cares:

Todays update brought in 7 new files, don't know what they are for, but after they downloaded, I moved back to 21 and managed to get the internet up and running just fine again.

Also discovered something interesting!  The reason changes made in smb.conf have little to no effect is because it isn't used by Samba in Gnome!  Gnome (Nautilus) uses the /var/lib/samba directory for it's configuration files, they are Binaries so they cannot be edited with a text editor.

That explains why my really noob comments to reboot 3 times is a charm actually worked for so many to get their network back up and running again.  The network data is apparently refreshed upon a second reboot.

A single reboot just reads the existing files and sets the IP's to what were stored.  Rebooting a second time (within a short time frame) apparently causes it to check the connections.  And a third reboot (within a short time frame) causes the binary configuration file to be overwritten with the new updated data.

So, if you can run smbtree and see all your shares, BUT Places Network don't show them, it sure don't hurt to try the triple reboot to get that binary file rewritten.

I've tried this method now about 20 different times when we had problems, and so far, it has worked every time.  NOW I think I know why!  That binary configuration file NOBODY TOLD US ABOUT!!!!!

TTUL
Gary

---

