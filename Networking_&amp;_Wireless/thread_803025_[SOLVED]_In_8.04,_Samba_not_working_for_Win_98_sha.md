---
title: "[SOLVED] In 8.04, Samba not working for Win 98 shares"
date: 2008-05-21
forum: Networking &amp; Wireless
---

### Post by jesrani on 2008-05-21
I have a network of XP/Win98 computer and used a Ubuntu 7.10 computer to backup the shares through Samba. I recently transferred the 7.10 to another computer and upgraded to 8.04. It works but I am having problems in accessing the network.
1) I can see all the XP/98 computers
2) When I click on **XP** computer it does not ask for authentication, only opens blank folder, no shares. If I enter the path of the share in Nautilus then I am asked for authentication and I can browse the share. No problem, but in 7.10 it was easier.
3) **Now the problem**. When I click on **Win 98** computer, I can see the shares all right. But some of the shares are **password protected**. When I click on one such, I get the authentication screen but I am just not able to authenticate. I was able to do this on 7.10 easily. If I click on a folder which is **not password** protected, it mounts the folder. Why does it do this, I only want to open it? In 7.10, it only opened, did not mount.

Can anyone help please, because without resolving this issue, I am stuck up as I have a number of Win98 computer with password protected shares. All was working well in 7.10.

---

### Post by jesrani on 2008-05-22
Just as a followup, I tried the command :
sudo mount -t cifs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,iocharset=utf8
for accessing a password protected share on Windows 98 but I got error 2 = no such file or directory. Tried smbfs option and got error 112 = host is down.
On my Win98 computer I have Windows logon setup with username=user and no password. The share is shared with password=pass with readonly access. From 7.10 Ubuntu I could mount this share with user=user and password=pass, but not able to do this on 8.04.

---

### Post by Peter09 on 2008-05-22
replace netbiosname by the ip address of the machine. CIFS does not resolve names.

PC

---

### Post by dmizer on 2008-05-22
please post the output of:
```
smbtree
```

---

### Post by jesrani on 2008-05-22
> **Peter09 said:**
> replace netbiosname by the ip address of the machine. CIFS does not resolve names.

PC

I have installed winbind and put the wins option in nsswitch.conf file. however i tried with ip address and getting the error no 112 for cifs now and same for smbfs as well.

---

### Post by jesrani on 2008-05-22
> **dmizer said:**
> please post the output of:
```
smbtree
```

Here it is, shows the folders / printers I have shared on Ubuntu box. It is surprisingly showing one of my XP computers, don't know why. FYI, I automount my XP and 98 shares but I have removed the 98 shares after upgrading to 98 as it is giving empty folder.

ASTRO
	\\UBUNTU         		Ubuntu_P4_1.4GHz-512Mb-80Gb
		\\UBUNTU\LaserJet_3030  	LaserJet_3030
		\\UBUNTU\PDF_file_generator	PDF_file_generator
		\\UBUNTU\IPC$           	IPC Service (Ubuntu_P4_1.4GHz-512Mb-80Gb)
		\\UBUNTU\Ketan          	
		\\UBUNTU\Source         	
		\\UBUNTU\Rajkumar       	
		\\UBUNTU\Music          	
		\\UBUNTU\print$         	Printer Drivers
	\\TESTLAB        		CD1.6GHz-500Mb-80Gb-IP8

---

### Post by dmizer on 2008-05-22
the win 98 computers are not showing up in your scan because your ubuntu computer and the win 98 computers are not in the same workgroup.  either updated the 98 computers so they are a part of the ASTRO workgroup (preferable) or update ubuntu so it is in the same workgroup as the win 98 computers.

this is critical if you want to connect to your shares.

---

### Post by jesrani on 2008-05-22
> **dmizer said:**
> the win 98 computers are not showing up in your scan because your ubuntu computer and the win 98 computers are not in the same workgroup.  either updated the 98 computers so they are a part of the ASTRO workgroup (preferable) or update ubuntu so it is in the same workgroup as the win 98 computers.

this is critical if you want to connect to your shares.

All the computers are in the same workgroup called "Astro". I can see the win98 computers when I go to Places -> Network.

---

### Post by Peter09 on 2008-05-22
can you ping the machine by ip address

ping <ip address>

---

### Post by jesrani on 2008-05-22
> **Peter09 said:**
> can you ping the machine by ip address

ping <ip address>

Yes, it pings fine. I am able to see the shares from Network but cant authenticate the password protected shares as I used to be able to do on 7.10. owever XP shares are working and getting authenticated.

---

### Post by dmizer on 2008-05-22
do you have firestarter or some other iptables configuration script installed?

---

### Post by jesrani on 2008-05-22
> **dmizer said:**
> do you have firestarter or some other iptables configuration script installed?

Firestarter is on but under policy, allow service, I have configured Samba (SMB) Port 137-139 445 for everyone. I had done this on 7.10 and it has stayed after upgrade to 8.04.

---

### Post by dmizer on 2008-05-22
i'm 99% sure that your problem is a result of firestarter.

