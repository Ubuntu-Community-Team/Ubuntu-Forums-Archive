---
title: "Uninstall ubuntu"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by liveinbox on 2009-12-02
would anyone please tell me how to safely and fully remove ubuntu 9.10 from my system.  currently I don't have another operating system on my computer, it's just ubuntu 9.10.  I plan to install windows xp pro thereafter.

much thanks in advance.  (the less computer jargon the better I'll be able to understand, hopefully there is a simple solution)

---

### Post by ramjet_1953 on 2009-12-02
Two ways to do this:

1: Just install Windows.

2: Use a Parted Magic disk to re-format first.

You can download parted magic and burn the iso for free.

Regards,
Roger :D

---

### Post by presence1960 on 2009-12-02
> **liveinbox said:**
> would anyone please tell me how to safely and fully remove ubuntu 9.10 from my system.  currently I don't have another operating system on my computer, it's just ubuntu 9.10.  I plan to install windows xp pro thereafter.

much thanks in advance.  (the less computer jargon the better I'll be able to understand, hopefully there is a simple solution)

How the heck can we tell you anything about a computer without using computer jargon? Unfortunately I haven't figured out how to do that.

---

### Post by liveinbox on 2009-12-02
does anyone know how to safely and fully remove ubuntu 9.10 from my system with ubuntu being the only os on the system.  I will install windows xp pro thereafter.

thank you.

---

### Post by running_rabbit07 on 2009-12-02
> **liveinbox said:**
> does anyone know how to safely and fully remove ubuntu 9.10 from my system with ubuntu being the only os on the system.  I will install windows xp pro thereafter.

thank you.

Sorry to see you leaving.

Put in the LiveCD you used to install Ubuntu and choose the option to boot without making changes. 

Go to System>Administration>Partition Editor and select the option to create a new partition table. This will delete all stored info and then you can create NTFS Partitions for Windows. You may also just delete the partitions one by one if you want, but either way, you will open the door to let MS back in.

Happy computing:)

---

### Post by liveinbox on 2009-12-02
> **ramjet_1953 said:**
> Two ways to do this:

1: Just install Windows.

**2: Use a Parted Magic disk to re-format first.**

You can download parted magic and burn the iso for free.

Regards,
Roger :D

would you be able to go through what this is and how to use it to re-format what it is I'm re-formatting.  thanks.

---

### Post by Dullstar on 2009-12-02
Actually, if you just install windows, it'll reformat for you.  I'd just do that, although I can't see why Windows.  Oh well, it works for some of us.

No windows release will ever suit my needs!

---

### Post by ramjet_1953 on 2009-12-02
Here is the URL for Parted Magic:

[http://partedmagic.com/](http://partedmagic.com/)

All of the documentation is available there.

Regards,
Roger :D

---

### Post by JBAlaska on 2009-12-02
Just do this in a terminal:
```
sudo apt-get install windoze
```

I think that's how ya do it ..

---

### Post by QIII on 2009-12-02
"Just install Windows" is not a good option.  If the disk is formatted as extX, the Windows installer will likely wet its pants and have an apoplectic fit.

The easiest thing to do would be to use the LiveCD you used to install Ubuntu.  With it in the CD drive, start the computer.   Choose the option that says something like "Try Ubuntu without making changes to your computer".  This way the hdd will not be mounted -- which is important when working with partitions.

The end result you want is a disk with a single partition formatted as NTFS.

So...

When Ubuntu is running in a live session, go to Applications | Accessories | Terminal and type 

```
gksudo gparted
```

That will start a graphical partitioning tool for you.

Without getting into too much jargon, I'll have to trust that you can sort out the interface.

You will need to delete all of the current partitions, then create a single new partition over the entire disk, formatted as NTFS.

We will still be here if you get stuck.  I hope that the computer you are reformatting is not the only one you have, so that you can get back here to ask for further guidance if you need it.

---

### Post by kwickcut on 2009-12-02
there is another way to do this that may be easier for you... remove the hard drive from the computer that has ubuntu on it then install it in another computer with windows on it  windows will not see the hard drive but the admin tools will see it....


what you need to do is this


rite click on My Computer and select Manage that will open a window called computer management.

on the left you will see in order from top to bottom


computer management

system tools

storage

iclick on storage if it is not expanded and then click on  disk management then look to the right and you will now see your hard drive with the linux os on it... it will look like small blocks usually 3 of them ..all you need to do is right click each partition and delete the partition until you see one big block once that is done you are good to go


just remember if you have 3 drives in your computer lets say c d and e just make sure you dont remove the partitions on them just the new one hope this helps some

this is a good how to with pics
[http://www.syschat.com/how-partition-format-hard-drives-windows-1827.html](http://www.syschat.com/how-partition-format-hard-drives-windows-1827.html)


kwick

---

### Post by liveinbox on 2009-12-02
> **Dullstar said:**
> Actually, if you just install windows, it'll reformat for you.  I'd just do that, although I can't see [SIZE=3]**why Windows**[/SIZE]**?**.  Oh well, it works for some of us.

No windows release will ever suit my needs!

 one main reason: I can't run autodesk's "Revit Architecture 2009"  I tried with something called wine that allows windows apps to run on linux but kept getting error message related to a "call"

---

### Post by QIII on 2009-12-02
Wine, unfortunately, does not run all Windows programs equally well.  Some not at all.

You could install VirtualBox (in the repos) and run Windows in a virtual machine.

If you give me a moment or two, I'll remember the name of an emulator that might work...


Edit:  This is not free, but...   [http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)

---

### Post by liveinbox on 2009-12-02
thank you.  I will try this.  Main reason for leaving ubuntu is "Revit Architecture 2009" a CAD/BIM software isn't supported by ubuntu.  I used "wine" (a download that will help install windows applications/software) to install it but continued to get error involving "call".

---

### Post by john newbuntu on 2009-12-02
Do you want to give it a try with virtualbox?

---

### Post by liveinbox on 2009-12-02
> **QIII said:**
> Wine, unfortunately, does not run all Windows programs equally well.  Some not at all.

You could install VirtualBox (in the repos) and run Windows in a virtual machine.

If you give me a moment or two, I'll remember the name of an emulator that might work...


Edit:  This is not free, but...   [http://www.codeweavers.com/products/cxlinux/](http://www.codeweavers.com/products/cxlinux/)


If I do decide to use ubuntu again I will consider this software for running revit, thank you.

---

### Post by liveinbox on 2009-12-02
> **john newbuntu said:**
> Do you want to give it a try with virtualbox?


could you provide more info on virtualbox: what it is, how to get it, install, and use it.  now I think I'll consider it then.

---

### Post by running_rabbit07 on 2009-12-02
> **liveinbox said:**
> could you provide more info on virtualbox: what it is, how to get it, install, and use it.  now I think I'll consider it then.

This optiion is only good if you have a clean install disk for Windows. [VirtulBox]("http://www.virtualbox.org/") is free and easy to use, but you have to provide the OS you want it to use.

---

### Post by running_rabbit07 on 2009-12-02
Also, if you don't have more than one gig of RAM, things will slow down while running a virtual machine.

---

### Post by presence1960 on 2009-12-02
> **liveinbox said:**
> does anyone know how to safely and fully remove ubuntu 9.10 from my system with ubuntu being the only os on the system.  I will install windows xp pro thereafter.

thank you.

please do not start duplicate threads on the same topic. You have a thread here also: [http://ubuntuforums.org/showthread.php?p=8426893#post8426893](http://ubuntuforums.org/showthread.php?p=8426893#post8426893)

---

### Post by cariboo on 2009-12-02
Please don't create multiple threads on the same subject. I have merged your two threads.

---

### Post by liveinbox on 2009-12-02
*iclick on storage if it is not expanded and then click on  disk management then look to the right and you will now see your hard drive with the linux os on it... it will look like small blocks usually 3 of them ..all you need to do is right click each partition and delete the partition until you see one big block once that is done you are good to go*



I'm in a bit of trouble here.  I went with your idea but failed to follow through successfully.  and I accidentally deleted the entire partition of my laptop drive after I connected it to my pc via usb 2.0 to ide/sata cable.

there were two partitions I was going to delete and I did leaving fat32 and ntfs.  I was going to delete fat32 after but the region I deleted (linux) read free or something like that.  So I wanted to get rid of it and thought the ntfs would automatically expand to fill in the gap.  

this did not happen and after right clicking on the free region/partition and hiting delete the whole thing was gone and white block like spaces disappeared.

not even what shows up on the left the drive icon and letter shows up (I don't remember what letter it was)

I don't know what to do.  my thinking is that the laptop drive is dead or can't be used.  I hope not.  I didn't even see its name recognized when I opened "my computer"

your help ---or anyone as knowledgeable in computer circles-- would be greatly appreciated here with helping me retrieve or undo, fix what I've done.  thanks.

---

### Post by presence1960 on 2009-12-02
Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and use the link in my signature to download the Boot Info Script to the desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
``` This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by liveinbox on 2009-12-03
thank you.  I managed to somehow find my way through to the device manager where I saw a red x at the hdd that I deleted all partitions from I right clickd on it and enable it, went back to management and partitions were there.  

So thanks to everyone who contributed.  I now have xp up and running but I'm having problems connecting to the internet now.  Shouldn't my laptop recognize connection after it's connected to modem from ethernet.  But anyways that's not ubuntu but if you know, don't hesitate to help out please.  Thanks!

---

### Post by running_rabbit07 on 2009-12-04
> **liveinbox said:**
> thank you.  I managed to somehow find my way through to the device manager where I saw a red x at the hdd that I deleted all partitions from I right clickd on it and enable it, went back to management and partitions were there.  

So thanks to everyone who contributed.  I now have xp up and running but I'm having problems connecting to the internet now.  Shouldn't my laptop recognize connection after it's connected to modem from ethernet.  But anyways that's not ubuntu but if you know, don't hesitate to help out please.  Thanks!

Gotta love having to download drivers.

---

### Post by Old *ix Geek on 2009-12-04
> **jbalaska said:**
> just do this in a terminal:
```
sudo apt-get install windoze
```

i think that's how ya do it ..

+1 :p

---

### Post by liveinbox on 2009-12-05
> **Old *ix Geek said:**
> +1 :p


this didn't seem to work.  the attached show what I see in device manager.  any ideas on what needs to be done and how, please post. thanks.

---

### Post by presence1960 on 2009-12-05
> **liveinbox said:**
> this didn't seem to work.  the attached show what I see in device manager.  any ideas on what needs to be done and how, please post. thanks.

That has nothing to do with intalling/uninstalling Ubuntu. You probably installed windows from a windows installation disk instead of a recovery CD/DVD set or recovery partition. The recovery CD/DVDs or recovery partition would have all the drivers for the hardware that came with your machine from the factory. A windows install disk does not have drivers for every piece of hardware for there is no way of knowing what hardware your machine has. 

You need to install the drivers for all those devices or they will not work.

---

### Post by ibuclaw on 2009-12-05
> **liveinbox said:**
> this didn't seem to work.  the attached show what I see in device manager.  any ideas on what needs to be done and how, please post. thanks.

This isn't a Windows support forum.
As it seems your Ubuntu question has been answered + actioned - we wish you well.

But having a quick look at the image, looks like you don't have the drivers for those devices.
Unless you have the manufacturer CD for those devices, you are going to have to download them from the product website.

Regards
Iain

---

