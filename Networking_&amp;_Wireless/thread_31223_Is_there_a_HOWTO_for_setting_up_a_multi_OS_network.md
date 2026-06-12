---
title: "Is there a HOWTO for setting up a multi OS network?"
date: 2005-05-02
forum: Networking &amp; Wireless
---

### Post by muzza on 2005-05-02
I want to set up a home network.  I have a Netgear DG834 router/modem and 2 PCs and a Mac laptop.

I have installed Ubuntu on the Mac, but there are times when I will want to run some OSX software. Unfortunately, the same goes for some Windoze apps.

So the network will need to potentially be able to communicate and share folders between Linux, Windoze and Macintosh.  (I want to edit DV movies on the Mac, but it's only got 20Gb HD, so I figure I'll store and retrieve the data on the main PC [80Gb + 200Gb HD's]

I've already gathered that I'll have to format a FAT32 partition to share between Win and Lin, but what about the Mac?  Does Linux read/write HFS+?  Does the Mac need to do the FAT32 thing?

The Netgear install CD had info on setting up a Windoze network, but that's no use to me.  

Also, I've got the printer connected to the main PC via parallel cable.  Will the other pooters be able to print to it?

I'll most likely settle on using Kubuntu as my main OS.  (I'm a sucker for eye candy)

All replies in Noob English, please!

---

### Post by Xerampelinae on 2005-05-02
It isn't clear to me if you have a main computer that will always be running ubuntu.  If so, you could create some sort of network share (nfs, etc) that the other machines could have access to to store files on and etc.

---

### Post by sethmahoney on 2005-05-02
I'm not sure if this describes your situation, but if you have three computers, one running Linux, one running Windows, and one running OS X, you don't need to reformat your Windows computer.  NTFS works fine (for me anyway) over the network.  They only time you would have to reformat is if Linux and Windows will be installed on the same computer.

As far as setting up the network goes, there shouldn't be much to it.  Once you get Ubuntu installed, make sure Samba is installed (go to System->Administration->Synaptic Package Manager and search for Samba).  Then set up the folders you want to be shared on your Windows machine.  I'm not sure how it works in Linux or OS X (I haven't had to set up a shared folder on my Ubuntu box yet), but in Windows, just right-click on the folder and click "Sharing" or something like that.  To access that folder in Linux (this part only applies if Windows and Linux are installed on different machines), open up Places->Network Servers and doubleclick on Windows Network, then on whatever your network name is, and then doubleclick on the name of the Windows machine.  The folders you have set up as shared should appear, and you can copy items back and forth that way.  I'd assume working with OS X should be similar.

---

### Post by muzza on 2005-05-02
Sorry, I wasn't clear.

The main computer, the one I'm using now, will (hopefully) mainly run Kubuntu.  But there are times when I will have to run it using Windoze.  (AutoCad and PowerTabs spring to mind.  Wine and Xoffice aren't an option yet.)  The computer doesn't run 24/7, only when I'm using it or when another computer will need to access the printer.

Although I have Ubuntu PPC installed on the Mac, I'll probably continue to use OSX apps - the linux stuff isn't quite there yet.  So I'll want to use the main PC as a storage area for miniDV movies that I will edit on the Mac.  Will this be possible?  (Maybe I should post that question in the UbuntuPPC forum?)

The second PC is my 5yo daughter's, so it will be running PC educational apps (and the occasional Ubuntu game) and it will need to access the printer, which will be connected to the main PC (this one)  There will probably times when that computer will also need access to files on the Mac.

---

### Post by sethmahoney on 2005-05-02
I'm not sure of the technical details of sharing files between Ubuntu and a Mac, but it shouldn't be an issue.  I'm guessing its just a matter of making sure you have a compatible file server (like Samba for Windows - I don't know what the Mac version of it is) and then setting up a shared folder by going to System->Administration->Shared Folders.

One thing to keep in mind: do you know for sure that there are Linux drivers for your printer?  Printer support is, unfortunately, one of the things that Linux is somewhat short on.

---

### Post by muzza on 2005-05-04
I've had the  printer working with Ubuntu.  Haven't tried it with Kubuntu yet.

---

### Post by nascent16 on 2005-05-09
I have used Samba quite successfully to communicate with Mac OS X, Windows, and Ubuntu. Mac OS 9 isn't very compatible with Samba without third party plugins, but hopefully nobody's still running that. Mac OS X and Windows support Samba natively, go to

[http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)

to see how to set up Samba in Ubuntu. It's a fairly straightforward process.

Justin

---

### Post by muzza on 2005-05-15
[QUOTE=nascent16]go to [http://www.ubuntuguide.org/](http://www.ubuntuguide.org/) to see how to set up Samba in Ubuntu. It's a fairly straightforward process.[/QUOTE]


Um... straightforward???  I looked at the guide and don't know where to start.  I think Samba is already installed on my system anyway.

I went into the Kubuntu Control Center and looked at the settings for Samba, but I don't know what any of the jargon means. Is there a _*BEGINNERS*_  guide to samba anywhere?

I also looked at the File Sharing settings but it was greyed out, even in administrator mode.

---