try this:
> to use the names, turn off "Block broadcasts from external network".
this is located in Firestarter under:
Edit --> Preferences --> Firewall --> Advanced Options
found here: [http://forums.fedoraforum.org/showthread.php?t=47624](http://forums.fedoraforum.org/showthread.php?t=47624)

---

### Post by jesrani on 2008-05-23
> **dmizer said:**
> i'm 99% sure that your problem is a result of firestarter.

try this:

found here: [http://forums.fedoraforum.org/showthread.php?t=47624](http://forums.fedoraforum.org/showthread.php?t=47624)

Thanks for the continued support. I have checked this and the option is already unchecked in firestarter, carried over from the 7.10 version after upgrade. Can the reasons be on of the two below:
1) Problem in netword card. I can see the network and browse the net. I can configure the network manually. But when I go to System->Administration->Network Tools and select Eth0 and press configure, it gives "interface device not found". In Sysinfo->Hardware->Network->Subsystem, it shows "Unknown device Intel corporation". Even in Firestarter advanced settings, under network, local network is grayed out/disabled.
2) I read on the net that Samba may be the problem in Hardy and reverting back to old 0.26 version or something can solve authentication problems. I have version 0.28 but dont know how to revert back and will it delete my shares and settings?

Please let me know what you feel, I appreciate the time and help you are giving.

---

