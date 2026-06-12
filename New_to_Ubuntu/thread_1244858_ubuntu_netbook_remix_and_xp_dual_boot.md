---
title: "ubuntu netbook remix and xp dual boot"
date: 2009-08-19
forum: New to Ubuntu
---

### Post by impatientboi on 2009-08-19
Hi all, bit a newbie. . . or is that n00b? Who knows? Firstly, i apologise for the bold /italics, but i do have a tendency to ramble so needed to highlight the questions. I am using a standard configuration ASUS 1000H, currently with xp installed. 


anyway i have been toying with the idea of trying a linux installation for some time. I recently created a bootable usb of ubuntu, and then of ubuntu netbook remix. i had some troubles getting ubr to boot but eventually got it sorted and am happily using it as i write  this thread. which reminds me of another question: [I]**if i have installed a program through the add/programs function **(in this example amorak), [B]provided there is sufficient space on the usb, will that program remain installed on the usb stick when i reboot using the usb stick? If so, is the program installed as part of the os installation or will i need to reinstall the program.

[/B][/I]Now onto my main questions.

My understanding is that the ubuntu installer includes a partioning utility to partion the hdd so that the os's can be installed independently of each other on the same machine. 

[I]Ideally what i would like to do is have seperate partitions for each operating system, and then a third partition for storage that is used by both operating systems. this scenario is operating under the asssumption that i would, for example, specify in windows that the my documents folders are located on the third partition say g:.
I would the like to do the same under linux, specify that the documents etc are located on the third partition, so that from the UNR desktop launcher, i could click on documents and it would effectively be a shortcut to same folder used as the my documents folder in windows.
I guess in a more succinct way my question is **using ubuntu, (specifically ubr) can i specify which folder opens when i click on the documents button**? i want to avoid having to click through documents and settings, user etc to navigate around my media files when using ubuntu. [/I]
if this isn't possible, the alternate scenario would be for me to install the operating systems in separate partitions (my configuration currently has two almost equal sized partitions) and then use my external hdd as storage for both to make it more accessible, just have the hard drive with my documents, my videos and my pictures etc and navigate through the folder that way.

if any one can make sense of my reasonings above and provide some feedback it would be greatly appreciated.

cheers
Mark

---

### Post by Arla on 2009-08-19
The quick response is yes, the slightly slower response is, since Documents is "just a folder" and you can mount drives and or folders to other folders, you can always mount a different folder into documents.

I've done that on my current PC, now, the problem area (and this one I'm not sure of) is whether it's a GOOD idea to use NTFS for storing Ubuntu documents (or conversly, using EXT3/4 for storing Windows Documents).

I've read that NTFS-3G is much improved and stable now, but I'm not sure what the official word on that is.

---

### Post by Arla on 2009-08-20
An example,

Either use the mount --bind command such as

> 
mount --bind /myData /home/user/Documents


where /myData would be the mount point of the drive and the folder you want to use, alternatively you can put this in /etc/fstab such as

> 
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/sda3       /media/Data     ntfs-3g defaults,locale=en_US.UTF-8 0     0

#Mount the Documents folder
/media/Data/Documents  /home/james/Documents bind defaults,bind   0       0


This (to the best of my understanding) mounts /dev/sda3 (my "documents" drive) as /media/Data directory, and then makes the Documents folder on my drive, mounted to the /home/james/Documents folder, so when I look in /home/james/Documents I actually see what's on /media/Data/Documents, which is really what's on my document partition drive in the Documents folder (make sense?)

---

### Post by impatientboi on 2009-08-20
thanks for that
If anybody could offer me any advice re: is it a bad idea to be using ubuntu docs  in windows and vice versa. 

My main concern is my media files, not so much documents if this makes a difference i just want to be able to access my itunes folder and video and picture folders for example from both operating systems. Ubunutu would then become my main os and xp primarily to manage my iphone, say once a week.

how do i mount a folder or drive to an existing folder or drive. I have tried the windows-centric way of going about things, but clearly this is not windows lol, so i'm a bit stuck as to how i would make a folder accessible directly from the documents folder

---

### Post by warreno on 2009-08-20
If all you need Windows for is managing your iPhone, why not install [VirtualBox]("http://www.virtualbox.org/") under Ubuntu and run XP as necessary in a windowed session, and stick with Ubuntu all the rest of the time?

You'd still basically have your partitions as described before, but only actually boot Windows in a sandbox on an as-needed basis. (Actually I believe VB supports shared folders, so XP wouldn't even know the difference anyway.)

And no, BTW, changes you make to the Live Ubuntu running off your USB thumb drive (installing a program, configuration, etc.) are not preserved; they go away with each reboot.

---

