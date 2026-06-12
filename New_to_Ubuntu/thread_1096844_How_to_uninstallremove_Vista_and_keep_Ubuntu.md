---
title: "How to uninstall/remove Vista and keep Ubuntu?"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by Skol312000 on 2009-03-15
Is there a way I can uninstall Vista and keep all info/setting i left on my Ubuntu side?
I dont need to transfer anything from Vista to Ubuntu
I just need to know how to completely delete/remove/ unistall Vista and everything that came with Vista.

Will such a removal force me to get rid on Ubuntu also?

Thank you so much for your help

---

### Post by Speed Demon on 2009-03-15
Use a partition editor (gparted) to remove the Vista partition and go from there. Not sure if you can make Ubuntu partition bigger tho

---

### Post by rasmus91 on 2009-03-15
> Will such a removal force me to get rid on Ubuntu also?


Nope. Install the Gparted, i think its called. unmount Vista partition, and format to ext3 or what ever desired format.

---

### Post by Berserker v7 on 2009-03-15
Just be careful if vista is on a primary partition and ubuntu is on a partition extended from it... i cant see how that would not harm your ubuntu...

---

### Post by Skol312000 on 2009-03-15
Vista is the main OS, i mean it has access to more memory and stuff, i want to know 2 things

How can i delete Vista completely! 

And how not to delete Ubuntu as i do it, 

And let Ubuntu take over the whole laptop

If i ever need to... How do i delete Ubuntu? (completely wipe it)?

---

### Post by Berserker v7 on 2009-03-15
if ubuntu is installed on a primary partition then everything is fine, otherwise i beleive removing vista will remove ubuntu also... to be on the safe side, backup all data you have on ubuntu...

to remove vista partition, use GParted... comes with the live cd and very easy to use...

remove ubuntu?? well thats pretty much easy, assuming that you installed vista first... just open local disk management from vista and reformat the ubuntu partitions as ntfs or fat... then on next boot, use your vista cd and fix the master boot record(mbr)... the process is self explanatory, i beleive... never been unfortunate enough to have to do that :)

---

### Post by Berserker v7 on 2009-03-15
If ubuntu is installed on a primary partition then everything is fine, otherwise i beleive removing vista will remove ubuntu also... to be on the safe side, backup all data you have on ubuntu...

to remove vista partition, use GParted... comes with the live cd and is very easy to use...

remove ubuntu?? well thats pretty much easy, assuming that you installed vista first... just open local disk management from vista and reformat the ubuntu partitions as ntfs or fat... then on next boot, use your vista cd and fix the master boot record(mbr)... the process is self explanatory, i beleive... never been unfortunate enough to have to do that :)

---

### Post by Skol312000 on 2009-03-15
Thats a little too technical for me , yes i did havw vista before Ubuntu and i put in a cd and fully installed it, all i want is to start from the scrap.

I want to turn on computer and neither Vista or Ubuntu pops up, and then i want to insert the Live Cd of Ubuntu and install it as thr one and only OS to run my laptop... I really wish for easy steps,

---

### Post by Skol312000 on 2009-03-15
I dont know what a primary partition is or anything, when i installed Ubuntu on Vista for first time i allowed it to have access to memory but below half of my laptops capacity, i now, want to run just Ubuntu, but i want to delete thrm both  and then install Ubuntu as the primary OS.   This is a big deal for me and i really wish i could do this...

---

### Post by theozzlives on 2009-03-15
> **Berserker v7 said:**
> if ubuntu is installed on a primary partition then everything is fine, otherwise i beleive removing vista will remove ubuntu also... to be on the safe side, backup all data you have on ubuntu...

to remove vista partition, use GParted... comes with the live cd and very easy to use...

remove ubuntu?? well thats pretty much easy, assuming that you installed vista first... just open local disk management from vista and reformat the ubuntu partitions as ntfs or fat... then on next boot, use your vista cd and fix the master boot record(mbr)... the process is self explanatory, i beleive... never been unfortunate enough to have to do that :)

If Vista is your primary partition just set the boot flag on your root (/).

---

### Post by lisati on 2009-03-15
> **Skol312000 said:**
> I dont know what a primary partition is or anything, when i installed Ubuntu on Vista for first time i allowed it to have access to memory but below half of my laptops capacity, i now, want to run just Ubuntu, but i want to delete thrm both  and then install Ubuntu as the primary OS.   This is a big deal for me and i really wish i could do this...

