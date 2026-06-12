---
title: "Ubuntu setup"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by AFUNA on 2009-01-29
I already downloaded ubuntu 8.10 from the official site
already tried it by setting it up inside windows and it worked just fine
and after about 45 days of testing and getting used to it
I formatted my PC and I wanted to turn into an official ubuntu user so I tried to install it from the start up not inside windows but it failed I dunno why but it is something in the partition resizing step or something then I said fine fine I will just install it inside windows :???:
but it always wanna download ubuntu 8.10 so I said what is the *#_$..
why to download the same version I already downloaded and burned it on CD
and to be honest I dont think the the official site servers quite fast and they are very lame to handle another download .
so am sure that there is a way to set it up without internet connection ..
or I would prefer not to set up it from inside windows and do it from the start up of the PC ..
I hope I explained my problem clearly cos I really wanna get back to linux I got used to it and u all know that windows sux :)

---

### Post by eddietours on 2009-01-29
did you use wubi?

---

### Post by mrfr0g on 2009-01-29
Hello,

From your description it sounds as if you downloaded the Wubi installer and installed Ubuntu from Windows, which worked out okay. You then attempted to install Ubuntu from a freshly formatted computer, and the partition re-sizer failed.

If this is the case, you may want to install Ubuntu using the alternate installer. 

[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

It's a non-graphical version of the installer program, and it usually works better for me in most cases. You also have the option from that page of downloading Ubuntu via a P2P torrent file. The torrent method, for me, is always faster then downloading directly from the server.

Best of luck!

---

### Post by AFUNA on 2009-01-30
woow this was fast :D
> **eddietours said:**
> did you use wubi?
yup !!
@mrfr0g
Ok I will download it and tell you the results but as I read
> This installation CD is suited for computers unable to run the graphical desktop based installation, either because their computer does not meet the minimum requirements for the live cd or because their computer requires configuration after the installation is complete in order to use the desktop.
so  I guess my problem is because their computer requires configuration after the installation is complete in order to use the desktop.
cos am sure that my PC is good enough to handle Linux :D
but Will it work ?
partition re-sizer failed and installation  processes ?

---

### Post by theozzlives on 2009-01-30
choose Guided-use entire disk

---

### Post by hyper_ch on 2009-01-30
if you select "use entire disk" then all your data will be deleted. Also the windows stuff. Are you sure you want that?

---

### Post by AFUNA on 2009-01-31
Hell NO I dont :D
anyway is there any direct download to the alternate installer cos I have some problems with torrents right now :(

---

### Post by ugm6hr on 2009-01-31
Start from the beginning.

If you have >512mb RAM, you will not need the Alternate CD.

How many HDs do you have?
Where did you get the Ubuntu CD from (official ubuntu.com or elsewhere)?
What partitions do you have?
What version of Windows do you have?

I'd suggest you read through: [http://psychocats.net/ubuntu](http://psychocats.net/ubuntu)

It is often sensible to manually shrink your Windows partition, then, either manually create partitions (if you understand partitioning), or use the "Guided - use largest free space" option.

---

### Post by AFUNA on 2009-02-02
> **ugm6hr said:**
> Start from the beginning.

If you have >512mb RAM, you will not need the Alternate CD.

I have 1GB RAM and still facing the problem :(
> **ugm6hr said:**
> 
How many HDs do you have?

only one and it is 160 GB
> **ugm6hr said:**
> 
Where did you get the Ubuntu CD from (official ubuntu.com or elsewhere)?

Ya from the official site
> **ugm6hr said:**
> 
What partitions do you have?

Windows on C (30 GB)
Linux I wanna it on D (30GB)
> **ugm6hr said:**
> 
What version of Windows do you have?

Windows XP SP2

when I try to install it from windows it starts downloading again the same version
pic:

[IMG]http://img134.imageshack.us/img134/4364/screengb8.jpg[/IMG]

---

### Post by ugm6hr on 2009-02-02
How did you set up your partition D?  You do not need to resize any partitions now.

My suggestion: 
Delete partition D (leave unallocated / empty)
Poot Ubuntu CD in CD drive
Reboot PC
At BIOS (opening screen) - select "Boot from CD" - most computers use F2 or F12 to access this at the time of turning on
Select "Install to HD"
Use the "Guided - Use largest free space" option.
The rest is pretty obvious.

PS: You have a 160GB HD with 2 30GB partitions - what's on the rest?

---

### Post by theozzlives on 2009-02-02
You need to boot up off the CD, get out of Windows,

---

### Post by AFUNA on 2009-02-02
> **ugm6hr said:**
> How did you set up your partition D?  You do not need to resize any partitions now.

My suggestion: 
Delete partition D (leave unallocated / empty)
Poot Ubuntu CD in CD drive
Reboot PC
At BIOS (opening screen) - select "Boot from CD" - most computers use F2 or F12 to access this at the time of turning on
Select "Install to HD"
Use the "Guided - Use largest free space" option.
The rest is pretty obvious.

I will try it and tell u the results ;)
> **ugm6hr said:**
> PS: You have a 160GB HD with 2 30GB partitions - what's on the rest?
My other data :twisted:
> **theozzlives said:**
> You need to boot up off the CD, get out of Windows,
Already didnt work but I will try ugm6hr's suggestions :D

---

### Post by AFUNA on 2009-02-02
unfortunately I did the same as suggestions said but same message
which I captured it with my camera .. :(
here u are the pic

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=101886&stc=1&d=1233577994[/IMG]

sorry for the bad resolution but I just formatted and didnt set my virtual PC yet to take a better screenshot :oops:
ps: I got a CD/DVD drive

---

### Post by tarps87 on 2009-02-02
virtual PC? Are you trying to install in in a virtual pc or on the actual hardware?
Is this the version you downloaded?
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
It should be an iso, if so you may want to verify your download:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

---

### Post by AFUNA on 2009-02-02
No I said "**didnt **set my virtual PC yet to take a better screenshot"
and it is on actuall hardware
am downloading Ubuntu 8.10 Desktop (the latest version)

---

### Post by ugm6hr on 2009-02-02
It looks like the CD booted just fine.

Then, during the installation, it ran into errors, presumably due to a bad CD burn.

Did you run the "Check CD for errors" from the launch menu?

Also - I asked about your partitions for a reason.  The Ubuntu Guided install creates a primary partition and an extended partition within the free space, and then a logical partition within the extended for swap.  If you already have more than 2 primary partitions it won't work.

---

### Post by AFUNA on 2009-02-03
May be I should burn a new CD !?
and about the partitions issue so how I can have 2 operating systems on two different partitions cos when I did the {{Use the "Guided - Use largest free space" option.}} suggestion it removed my C partition free space which has the windows ..

---

### Post by ugm6hr on 2009-02-03
> **AFUNA said:**
> May be I should burn a new CD !?

Read the advice re: md5 checks and checking CD for errors.

If it fails - re-download / re-burn.

---

### Post by AFUNA on 2009-02-12
sorry for the absence ..
re-downloaded from along time but didnt have the chance to try it
but I did and all things are working now just fine and am back to my sweeeeet ubuntu :D
Thanks for the support and My regards ;)

---

