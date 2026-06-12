---
title: "can i delete or move files from vista with a live linux disk?"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by bradmayne04 on 2010-06-23
Hey this is a weird question.  My mom has a virus on her laptop. she's running vista home basic.  She has norton anti-virus and all that stuff but she can't get rid of two files because they replicate.  she's tried talking to microsoft and they couldn't do anything from a remote connection because if you delete one file the other file actually replicates and vice versa for trying to remove the other file first.  She was told she would have to do a full reinstall of her os.  I was wondering if i could take a live disk like knoppix std and boot from the dvd on her laptop and then either move the files or just remove them.  I know that you can do something similar to crack windows passwords by copying the files to a usb stick and cracking like that from a live disk.  So my question is it possible to use either a linux live disk or a windows vista recovery disk with a C prompt and remove the files?  if so how would i do it?

---

### Post by linuxman94 on 2010-06-23
You can use a live disk to remove the file. If you use a Ubuntu live, just mount the disk then open a terminal and use the rm command.

```
rm /path/to/file
```

---

### Post by ron999 on 2010-06-23
Yes, a Linux LiveCD such as Ubuntu will let you move or delete files from Windows.
If you're not happy with the command line just look in 'Places'.

---

### Post by bodhi.zazen on 2010-06-23
> **linuxman94 said:**
> You can use a live disk to remove the file. If you use a Ubuntu live, just mount the disk then open a terminal and use the rm command.

```
rm /path/to/file
```

That probably will not work, but if it does - w00t =)

To remove the beast you first need to identify it, and you likely need to edit the registry.

Probably just as easy to do within windows as from a live CD.

---

### Post by AgentZ86 on 2010-06-23
Yes linux live, Ubuntu or Slax or whatever should do it.

Also note: that this type of virus may duplicate the file regardless because the duplication may not be occurring from the file itself but from another file that was re-written or changed in windows that is depending on the file your trying to delete.

So even if that file gets deleted it may re-replicate after you boot to windows again anyhow ?

But NO re-installation should be needed for this.

My very earnest reaction is to remove/ uninstall Nortons completely

And install AVAST free virus home edition and register it for FREE 14 months of virus killing. Also it won't bog down the machine like nortons.
I've killed hundreds of viruses and detected them on 1 machine alone where nortons said the system was perfect LOL
Then do a complete scan and delete any viruses that may appear etc.
Then reboot windows.

Then second download Search and Destroy
[http://www.safer-networking.org/en/spybotsd/index.html](http://www.safer-networking.org/en/spybotsd/index.html)

This is the absolute best malware killer around and it's also FREE
It will ask you to update it once installed just follow the instructions.

Then do a scan and I think a selection for archiving the scan etc. 

Once that's done you can remove all those red checkmarked items that show malware etc.
I think it's just a one click to clean or something it's been a while.  

Then you can archive again if you like and restart.

Once it restarts you can turn off the search and destroy if you like or just adjust the setting to your liking.

Anyhow this will kill the program creating the duplication and also the maleware itself.

Then you should be able to delete the item without problem.

And if it still will not delete, but you feel that the malware is gone you can try to delete it with linux boot up again, or even the command prompt on windows if your familiar with dos commands to do so.

I personally used both Avast and Search and Destroy as a PC tech and always worked for me without additional cost to the customer

Anyhow hope this helps

---

### Post by bradmayne04 on 2010-06-23
> **bodhi.zazen said:**
> That probably will not work, but if it does - w00t =)

To remove the beast you first need to identify it, and you likely need to edit the registry.

Probably just as easy to do within windows as from a live CD.


yeah but what is the command to mount the windows partition?  when you say mount the disk are you referring to starting up the live disk? and how do i get to the windows partition from the bash? what are the commands?  I have identified the file(s) there are two of them on my moms computer. in the c:

---

