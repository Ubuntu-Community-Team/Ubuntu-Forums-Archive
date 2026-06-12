---
title: "can't delete files, nautilus will not run"
date: 2011-01-04
forum: New to Ubuntu
---

### Post by thesnappysneezer on 2011-01-04
I read about doing sudo nautilus and sudo rm -r

sudo rm -r says rm: missing operand

sudo nautilus says could not creat the following required folders: /root/desktop, /root/.nautilus., how do I creat said folder? I am total newb here, and I am trying to delete folders placedin my home folder by accident while using photorec to recover harddrive accidentally formatted. It has given me "low disk space, and made some operations not work in Linux. 

I can start nautilus from the main menu though I do not know how to use it. 

I have gotten that harddrive onto another harddrive and all of the mp3s seem to have retained their tags and photos but only a second of their actual music. As an aside, if this is the case in photorec, would this be the case in other programs as well?

---

### Post by coffeecat on 2011-01-04
First, are the folders created in your home directory owned by root? Is that why you are using sudo? Are you sure you cannot delete them as an ordinary user? 

Next - your rm command is missing an operand - that is you need to tell it which files to work on. Use 'sudo rm -r <name-of-folder>' to delete an unwanted folder and all contents. But when using rm with sudo and the -r option, be very, very, very, very, very, **very** careful. One typo and you could destroy your operating system.

For nautilus, don't try to create those missing folders in /root. Try:

```
gksudo nautilus
```

---

### Post by thesnappysneezer on 2011-01-04
gksudo nautilus does not work, I forgot to type the gk in the post above, I just tried to drop these in the trash and they will not go so I am trying to find a way to get the permission to ditch them, it won't even read a dvd I have in there because it can't mount, too much stuff got crammed in it and it has made the system not work properly. 

that sudo command you gave me to remove, it worked, thank you so much, it will play dvds now and the files are gone but when I start up I still get the message that I first got when this problem occurred though not many of the others, many came up before now I just get this:

The volume "Filesystem root" has only 0 bytes disk remaining. You can free up disk space by removing unused programs or files I am examining but I do not understand why this is coming up or how to view the files in root, no permission, I am guessing that whenever I made my mistake about those recovered files, I must have accidentaly put some in there too, I was up for three days trying to wrap myself around how to solve this problem and get back my stuff plus work, so frustrating. I wish I hadn't of deleted all of my stuff when trying linux, this should be fun not frustrating, well maybe frustratingly fun. It does look lik mypics are ok and much of my mp3s are still there just the last few things I added to my computer seem to be damaged, though I can not be certain photorec created a jungle I have no idea how to sort out.


So long story short, how do I get permission to see the files in root?

---

### Post by coffeecat on 2011-01-04
> **thesnappysneezer said:**
> gksudo nautilus does not work

....

The volume "Filesystem root" has only 0 bytes disk remaining. 

I should imagine the two are related. Nautilus run as root should work. If you are getting a message that your root filesystem is full, then your root filesystem is full. By the way, that message is referring to your root partition, not the root account, nor the /root folder which is the equivalent of root's home folder.

To free up some space I recommend the following as starters. Open a terminal, and:

```
sudo apt-get clean
```That will clear out the cache of downloaded application package files. That should regain a couple of hundred megabytes or so. The next assumes that you did once manage to delete some files with a root nautilus. What happens when you do that is that they are not actually deleted from the hard drive, but moved into root's trash which is not the same place as an ordinary user's trash. This is the command you need:

```
sudo rm /root/.local/share/Trash/*
```If you need to investigate more, here is a useful guide:

[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)

---

### Post by thesnappysneezer on 2011-01-04
urgh, this thing won't mount dvds. I have found more of the files stuffed into File System, the sudo command you gave me before will not work on these files, claiming they are read only. thanks for your help and please help some more.

---

### Post by coffeecat on 2011-01-05
> **thesnappysneezer said:**
> urgh, this thing won't mount dvds.

What do you mean? What has that to do with the original problem?

> **thesnappysneezer said:**
>  I have found more of the files stuffed into File System, the sudo command you gave me before will not work on these files, claiming they are read only.

What files? Don't go trying to delete read-only files unless you know what you are doing. No, I'll re-phrase that. Don't go deleting read-only files. They are there for a purpose.

> **thesnappysneezer said:**
>  thanks for your help and please help some more.

