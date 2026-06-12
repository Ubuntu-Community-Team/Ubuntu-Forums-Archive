---
title: "Running XP as guest in Virtualbox, sharing folders?"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by jotto! on 2009-11-12
Ok am slowly getting in to this.
Am running 9.10 with virtualbox running xp as a guest. 
I have installed guest additions on the guest and now am having problems with the following code. Probably very basic for you guys but still new to me.

mkdir ~/VirtualBoxShare
VBoxManage sharedfolder add "XP" -name "share" -hostpath /home/your/shared/folder/VirtualBoxShare/I get the first line, and that works but I get an error on the second line.
Lets say I have a folder called Shared in my home folder and I want to make that shared between the guest and host, what would I need to put in for that?

If I want to share a folder named 'shared' that is on my 2nd HDD, which appears to be called 2058B12558B0FA9C, what should I type then?

Is it possible to give my guest XP installation full access to my 2nd hard drive?

And finally, is it possible for my guest XP to have USB support or is that just available in the non free versions?

Sorry for all the questions!

---

### Post by Merk42 on 2009-11-12
I set up shared via the GUI
So open up Virtualbox, but don't run the XP Machine
Go to Settings, then the last one Shared Folders.
Navigate the the folder you want and type in a name.
Start the VM, I don't have XP currently, but I believe it shows up under network places.
If not you can type in the address bar of Windows Explorer \\vboxsvr\VirtualBoxShare (assuming VirtualBoxShare is the name you typed in for the settings)

I haven't tried an entire drive, though I don't see why you couldn't navigate to it the same way.  You may want to use Ubuntu's disk utility to give it a name.

You can't use USB in the OSE version, only the PUEL version

---

### Post by blur xc on 2009-11-12
For shared folders, I've always just followed the instructions in the VBox manual.  It's pretty well laid out, and never had a problem, except that you can't have any spaces in the path of the shared folder.

As far a USB devices go, you need the PUEL version.   I read there's some complicated work-a-round to get usb access in the OSE version, but I can't see any reason to do that when the PUEL version is free (as in beer).  But even w/ the OSE verion, to access on USB mass storage device, I don't see why you can't make /media/disk a shared path and be able to transfer files that way.

BM

---

### Post by jotto! on 2009-11-12
Thanks! 
Thats where I was going wrong, I assumed the drive would just show in my computer...didnt realise it would be in my network places!

Went to my network, added the drive and hey presto, full drive available!

If I keep my virtual drive file, can I simply uninstall the OSe version, install the PUEL and then import my existing virtual drive?

---

### Post by blur xc on 2009-11-12
You don't have to do anything.  Just uninstall he OSE version, but DO NOT do a complete uninstall.  When you install the PEUL version (PUEL?), it will find the config files in your home directory and everything will be as it was in the OSE version.  Works real nice...  even in windows.

It just takes a matter of minutes to make the switch.  Also, I've noticed it's more stable to uninstall/reinstall when upgrading your VBox version, but I have not yet added the VBox repos to my sources.  I'm lazy, but that should make it a lot more convenient.

BM

---

### Post by jotto! on 2009-11-12
PUEL, Personal Use and Evaluation License...
Thanks for the help. Will try this version and see what happens. ;)

---