A quick translations for you: Many hard disks are organized into "partitions". If your disk drive was a filing cabinet the partitions would be the drawers, one with Vista, one with Ubuntu, and any others that might be present. A "primary partition" is a bit like the first drawer you'd go to on your filing cabinet. 

One of the tools within Ubuntu that lets you organize the drawers (partitions) is called "gparted".

Hope this helps.

By the way, one thing to be aware of is something called a "recovery partition", which some people prefer not to mess around with.

---

### Post by KayakJim on 2009-03-15
Another option that you have available is to backup your important items (e.g. music, pictures, documents, etc).

Then insert the Ubuntu LiveCD and boot from it and when asked about the hard drive select to use the entire disk.

This will wipe everything out (both your current Windows and Ubuntu) and start fresh. After the install, do an update to get the system current, restore your backup, and then install any programs you want.

---

### Post by Berserker v7 on 2009-03-15
> **Skol312000 said:**
> allowed it to have access to memory but below half of my laptops capacity

By memory you mean RAM right? in that case, does this mean you have installed Ubuntu on VMWare or some other virtualization software?? Please clarify on what you meanby "half of my laptops capacity"...

By the way, regarding primary and extended partitions, a system can have at most 4 primary partitions only. extended partitions are used to make many(i dont know the limit, if any) more partitions(called logical partitions) for ease of use, etc., etc... so, basically they are all but the same from an user perspective... sorry for all the confusion caused, its a darned habit i have been trying to put off... my apologies :)

---

### Post by Skol312000 on 2009-03-15
Awesome i really lole that, thats the answer ive been looking for,

Now, can someone comfirm this as accuratw info please?  


What if i go in Vista and choose to delete it... I suppose that will delete Ubuntu also right?

And then i can stick in the live CD and be fine, right?

How do i delete Vista from Vista... Start menu....

---

### Post by lisati on 2009-03-15
It might be difficult (impossible?) to delete Vista from within Vista, which is why it would be helpful to know if you installed Ubuntu "within" Vista or on a separate partition.

KayakJim suggested a good way to proceed: 
[LIST=1]
[*]Make a backup of important data
[*]Boot from the "Live CD"
[*]Install Ubuntu, telling it to use the whole disk
[/LIST]
That way will take care of deleting Vista for you automatically (it will also delete whatever copy of Ubuntu you have on your system and replace it with a fresh copy)

---

### Post by Berserker v7 on 2009-03-15
> **lisati said:**
> It might be difficult (impossible?) to delete Vista from within Vista, which is why it would be helpful to know if you installed Ubuntu "within" Vista or on a separate partition.

KayakJim suggested a good way to proceed: 
[LIST=1]
[*]Make a backup of important data
[*]Boot from the "Live CD"
[*]Install Ubuntu, telling it to use the whole disk
[/LIST]
That way will take care of deleting Vista for you automatically (it will also delete whatever copy of Ubuntu you have on your system and replace it with a fresh copy)

Of course, if Ubuntu is installed within Vista, this would be the only option. If not, then it would be better to make a backup and remove vista using live cd... atleast if things do go right you wont have to reinstall all the softwares...

---

### Post by egalvan on 2009-03-15
I was cruising by and read your thread...
I'm a bit confused...

in your first post you stated..

> **Skol312000 said:**
> 
want to run just Ubuntu, but i want to **delete them both**
and then install Ubuntu as the primary OS.


in a later post you stated...
> **keep all info/setting** i left on my Ubuntu side

The first one, erasing the entire drive and starting over,  is easy...

 the second one, saving data and/or settings, can get a bit more difficult.