### Post by ron999 on 2010-06-23
> **bradmayne04 said:**
> yeah but what is the command to mount the windows partition?  when you say mount the disk are you referring to starting up the live disk? and how do i get to the windows partition from the bash? what are the commands? 
Forget about all that stuff.
Boot from the LiveCD and look in 'Places'.

---

### Post by bradmayne04 on 2010-06-23
> **ron999 said:**
> Forget about all that stuff.
Boot from the LiveCD and look in 'Places'.

i can't use ubuntu on her computer.  for some reason it will not boot.  I am using backtrack 4 which works on her computer.

---

### Post by alphacrucis2 on 2010-06-23
Some of these viruses can be very difficult to remove from windows. A very useful AV software for a one off clean job is the free version of malwarebytes anti malware

[http://www.malwarebytes.org/](http://www.malwarebytes.org/)

You could download it via ubuntu and store it somewhere on the ntfs partition (Windows C drive) (some viruses actually block windows from accessing antivirus software websites). Then boot windows in [COLOR="Red"]**safe mode**[/COLOR] and try running the mbam installer from wherever you stored it.

---

### Post by bradmayne04 on 2010-06-23
listen guys i know your trying to help.  I'm not asking for anti virus information. i'm asking how to mount vista through the bash shell.  that's all i need.

---

### Post by bradmayne04 on 2010-06-23
ok I mounted the windows partitio

 sudo mkdir -p /media/c
then:

sudo  mount  -t ntfs -o nls=utf8,umask=0222 /dev/hdb1 /media/c

now i cd to /media/c

then i did an ls command

however the files are in green and some are highlighted.  also, some of the files have spaces between them such as the one i need to get into which is System Volume Information
linux doesn't like when there are spaces between names so now I have two questions 1) how do i get into the system volume information and 2) why are some of the files highlighted?  the files i need to delete are in the System Volume Information  so where do i go from here?

---

### Post by bodhi.zazen on 2010-06-23
> **linuxman94 said:**
> You can use a live disk to remove the file. If you use a Ubuntu live, just mount the disk then open a terminal and use the rm command.

```
rm /path/to/file
```

> **bradmayne04 said:**
> ok I mounted the windows partitio

 sudo mkdir -p /media/c
then:

sudo  mount  -t ntfs -o nls=utf8,umask=0222 /dev/hdb1 /media/c

now i cd to /media/c

then i did an ls command

however the files are in green and some are highlighted.  also, some of the files have spaces between them such as the one i need to get into which is System Volume Information
linux doesn't like when there are spaces between names so now I have two questions 1) how do i get into the system volume information and 2) why are some of the files highlighted?  the files i need to delete are in the System Volume Information  so where do i go from here?

Use tab completion

cd System<tab>

or escape the space

cd System\ Volume

or use quotes

cd "System Volume"

Other then that are you now asking for a long post on Linux and NTFS and how to set permissions and colors in Bash and what directories with permissions of 777 look like ?

Honestly, just try deleting the files in question and leave those nuances for later.

I am pessimistic that this will solve your problem and I still think you are going about this the wrong way. 

I again suggest you start by identifying the virus and then use google to find out how to remove it (what makes you think deleting the file from Linux via a live CD is any better then deleting the file from windows ? the virus is smarter then that).

---

### Post by oldfred on 2010-06-23
If you need to use the command line to mount.

HowTo Mount NTFS Partitions Read Write in Ubuntu & Kubuntu
[http://ubuntu.swerdna.org/ubuntfs.html](http://ubuntu.swerdna.org/ubuntfs.html)

You make a directory and then mount your windows partition to that directory or mount point.

Does backtrack use sudo?
to see NTFS partition(s)
sudo fdisk -l
sudo mkdir /windows
If on liveCD may be /media/dev/sda1
mount -t ntfs-3g /dev/sda1 /path_to/mount_point
sudo mount /dev/sda1  /windows

use ls to list files or folders and cd space folder name to change to that folder. You can use tab to finish if first few chars are unique.
ls
cd /windows
cd ..

---

