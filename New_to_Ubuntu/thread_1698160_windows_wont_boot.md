---
title: "windows wont boot"
date: 2011-03-01
forum: New to Ubuntu
---

### Post by TheAJGman on 2011-03-01
i was referred here from my other [post]("http://ubuntuforums.org/showthread.php?t=1696504&highlight=chromium+os")
here is the problem code section
```
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 18233775. But according to the info from 
                       fdisk, sda2 starts at sector 63.
    Operating System:  
    Boot files/dirs:
```
tell me what to do

---

### Post by Rubi1200 on 2011-03-02
What happened to sda1? The boot script results in your other thread only show sda2, sda3, and sda4.

Do you have a Windows installation/repair CD?

---

### Post by TheAJGman on 2011-03-02
Sorry I was at school. Yes I have instalation disks

---

### Post by FoxEWolf on 2011-03-02
hmm... with all the problems windows has been causing i am beginning to suspect thata it not booting up is not an error but a sign that things are working. nah what am i talking about.


Was this a first time boot after ubuntu install or were you able to boot windows after install. that is kind of crucial for my help.

---

### Post by Rubi1200 on 2011-03-02
> **TheAJGman said:**
> Yes I have instalation disks
Okay, that is a start.

But, you did not answer the question about what happened to sda1. This may provide critical information which might affect the solutions offered here.

---

### Post by TheAJGman on 2011-03-02
i dont know what happened to it. i cant and have never booted to windows 7 after i installed ubuntu 10.04. if it helps i can still view and transfer files to and from windows 7 partition.

---

### Post by TheAJGman on 2011-03-03
Bumpety bump bump bump

---

### Post by TheAJGman on 2011-03-04
someone help

---

### Post by Rubi1200 on 2011-03-04
I suggest you do the following:

1. since you can copy files from the Windows side, backup all important data now.

2. run a repair to fix the MBR and restore the ability to boot Windows

3. assuming that works, we can then reinstall GRUB

Windows links:
[http://ubuntuforums.org/showthread.php?p=9826152](http://ubuntuforums.org/showthread.php?p=9826152)

It might be worthwhile starting off with a chkdsk to see what is going on and it may even solve the problem straight away.

---

### Post by TheAJGman on 2011-03-04
ok ill try as soon as im done installing updates

---

### Post by TheAJGman on 2011-03-04
didnt work. aaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaaa!!!!!!!!!!!!!!!!!!!!!!!
](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,) ](*,)

---

### Post by TheAJGman on 2011-03-05
Help meeeeeeeeeee

---

### Post by Rubi1200 on 2011-03-05
I am sorry this is not working well and I understand how frustrating the situation must be for you.

But, and this may sound harsh, you are not helping us very much either.

What did not work? What have you tried?

Please try and be as specific as possible.

We are not sitting there in front of the computer with you, which means you need to tell us what is going on.

Any relevant information such as error messages etc. need to be posted here otherwise it is nigh on impossible to know what is happening at your end.

Thanks.

---

### Post by Quackers on 2011-03-05
Judging from the output of the boot info script in your other post it appears that you do not have any Windows system installed.
As you can see the operating system filed is empty
```
sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  According to the info in the boot sector, sda2 starts 
                       at sector 18233775. But according to the info from 
                       fdisk, sda2 starts at sector 63.
    [COLOR="Red"]Operating System:[/COLOR]  
    Boot files/dirs: [COLOR="Black"]
```[/COLOR]
You say you can mount Windows files?

---

### Post by TheAJGman on 2011-03-05
I can edit all files on windows partition

---

### Post by Quackers on 2011-03-05
If you've been "editing" files on the Windows partition (that doesn't seem to exist :-) ), that could be the problem.
Maybe you could try running the repair console from the installation disc and in the Command Prompt option run ```
chkdsk C: /r
```
and keep running it until no errors are reported.

---

### Post by TheAJGman on 2011-03-05
I have already done that. When I installed ubuntu I made a new partition specicificly for it and gave it about 50 gigs of space Wichita left windows room. But when I try to boot it won't work I have already backed up all my files. But I can't reinstall windows 7 because it was an upgrade from vista so I can't reinstall 7 I'd have to reinstall vista then boot to 7 disk and then install on a separate partition. Leaving me with about 20 partitions which would be confusing be cause windows see's ubuntu on about 6 partitions.

---

### Post by Quackers on 2011-03-05
You can do a fresh install from an upgrade disc. I don't have a link for that but google will bring up about 356 million hits.

---

### Post by TheAJGman on 2011-03-05
No you can't if i try it says that the pkey is for upgrading from a previous installation of windows

---

### Post by Quackers on 2011-03-05
You have to install it twice if I remember correctly.

---

### Post by TheAJGman on 2011-03-05
crap cant access windows partition anymore

---