I use dban (Darik's Boot and Nuke) to totally wipe a drive.

[www.dban.org](www.dban.org)

Download the iso (very small, approx 2meg in size), burn to cd, then boot it and nuke (wipe) your drive.
 (usb-flash-drive option available)
This WILL WIPE YOUR DRIVE, so use with a bit of care.

Other options include running gparted under a LiveCD 
(Ubuntu LiveCD, for example, PartedMagic LiveCD is another).

---

### Post by egalvan on 2009-03-15
Run gparted from within your existing Ubuntu.

take a screen shot

Applications -> Accessories -> Take Screen Shot

post it here.

this will help figure out your install...

---

### Post by Skol312000 on 2009-03-15
Ok i guess ill just do that



Whay i did the first time i put the CD while i. vista and told it to installl, i chose a little partition for Ubuntu to use but Vista has thr biggest. 

I then restarted laptop and a menu apeared and asked me which one to boot, vista or ubuntu... Its a black screen,  thrn i chose ubuntu... Anyways. I guess ill just redo the thing with thr Live Cd... 


So pretty much install Ubuntu again and when it asks for partitions chose it to run the whole drive? Of both ram and hdd?

And after i do that i will never see Vista again?

---

### Post by carml on 2009-03-15
If into the installation process you choose to give all the space to Ubuntu,you'll give only the disk,so you'll format (read delete) also the partition with Vista. The RAM is always untouched,because it's intended only to charge softwares into an OS, the content of the RAM is erased everytime you turn off or reboot the PC, to maintain all data in memory one uses the hard drive.
I hope this clarify your doubts. :)

---

### Post by jimmyhacker on 2009-03-15
Gparted formats a partition without deleting things by that partition and it also recovers information if your partition was corrupt.Try this with Windows Xp installation`s partition.I think you will have 2 free spaces =))

---

### Post by Skol312000 on 2009-03-15
> **egalvan said:**
> I was cruising by and read your thread...
I'm a bit confused...

in your first post you stated..




in a later post you stated...


The first one, erasing the entire drive and starting over,  is easy...

 the second one, saving data and/or settings, can get a bit more difficult.


I use dban (Darik's Boot and Nuke) to totally wipe a drive.

[www.dban.org](www.dban.org)

Download the iso (very small, approx 2meg in size), burn to cd, then boot it and nuke (wipe) your drive.
 (usb-flash-drive option available)
This WILL WIPE YOUR DRIVE, so use with a bit of care.

Other options include running gparted under a LiveCD 
(Ubuntu LiveCD, for example, PartedMagic LiveCD is another).


Teach me the first one.

---

### Post by Skol312000 on 2009-03-15
ThAnks to all that answered, 

I think this is getting too complicated, i want to delete everything, and after my laptop is clean i want to install Ubuntu...
I would really apreciate step by step instruction, i know this takes ur time and patience, i would really be thankfull...

---

### Post by Linux000 on 2009-03-15
Simple,
1. Put in the Live CD
2. When it boots tell it to install
3. Type in the Data
4. When it comes to a screen and a box reads something with Partition comes up and goes away, (after time zone selection, I belive)
5. Select Guided -- Use entire disk
6. Finish Install

WARNING : This will wipe your hard-drive completely, you will never have a way of getting your old data back...ever...period.

Hope it helps

---

### Post by Skol312000 on 2009-03-15
> **Linux000 said:**
> Simple,
1. Put in the Live CD
2. When it boots tell it to install
3. Type in the Data
4. When it comes to a screen and a box reads something with Partition comes up and goes away, (after time zone selection, I belive)
5. Select Guided -- Use entire disk
6. Finish Install

WARNING : This will wipe your hard-drive completely, you will never have a way of getting your old data back...ever...period.

Hope it helps



Thank you, yes it did but!!!

On #3. What do i type? What data?

---

### Post by presence1960 on 2009-03-15
> **Skol312000 said:**
> Thank you, yes it did but!!!

On #3. What do i type? What data?

Pop in the live CD and you will see it asks for time zone, keyboard layout. user name and password. You are making this very simple matter very troublesome. **[COLOR="Red"]Boot from the live CD and follow the prompts. YOU WILL GET WHAT YOU WANT. FOLLOW the outline LINUX000 gave you. JUST DO IT![/COLOR]** Unfortunately we can't do it for you. Take the bull by the horns, this how you will learn.

---

### Post by carml on 2009-03-15
Once you put in the cd and boot you:
1. Choose your language;
2. Set your time zone;
3. Select the kind of keyboard;
4. Now you'll see the partitioning application and you'll choose how much 
space reserve to Ubuntu.
I tried to install into a new virtual machine,but the sequences should be the same on your machine. ;)

---

### Post by Skol312000 on 2009-03-15
Ok guys, thank you fpr your patience and time

---

