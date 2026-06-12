---
title: "Partition confusion - Windows 7 first, Ubuntu Live CD [Screenshot]"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by Helenarth on 2011-06-14
Hi everybody. Just got a new laptop and it came installed with Windows 7 (clean, the only files I have are this screenshot and PerfectDisk12 for the partitioning). I want to install Ubuntu alongside it, and I want Ubuntu to be the OS my computer boots into automatically. Here's what I've done so far based on reading guides (I shrunk the SYSTEM partition which I'm guessing holds Windows 7 as much as I can, and I shrunk C: some as well but I'm unsure what to do with it really as the guides I saw only had one partition plus a recovery).

[IMG]http://i56.tinypic.com/105b31s.png[/IMG]

Now I don't know what to do as I have unallocated space in two areas (after SYSTEM and after C:). Maybe gparted from the Ubuntu live CD can help somewhat...? Erp. I have no idea really. Help?

---

### Post by wolfen69 on 2011-06-14
Just put in the ubuntu cd and start installation. Choose the 46gb (unallocated) partition for the ubuntu install. Done. 

Then at boot-up, you will be given a choice of which OS to use.

---

### Post by Helenarth on 2011-06-14
Thank you. I'll try in a while and say what happened here afterwards. So happy to escape Windows >_>

---

### Post by mike555 on 2011-06-14
You can only have four main partitions , so shrinking the first partition do no good, but no harm....... 
 if you had made the 46 GB partition an extended partition then you could have had a swap partition inside it, but again no problem , Linux works with a swap file instead.
 you should be fine........

---

### Post by coffeecat on 2011-06-14
One point about your partition 1, the "System" partition. That is your Windows boot partition - not the actual Windows system - and which also contains some recovery utilities. It should be 100MB, which looks as though that is what is was before you shrunk it to 84MB. You've released all of 16MB which you can't use anyway. I really don't know if Windows need that 16MB elbow room, but If that was my system I would use the Windows Disk Management utility to expand it back to 100MB again, and then leave it well alone.

---

### Post by nzjethro on 2011-06-14
Maybe too late for this install, but in future I would recommend making the Ubuntu partition an extended partition with logical drives, rather than a primary partition. This is because you can have a maximum of four primary partition, meaning that down the track if you want to try a new distro, or even test a new Ubuntu, you don't have to muck around with moving partitions.

---

### Post by Mark Phelps on 2011-06-15
If you force an installation that creates another Primary partition, don't be surprised if this hoses up your Win7 setup.  Why? Because Win7 has a nasty habit of automatically converting Basic Volumes to Dynamic Disks -- when it detects more than 4 primary partitions on a drive.

BEFORE you do anything else, if you want to have a hope of continuing to use Win7 after the Ubuntu install, go to the Win7 backup feature and use it to create and burn a Win7 Repair CD.  That will allow you to repair the Win7 boot loader -- should it become damaged.

And if you DO want to install Ubuntu into its own partition, you MUST get the total number of Primary partitions (including any Ubuntu partitions) down to a maximum of four.

---

### Post by Helenarth on 2011-06-16
Erp,  I wish I hadn't rushed into this now. Got a few problems.

Windows 7 won't start. The Windows boot manager comes up and says it failed to start because of a recent hardware or software change. Status 0xc0000225. It told me to use the 'repair your computer' function on the recovery disk which I did,  but it found no errors. 

One of the partitions (the 400gb one ) is unrecognised. No real idea what happened.

Also, I can't figure out how to connect to my wifi. If I go to network connections > wireless > add,  it asks me for a bssid which my router doesn't show, only the ssid, serial, passkey and mac address (which isn't seperated by colons like in the example.)

I have the win7 recovery disk and the 9.10 livecd.

---

### Post by oldfred on 2011-06-16
If you ran the auto repair you have to run it 3 three times as it only fixes one thing at a time. One of those fixes will be reinstalling the windows boot loader to the MBR, so then you have to reinstall grub2's boot loader to the MBR.

It may be better to use the command line repair and run this:

BootRec.exe /FixBoot  #updates PBR partition boot sector

How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Use bootsect.exe to repair XP & older or Vista/7 bootsectors
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Is 9.10 the version of Ubuntu you installed? You should have liveCD or windows repair CD for current version install, just to be able to make repairs.

If you have to reinstall grub2's boot loader:
#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2's bootloader in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
If grub 1.99 with Natty uses boot not root
sudo grub-install --boot-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# If no errors on previous commands reboot into working system and run this:
sudo update-grub

#More info here
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

---

### Post by Helenarth on 2011-06-16
Thanks for your post,  I'll run repair a few more times but I don't really understand the last bit since I don't know much about linux in general yet. 
Yes it was 9.10 I installed.

My main concern is getting the wireless to work as I can deal with not being able to use windows but I do need internet access.

---

### Post by DM was on fire! on 2011-06-16
I am not good at networking. :c But I think from what I'm reading, you can enter your SSID in the same area? I think?
[Wiki](http://en.wikipedia.org/wiki/Service_set_(802.11_network))

It should recognize your network automatically though. :\ When I tried wireless on 9.10 it worked flawlessly.

---

### Post by Helenarth on 2011-06-16
It's weird. When I do vpn connections>configurw vpn>wireess there's nothing there. I have to add the whole thing by hand. And then what, nyway? When I've added it,  would it 
connect automatically? 

When I tried out the livecd on my old pc I could swear there was some kind of wireless manager or something because I never had this trouble. 

Maybe my wireless card isn't compatible or sonething?

---

### Post by DM was on fire! on 2011-06-16
Yes, there is. It appears on your top panel in the notification area.
I have a similar issue when I attempt to use LinuxMint. I have no wireless on it. However I have no issues on Puppy. 

It is very possible your wireless card isn't compatible. Do you have the drivers disk for it?

---

### Post by Helenarth on 2011-06-16
All there is at the top is sound, network connection, bluetooth and evolution mail. 

Nope, I don't,  the only cds I have are the 9.10livecd and the 7 recovery disk. I don't even know what the card is,  is there a way to find out? 

Welp. If all else fails, will using the recovery disk to reinstall win 7 allow me to just have windows and get rid of ubuntu? I hate to do it but I need internet for school research and stuff.

---

### Post by DM was on fire! on 2011-06-16
It most likely will. It will overwrite all of your current information, so if you can go into your files and back everything up if you haven't done such already.

In regards to the drivers...they'll be somewhere in your system, but where I don't know. What kind of card is it? Or does it not say (on the card itself)?

---

### Post by Helenarth on 2011-06-16
I'm not sure,  I looked it up and apparently lspci identifies stuff, the ones which look relevant are: 
Ethernet controller: Marvell Technology Group ltd. 88E8040 PCI-E Fast Ethernet Controller
Network Controller: Broadcom Corporation Device 4727 (rev 01)

---

### Post by DM was on fire! on 2011-06-16
A quick Googling of the latter you posted (the former is for computer to modem wired connections) gave me [this](http://ubuntuforums.org/showthread.php?t=1610415). It might prove a little useful. :33

---

### Post by Helenarth on 2011-06-16
I tried, but when I did the sudo apt etc.  bit it said it was already the newest version.

---

### Post by DM was on fire! on 2011-06-16
Damn. :c I'm afraid that's all the help I can offer. 
If I knew where the drivers were, you could navigate to them and install via Ndiswrapper. 
Someone with more knowledge of Windows drivers and stuff may have to come in with that. :c

pls herena i wish i could halp mroe

---

### Post by Helenarth on 2011-06-16
It's ok DMie :3 Made a thread in the networks board, hopefully someone will figur something?

---

