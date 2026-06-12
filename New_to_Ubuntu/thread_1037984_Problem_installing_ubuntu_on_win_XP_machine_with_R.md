---
title: "Problem installing ubuntu on win XP machine with RAID 1"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by wizardzg on 2009-01-12
Hi all. I have a question. Need help with installation also. I have 4 HDD-s, 2x250 gb in RAID 1 and 2x 500 gb also RAID 1. On my 1. partition on 250gb disks I have Win XP, and on second primary partition on 500 gb wanted to install ubuntu I also made thrid primary partiton for swap on 500 gb. I successfully finished installation but after reboot my computer doesn't display boot manager so it directly boots win XP. I also noticed that when it boots in win xp my Gigabyte RAID manager shows that it found errors on the first RAID arrey that is on my 250 gb disks. I understand that the MBR is on that disk but for some reason ubuntu didn't install its loader. I would thought that the problem is a driver for my RAID controller which is on my motherboard but during installation it read all of my partitions with no problem, and I also managed to partiton second disk and create 2 partitions for my Ubuntu. Why is that???
How to solve this problem. PLS help !

---

### Post by linuxaz on 2009-01-12
wizardzg,
I could be wrong here, but I think the problem is that you are installing it on a raid environment using 'software raid' or BIOS raid.  
Some BIOS raid cards on motherboards are supported, but not all.
You can check the Ubuntu HCL to see if it is or not.

From your post, it seems you went through the installation process with Ubuntu.  I *think that for installing in a raid array, you need to use the CD ISO image with the "alternate installer".

I'm sure somebody will chime in here that can help more than I.

linuxaz

---

### Post by wizardzg on 2009-01-12
Hey thanx Linuxaz. Fast answer :) Yeah I do have RAID controller on my MB so it's not a software RAID. So if what you said is wright then only one thing is strange. How did it manage to find and read all of my partitions and see file systems on them. Still this is all from point of view from a Microsoft teaching :) I'm only starting with linux. Thanx a lot  anyway I'll go and check HCL now.

---

### Post by Nostalos on 2009-01-12
hehe.  Raid on the Mobo does not make it a hardware raid ;)

However more than likely you have the same issue I have with my Nforce4 Raid controller.  It installs properly, however Grub can not automatically recover the Disk Geometry when installing so the install of the MBR failed.

Unless it compeletly errored out your install should be fine, you will just need to manually pass Disk Geometry to Grub manually and add the MBR.   Check the FakeRaid Howto,   skim to the section on onstalling GRUB.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by caljohnsmith on 2009-01-12
In order to get a clearer picture of your setup, how about booting your Live CD, download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