Can you boot into the system? Was the comment about DVDs that you can't boot a live CD? You could use a live USB, but freeing up room with a live session is a little more complex. You need to describe what you are trying to do.

---

### Post by thesnappysneezer on 2011-01-05
I think it is related about the DVDs, it says there is not enough memory to mount. I was just trying to see if a DVD could play on it, it had before.

 The files I want to delete are files I need to delete, these are files "recovered" from the formatted harddrive that I intended to send to another harddrive but by accident I put them in the media folder in filesystem on the same harddrive they were from and it over clogged it. I know these are those files, I see the tags of mp3s, images from the the last webpages I was in on vista, old files that do not work, this is the photorec leftovers, named like it names them. I have recovered what I can recover of these to another harddrive now, I need to get this out to make this a functional system. At least this is what I suspect. I am considering gping down to a 32 bit version of linux and just rewriting the whole disc again, not like there is anything I can recover from windows after seeing what was left o f my mp3s through photorec, that stuff has to be randomly damaged as well and getting this error out of this version seems to be nonfixable unless you have a bettter idea.

---

### Post by coffeecat on 2011-01-05
Putting files in /media was certainly an error. The system folder /media should only be used for creating mountpoints for mountable media such as external drives and internal partitions.

If the files that are clogging the system are in /media, post the names of some of the sub-folders in /media that they are in and I'll give you terminal commands to get rid of them. Are these the files that are read-only? Please be clear in your answer. If they are I'll give you a command to render them writeable and deletable.

---

### Post by thesnappysneezer on 2011-01-05
the files in media are 
recup_dir.1
recup_dir.2
recup_dir.3
recup_dir.4
recup_dir.5
recup_dir.6
recup_dir.7
recup_dir.8
recup_dir.9
recup_dir.10
recup_dir.11
recup_dir.12
recup_dir.13
recup_dir.14
recup_dir.15
recup_dir.16
recup_dir.17
recup_dir.18
recup_dir.19


also there is an empty recup_dir.17 in the File System

---

### Post by thesnappysneezer on 2011-01-05
nevermind, rebooted the system, this is no longer the issue

---

### Post by Sicadastra on 2012-01-28
> **coffeecat said:**
> First, are the folders created in your home directory owned by root? Is that why you are using sudo? Are you sure you cannot delete them as an ordinary user? 

Next - your rm command is missing an operand - that is you need to tell it which files to work on. Use 'sudo rm -r <name-of-folder>' to delete an unwanted folder and all contents. But when using rm with sudo and the -r option, be very, very, very, very, very, **very** careful. One typo and you could destroy your operating system.

For nautilus, don't try to create those missing folders in /root. Try:

```
gksudo nautilus
```

Can I use the sudo rm -r code for multiple folders to delete? I have the same problem as the OP although my recup_dir files are up to 139 folders, and it's a bit tiring deleting them one by one.

---

### Post by mcduck on 2012-01-28
> **Sicadastra said:**
> Can I use the sudo rm -r code for multiple folders to delete? I have the same problem as the OP although my recup_dir files are up to 139 folders, and it's a bit tiring deleting them one by one.

Sure, but be *extremely careful* with rm -r, and *even more careful* when using wildcards with it to remove multiple files or directories. If you make any mistake and end deleting wrong files/directories, getting them back will be very hard if not completely impossible...

So, you have multiple directories inside /media, each one called recup_dir. and then a number in the end? In that case the following command should work:

```
sudo rm -r /media/recup_dir.*
```

---

### Post by Sicadastra on 2012-01-29
Thank you for this. But just to clarify, my code would be:

<sudo rm -r /home/sicadastra/recup_dir.*>

I'm very wary using this too so I apologize for clarifying things up again.


> **mcduck said:**
> Sure, but be *extremely careful* with rm -r, and *even more careful* when using wildcards with it to remove multiple files or directories. If you make any mistake and end deleting wrong files/directories, getting them back will be very hard if not completely impossible...

So, you have multiple directories inside /media, each one called recup_dir. and then a number in the end? In that case the following command should work:

```
sudo rm -r /media/recup_dir.*
```

---

### Post by mcduck on 2012-01-29
> **Sicadastra said:**
> Thank you for this. But just to clarify, my code would be:

<sudo rm -r /home/sicadastra/recup_dir.*>

I'm very wary using this too so I apologize for clarifying things up again.

If the directories you need to delete are in /home/sicadastra, then yes, that would be the correct command.

---