### Post by dmizer on 2008-05-23
> **jesrani said:**
> Thanks for the continued support. I have checked this and the option is already unchecked in firestarter, carried over from the 7.10 version after upgrade. Can the reasons be on of the two below:
1) Problem in netword card. I can see the network and browse the net. I can configure the network manually. But when I go to System->Administration->Network Tools and select Eth0 and press configure, it gives "interface device not found". In Sysinfo->Hardware->Network->Subsystem, it shows "Unknown device Intel corporation". [COLOR="Red"]Even in Firestarter advanced settings, under network, local network is grayed out/disabled.[/COLOR]
this (my highlight) is very likely your problem.  try disabling network manager according to these directions:
[https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5](https://help.ubuntu.com/community/WifiDocs/NetworkManager?#head-1de145d05f957ff659f5fdb58974ec3e5864def5)
(it's only necessary to follow the two steps under "Disabling NetworkManager")

this will remove your network configuration icon from the system tray, but your network can still be easily configured by going to system > administration > network

further, if you desire a network monitor in your system tray, you can right click and add one through the panel menu.

> **jesrani said:**
> 2) I read on the net that Samba may be the problem in Hardy and reverting back to old 0.26 version or something can solve authentication problems. I have version 0.28 but dont know how to revert back and will it delete my shares and settings?

samba is causing some problems in hardy, but it is not impossible.  it's just requiring a few more options than before.  i think a lot of people were relying on smbfs, but that's depreciating and may not be as well supported in hardy.  also, mounting shares via nautilus has also caused more problems, but neither of these problems will effect mounting manually via /etc/fstab.

---

### Post by jesrani on 2008-05-23
> **dmizer said:**
> this (my highlight) is very likely your problem.  try disabling network manager according to these directions: 

Ok I have tried this but still the same problem. I noticed something interesting. When I open the network in Nautilus and try to open the Win98 protected share, I get an error, but the unprotected Win98 share mounts. However, using the mount -t cifs command, I am unable to mount either of the shares. I am able to mount XP protected shares using this command though. Now I have also noticed that I am not able to open the mounted unprotected Win98 share. It gives error that "Couldnt display as there is no application for this file type".

---

### Post by dmizer on 2008-05-23
okay ... are you doing something with this computer which requires firestarter?  if not, i highly suggest that you (for testing purposes) completely uninstall it.

---

### Post by jesrani on 2008-05-23
> **dmizer said:**
> okay ... are you doing something with this computer which requires firestarter?  if not, i highly suggest that you (for testing purposes) completely uninstall it.

Did this, completely removed with the configuration files and restarted computer. Same problem. Now Nautilus is not displaying the XP shares also, but is mounting them. However if I mount via command line, I access them. Maybe because of disabling the network manager this problem is occuring. However my basic problem of accessing password protected Win98 shares still remains, and now I am not able to mount the unprotected Win98 shares also from command line. Does Hardy have a dislike for Win98. Should I revert to old Samba? How can I prevent you and myself from going mad?????

---

### Post by jesrani on 2008-05-23
Just wanted to add, are you sure it has nothing to do with the MB or network driver?

---

### Post by jesrani on 2008-05-23
Ok I have something very interesting. I booted from a PCLinuxOS 2007 CD and I am able to browse the network easily as before, all Win98/XP shares. It had Samba 0.25 version and I think that either samba or the network driver is the problem. So what do I do next?

---

### Post by dmizer on 2008-05-23
> **jesrani said:**
> Should I revert to old Samba? How can I prevent you and myself from going mad?????
for mounting win 98, you will need to use smbfs rather than cifs.  i have found many posts which indicate that 98 is too old for cifs.

> **jesrani said:**
> Just wanted to add, are you sure it has nothing to do with the MB or network driver?
i'm quite sure there is no hardware issue or driver issue here.  unless you want to include your win98 machines in this assessment.

please post the exact line from fstab you are currently using to mount the win98 share (complete with all your actual share names).  since this is only a local network share, there is no danger of you exposing any critical information.

---

### Post by jesrani on 2008-05-23
> **dmizer said:**
> for mounting win 98, you will need to use smbfs rather than cifs.  i have found many posts which indicate that 98 is too old for cifs.

I have tried this but doesn't work, I get the same error.

> **dmizer said:**
>  please post the exact line from fstab you are currently using to mount the win98 share (complete with all your actual share names).  since this is only a local network share, there is no danger of you exposing any critical information.

I am not using fstab for mounting. I was automounting the shares through a automount.conf file. I have stopped that for the time being and just using the "sudo mount -t" command.

---

### Post by dmizer on 2008-05-23
try smbfs with something like the following (edit it to match your setup)
```
sudo mount -t smbfs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,fmask=777,dmask=777
```

---

### Post by jesrani on 2008-05-23
> **dmizer said:**
> try smbfs with something like the following (edit it to match your setup)
```
sudo mount -t smbfs //netbiosname/sharename /media/sharename -o username=winusername,password=winpassword,fmask=777,dmask=777
```

Didn't work. I uninstalled and reinstalled samba, but same problem. I am beginning to think it is a samba problem with Hardy but I don't know how to install old version

---

### Post by jesrani on 2008-05-24
Are there any more suggestions. I am stuck in 8.04. At least can anyone tell me how to revert to older version of Samba.

---

### Post by ispyisail on 2008-05-24
Hi

I had a simlar problems

The problem went away when i updated my ubuntu box

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

I'm not 100% sure that fixed the problem because i was playing with other setting at the same time.

webmin is a good program for checking your samba settings

---

### Post by AbdRahim on 2008-05-24
I am having the same problem connecting to shares on another ubuntu 8.04 machine

---

### Post by AbdRahim on 2008-05-24
This appears to be a bug in Nautilus, because I can connect to the netwoirk shares with no problem using Konquerer.

---

### Post by jesrani on 2008-05-25
> **AbdRahim said:**
> This appears to be a bug in Nautilus, because I can connect to the netwoirk shares with no problem using Konquerer.

I installed Konquerer and alo tried. It views the shared folders which are not password protected but doesn;t still open the folders which are password protected.

---

### Post by AbdRahim on 2008-05-25
Ok folks. I have an answer. On the U buntu 8.04 machine sharing the files, open a terminal and type "gksudo nautilus /<your drive to be shared>" (e.g  /media /my drive). A browser will open., Go up one level. Right click the drive and select properties, then permissions. You can now change things in here providing this is a ext3 filesystem. for FAT32, you can allow only the owner to create and delete files. If you have installed samba there will also be a share tab.You may have to log out and back in on the remote machine. Now you can go to the network and log into your shared folder or drive and create and delete files.

Be sure the smbf is installed on the client machines.

Happy file sharing.

Pheww!! Now I can get some sleep.

---

### Post by jesrani on 2008-05-27
I solved the problem finally using help from here:
[http://www.linuxquestions.org/questions/linux-networking-3/samba-unable-to-connect-to-win98-shares-644594/](http://www.linuxquestions.org/questions/linux-networking-3/samba-unable-to-connect-to-win98-shares-644594/)

---

### Post by dmizer on 2008-05-27
i am so glad to hear that you got this working.  i've been looking for a solution for you but i just haven't been able to come up with anything.

please mark this thread as "solved" with the "thread tools", so other people (there are quite a few) know that there is a solution here.

---

### Post by jesrani on 2008-05-28
> **dmizer said:**
> i am so glad to hear that you got this working.  i've been looking for a solution for you but i just haven't been able to come up with anything.

please mark this thread as "solved" with the "thread tools", so other people (there are quite a few) know that there is a solution here.

It took me a lot of time too. I am not too technical and hence I just follow advice and use some logic. But it shows that Linux can be very difficult and frustrating for seemingly simple things. What was working shouldn't stop working. And since most of the computers on the earth are "Windows" based, that support is essential.
I don;t think I or anyone would have switched over to Openoffice if it didn't have MS Office support in the first place. Even once all documents are converted this is required as many people may send MS office documents.

---

### Post by dmizer on 2008-05-28
> **jesrani said:**
> It took me a lot of time too. I am not too technical and hence I just follow advice and use some logic. But it shows that Linux can be very difficult and frustrating for seemingly simple things. What was working shouldn't stop working. And since most of the computers on the earth are "Windows" based, that support is essential.

unfortunately, this problem is not unique to linux.  windows updates have broken plenty of windows applications including file shares.  not too long ago, there was a [windows update](http://support.microsoft.com/kb/927891/) that brought most computers in japan [to their knees](http://grandstreamdreams.blogspot.com/2007/05/microsoft-100-cpu-usage-and-svchostexe.html).

this makes your situation no less frustrating though.

---

