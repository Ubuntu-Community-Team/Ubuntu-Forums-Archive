---
title: "Network Drives - recomendations please"
date: 2008-03-25
forum: Networking &amp; Wireless
---

### Post by Gina on 2008-03-25
I'm thinking of buying a network drive - connected to my router (or perhaps wireless) - so that I can access stored files such as video and music from any networked computer rather than using drive(s) connected directly to a server computer.  I would like recommendations please.  

I'm using Ubuntu (Hardy and Gutsy) and would like to know if there are any problems getting an NAS drive running.  I would prefer not to have to use Windows to set it up if possible.

The Western Digital My Book World looks interesting but so far I haven't been able to find out much about it.

Any help would be much appreciated.  Thank you.

---

### Post by dstew on 2008-03-25
> would like to know if there are any problems getting an NAS drive runningIf you get a NAS device with a PXE-capable BIOS, you can install Ubuntu on it over the network. I did it with an ancient PowerVault NAS that had no provision for bootable USB, floppy or CD-ROM drives. [Here]("http://ubuntuforums.org/showthread.php?t=690483&highlight=powervault") is the thread.

---

### Post by Gina on 2008-03-26
Thank you - I'll look into that.  But I'm a bit new to this sort of thing - how do I tell is a particular drive has e PXE capable BIOS?

---

### Post by dstew on 2008-03-26
From what I know, network-associated storage devices are not simple disk drives, but are really full-blown computers, with BIOSes and operating systems just like any other computer. They need a pretty robust operating system because they act as file servers, so they need to maintain disk integrity and communicate with the network. The main difference is that NAS appliances have no bells and whistles -- no disk drives other than their main hard drives, no (or basic) graphics for display purposes, no sound. They usually have PXE BIOSes so the operating system can be loaded and upgraded over a network connection. PXE stands for "pre-execution environment", and it means that the BIOS provides basic networking capability and file transfer capability. This allows the NAS appliance to get an IP address by DHCP, and then transfer to its memory a file that contains a program that will bootstrap load an operating system.

You have to look at the system specs for whatever NAS appliance you want to buy to see how it is set up. My guess is that when you turn it on, you can get a BIOS configuration display, like that on any PC. Look at the BIOS boot options, and usually there will be an "Installation Boot", or something like that. That is the PXE option.

That said, it may come with a pre-installed operating system that will work fine with Ubuntu once you configure it. If you are going that route, look for NAS that has a web-based configuration setup, that does not require installation of a program on another computer on the network. I just did the Ubuntu install on my NAS for fun.

---

### Post by Gina on 2008-03-28
Thanks for your input :)  Seems the ones most readily available don't have a PXE BIOS - they need setting up with Windows (or Mac).  I was hoping someone would know of one that could be set up by just logging on (like a router) or from Linux.  I do have XP available on one machine but prefer not to use it.  I guess it's not that big a deal.

---

### Post by dstew on 2008-03-28
> Seems the ones most readily available don't have a PXE BIOS - they need setting up with Windows (or Mac)I bet the WD My Book World has a PXE BIOS, but I can't prove it by looking at the documents on line. Actually, the WD My Book World probably has a linux operating system on it already. (See my post in the other thread about this). According to the WD My Book World User's Manual, the disk is formatted with a Linux format. However, the setup software on it only interfaces with Mac or Windows. Once it is set up, you interact with it over a network using Windows Networking, or Samba. If you were making a NAS, wouldn't you want it to run Linux for stability? So, my guess is that it has a Linux OS on it, but it is hidden from view.

What needs to be done, is to get my hands on one, and hack around a little, and see what is going on inside it.

---

### Post by Gina on 2008-03-30
Thank you for that :)  I've decided to take the plunge and get one.  I've studied the online WD manuals and several reviews and I'm pretty sure it will do what I want.

I'll report on my findings,

---

### Post by Gina on 2008-03-31
Ordered last night from PC World (£150) using "Collect @ Store" and picked up this morning.  Connected it all up and left it to sort itself out.  Then thought I'd try accessing it from Firefox in Ubuntu.  I found a post in another thread suggesting **nmblookup -T "*" **in Terminal so tried that.  Immediately got name and network ID from that and put it in Firefox.  I was in! :)  Entered admin name and password (123456) and I was into the setup screen.  Had a look round, changed the admin password and noted the other settings but didn't change anything - I didn't set up any users - and saw there was already one folder named "PUBLIC" - "that'll do" I thought! :lol:

Then went to Places > Network in Ubuntu and there was the NAS :)  I double-clicked the Public folder to go into it and dragged and dropped a couple of folders from my local hard drive onto it.  The files and folders were then accessible from my other computers on the LAN.

RESULT!!!  And so easy!!  No extra software installed - didn't leave Ubuntu - the supplied CDROM is still in it's sleeve untouched.

**NOTE :- It does NOT need Windows or Mac to set it up or access it.**

Edit :- One thing though - the transfer rate seems a bit low - I estimate I'm getting about 12 Mbps rather than 100.

---

### Post by Gina on 2008-04-08
**Update...**  I can now get 3 or 4 MB/s write speed and 5 or 6 MB/s read speed.  That compares with the 1.4 MB/s I was getting at first - so an improvement.

---

### Post by morgengenuss on 2008-04-09
actually i was thinking of going for a wd mybook world with 500gb (since that is sufficient spacewise and raid is not so important to me).

now i read a lot about speed issues with this nas. my question is: is data-transfer-rate a general issue with all nas-systems or is the wd especially bad?

i'm considering using it as a backup (with rsync) and maybe mediaserver; also ssh from outside would be nice.

oh, and i almost forgot: what about noise production?

---

### Post by addisor on 2008-04-27
Hey Gina, that sounds like the sort of thing I'm trying to achive with Western Digital NetCenter 500GB NAS HDD & Print Server off Ebay!!! Just curious, can you access your NAS from a Windows XP computer (if you so wished)

---

