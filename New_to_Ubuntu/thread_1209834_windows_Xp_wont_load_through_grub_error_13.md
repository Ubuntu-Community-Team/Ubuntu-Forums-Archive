---
title: "windows Xp wont load through grub error 13"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by windy81 on 2009-07-10
This was my solution

from :- Applications/Accessories/Terminal 

type 

```
sudo fdisk -l
```my results were

```

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9403    75529566    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdac08953

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30027   241191846   83  Linux
/dev/sdb2           30028       30401     3004155    5  Extended
/dev/sdb5           30028       30401     3004123+  82  Linux swap / Solaris
```from this we know that :-

**dev/sda    =   internal HD with Windows XP**

[B]dev/sdb    =   external HD with Ubuntu
[/B] 
so next we need to know what their aliases are or in other words what grub calls the drives. Very important!

type in

```
gedit /boot/grub/device.map
```my resulte were

     ```
(hd0)    /dev/sda
(hd1)    /dev/sdb 
```from this we know that:-
 [B]
(hd0)    =    dev/sda   =   Internal HD with XP[/B]
[B]
(hd1)    =    dev/sdb   =   External HD with Ubuntu[/B]

so next we need to tell Grub, which loads up the OS you want via the start menu
where to look to boot up the appropriate OS you select.

1st though we might want to see the READ only version, just in case we make any mistakes

type

```
gedit /boot/grub/menu.lst
```my results were

  ```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1
```so now we know that Grub is trying to load the Windows Xp from the correct disk, 
but why isnt it working ? 

[B]I now know that Windows Xp doesn't like to load the OS from the 1st partition on a drive so we have to fool it to think it's loading from another partition
[/B] 
type

```
gksudo gedit /boot/grub/menu.lst
```which will bring you to the READ and WRITE terminal of GRUB. 

Be careful not to write any mistakes here and not to inadvertently save it incorrectly.
You might want to backup this list, as a cautionary measure

here was mine, same as above, other than the fact i can edit this list and save it.

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1 
```[B]so we need to fool the Windows to make it think it's loading from another 

partition except for the 1st one, so re-write the GRUB menu.lst as follows,[/B]

**adding the mapping commands**


```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
savedefault
chainloader    +1
```now your windows should start up correctly.

good luck.

and if the problem of yours isnt quite the same, i hope the logic here will enable you to work it out for yourself.

Thanks LEW again, you are an amzing guy. 
Bye Bye ):P

**[original post below]**
> totally new to ubuntu so im totally clueless as to the commands i need to get this sorted

i have Ubuntu installed on an external HD (dev/sdb)

i have Windows Xp installed on my internal HD (dev/sda)

when i try and load Windows Xp through grub start menu i get error 13. 
Howver if i disconnect the hard dive with ubuntu on it (dev/sdb),  Windows loads up perfectly.

what do i need to do to get grub to load windows  properly through grub?

thanks

---

### Post by Western Digital on 2009-07-10
Although I have no solution to the problem, I can say that I have experienced the same problem that you are having. I have noticed that I can't have any sort of removable media in my computer if I want to even think about using GRUB.

Sorry for no solution. :/

---

### Post by windy81 on 2009-07-10
thats ok..... this is  the first problem i need to sort out.
im really keen to get ubuntu working nicely, i just dont understand it yet:lolflag:

2nd problem is booting ubuntu when my other external hard drive is connected (dev/sdc)... but that shall wait till later;)

---

### Post by LewRockwell on 2009-07-10
here, you've got your machine set up to boot from USB before the internal hard drive

sometimes I have students that want to have "just a windows machine" but want their other distros to be selectable whenever they plug in their external hard drive

what happened with your installation is that the grub was installed to the mbr of the external drive(which is fine if you want it that way...it's actually kind of cool)

so what do you want to do?

.

---

### Post by LewRockwell on 2009-07-10
and while I'm waiting for what you'd like to do I'll address the booting issues mentioned

when the computer first boots, the BIOS settings direct it to look at devices in a certain order

The order is mainly a preference of usage and is both easily changed by altering the BIOS settings OR by depressing the "F12" key about twice per second during the beginning of the power-on phase of the computer start-up sequence

Note: even if you have your USB(s) and/or optical drive(s) set to be checked before your hard drive, if the media is NOT bootable then the BIOS will continue on past it til it finds media that IS bootable

So, what this means is that a CD/DVD and/or thumb drive with random folders/directories/files/data on it will be "seen" as non-bootable(this is what sometimes happens when someone downloads a Linux ISO/Image and then just "copies" it to a disk...then the disk is not written in such a fashion as to be "bootable")

Hopefully that makes sense and gives some folks an "ahHA" moment

.

---

### Post by windy81 on 2009-07-10
i should have said, i installed the grub on the external hard drive (dev/sdb) alongside the Ubuntu installation, 
so i thought, 
whenever i connect that external hard drive i would get a selection as to what OS i wanted, 
i.e i could leave it plugged in and simply choose whenever i booted up.

is that not possible ?


also i have the windows BIOS to select CD ROM 1st, External HD 2nd, and Internal HD 3rd, so is well i think

---

### Post by windy81 on 2009-07-10
thanks you for taking the time to help out. I do appreciate it

---

### Post by LewRockwell on 2009-07-10
> **windy81 said:**
> i should have said, i installed the grub on the external hard drive (dev/sdb) alongside the Ubuntu installation, 
so i thought, 
whenever i connect that external hard drive i would get a selection as to what OS i wanted, 
i.e i could leave it plugged in and simply choose whenever i booted up.

is that not possible ?


also i have the windows BIOS to select CD ROM 1st, External HD 2nd, and Internal HD 3rd, so is well i think

yes, it is quite useful to have the boot-up complete in that manner

here, you can do one of two things:

you can leave it "as is" and only boot windows with the external hard drive removed and only boot Ubuntu when the external hard drive is plugged in

or

you can correct the grub to successfully boot windows as you originally intended

I'll post this and then amend it so you can read up to this point

.

---

### Post by windy81 on 2009-07-10
> **LewRockwell said:**
> yes, it is quite useful to have the boot-up complete in that manner

here, you can do one of two things:

you can leave it "as is" and only boot windows with the external hard drive removed and only boot Ubuntu when the external hard drive is plugged in

or

you can correct the grub to successfully boot windows as you originally intended

I'll post this and then amend it so you can read up to this point

.

you know, i like things to work smoothly... 
yes u are right i could leave as is, but i would rather the grub start-up screen work as it should.

now my theory is that grub is looking in the wrong place for the Windows OS. I could be wrong, 

i have read other googled posts on error 13, i just dont understand the codes hd1,0 hd0,0 etc etc...

---

### Post by windy81 on 2009-07-10
tell me what commads u need to see from the "terminal" application and i will post it here. 
I've wroked out how to use that, barely :P

---

### Post by LewRockwell on 2009-07-10
> **windy81 said:**
> tell me what commads u need to see from the "terminal" application and i will post it here. 
I've wroked out how to use that, barely :P

While booted up into Ubuntu from your external drive installation you can view(read only) your /boot/grub/menu.lst file to see what it looks like

Through the GUI you can find that via your "Places" drop-down menu by selecting "computer" then "file system" then "boot" then "grub" and finally "menu.lst"

Again, this is in "read-only" mode so even if you attempt to change anything in this gedit screen, you won't be able to save any changes(this is a "by design" safety so that the uninitiated can go "exploring" without blowing things up

I'll post this and then continue

.

---

### Post by LewRockwell on 2009-07-10
In menu.lst you can scroll down to where the windows information is located and it will look something like:

```
title            Microsoft Windows (on hda1)
rootnoverify     (hd0,0)
savedefault
makeactive
chainloader      +1
```


can you find it?

what does yours say?

.

---

### Post by windy81 on 2009-07-10
ok lew went offline :(

can anyone else help me please.... 
all i need to do is set grub to load windows from the internal hard drive.

---

### Post by windy81 on 2009-07-10
aesome you came back... im on to it. gimme a sec :guitar:

---

### Post by windy81 on 2009-07-10
```
dylan@dylan-laptop:~$ /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied

```

so that didnt work :(

```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

```

so that was by typing gedit /boot/grub/menu.lst

---

### Post by LewRockwell on 2009-07-10
now that I've shown you how to safely view your menu.lst

we'll now move on and get dangerous

```
gksudo gedit /boot/grub/menu.lst
```and after keying that in and depressing "enter" you'll be magically transported into a LIVE(read AND write) session of the file editor

I'll post this and wait to see how your menu.lst looked

.

---

### Post by windy81 on 2009-07-10
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

```

says the same thing,

so what information do u need from me now to ascertain where to aim the windows boot up process ?

---

### Post by LewRockwell on 2009-07-10
ok, you've used the terminal to go to the file in read-only mode which is good

and we can see that the grub was initially set up with the default which is (hd0,0)

grub "sees" drives and partitions "from" "zero" which means that it's looking for windows on the first partition of the first booted device

of course, your external drive was booted first so it is the "first booted drive" hence, your problem

I'll post this and then continue

.

---

### Post by windy81 on 2009-07-10
excellent, i think were making progess. thank you so much Lew.

what's the next step ?

---

### Post by LewRockwell on 2009-07-10
> **windy81 said:**
> ```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

```

says the same thing,

so what information do u need from me now to ascertain where to aim the windows boot up process ?

if you've opened a read and write editing session(using gksudo gedit) then you might as well go ahead and change the first zero to a one(hd1,0) and save the edited menu.lst file

try booting again and see what happens, if it doesn't work then we'll move on to the next step

.

---

### Post by windy81 on 2009-07-10
ok. :)

---

### Post by windy81 on 2009-07-10
tried booting Windows Xp from the grub menu....

its hangs at the   *"starting up*....."   text. i waited 2 mins, no joy. 

Good news is that error 13 didn't come up this time.

---

### Post by windy81 on 2009-07-10
this is my sudo fdisk -l  if that helps ```
dylan@dylan-laptop:~$ sudo fdisk -l
[sudo] password for dylan: 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95aa95aa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9403    75529566    7  HPFS/NTFS

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xdac08953

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       30027   241191846   83  Linux
/dev/sdb2           30028       30401     3004155    5  Extended
/dev/sdb5           30028       30401     3004123+  82  Linux swap / Solaris

```

---

### Post by LewRockwell on 2009-07-10
and for the benefit of general reference and future viewers of this thread, we'll continue while Windy81 attempts the correction we've described so far...

if that doesn't work then we'll see what the windows drive is REALLY being called by doing this:```
sudo fdisk -l
```and that's a little "L" and NOT a "one"


I have a suspicion that it might also be (sd1,0) so we'll see

at any rate, you can see the process, the method, and the reasoning

it is important when initiating a trouble-call, by starting a thread on a forum, to be reasonably specific in your title and initial subject matter

that way, if you take off for a few minutes to get something from the deli around the corner...while you're away someone can hopefully be answering your questions at the same time

class dismissed(hopefully...lol)

.

---

### Post by windy81 on 2009-07-10
see above :P

---

### Post by LewRockwell on 2009-07-10
suspicions confirmed...lol

hopefully we've proceeded in a fashion where you know both HOW and WHAT to do!

.

---

### Post by LewRockwell on 2009-07-10
> **windy81 said:**
> see above :P

see above

```
gksudo gedit /boot/grub/menu.lst
```then change the (hd1,0) to (sd1,0) and save and see if that works

.

---

### Post by windy81 on 2009-07-10
like i said... i dont know but i'll take a guess. 

should i re write in the ```
gksudo gedit /boot/grub/menu.lst
```

command to set hd7,0 ?  the ID says that the internal HD is 7..lol i dunno.

---

### Post by windy81 on 2009-07-10
> **LewRockwell said:**
> see above

```
gksudo gedit /boot/grub/menu.lst
```then change the (hd1,0) to (sd1,0) and save and see if that works

.


ok. i'll be back in  a minute.

---

### Post by windy81 on 2009-07-10
nope changing it to (sd1,0) didnt work. I now get "error 23" "error in parsing number"  :(

---

### Post by LewRockwell on 2009-07-10
> **windy81 said:**
> nope changing it to (sd1,0) didnt work. I now get "error 23" "error in parsing number"  :(

hang tight and I'll put together the fix...

---

### Post by windy81 on 2009-07-10
thank you so much Lew, i really appreciate this.

---

### Post by windy81 on 2009-07-10
as i'm waiting, googling it myself, thought this might be useful
```
gedit /boot/grub/device.map
```results of which are

```
(hd0)    /dev/sda
(hd1)    /dev/sdb
```

im thinking that (hd0) is the right command, 
however it might be pointing at the wrong partition on the HD so it might be (hd0,1)  (hd0,2) or something like that ?

---

### Post by LewRockwell on 2009-07-10
> **windy81 said:**
> thank you so much Lew, i really appreciate this.

try changing the menu.lst entry for windows to:```

title        Microsoft Windows XP Professional
rootnoverify (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
makeactive
savedefault
chainloader    +1
```

(windows doesn't like not being on the first partition of the booted drive so we'll try to fool it with some "mapping")

.

---

### Post by windy81 on 2009-07-10
> **LewRockwell said:**
> try changing the menu.lst entry for windows to:```

title        Microsoft Windows XP Professional
map (sd0) (sd1)
map (sd1) (sd0)
rootnoverify (sd1,0)
makeactive
savedefault
chainloader    +1
```(windows doesn't like not being on the first partition of the booted drive so we'll try to fool it with some "mapping")

.


im assuming i add those mapping lines in "gksudo gedit /boot/grub/menu.lst"  ?? ????

---

### Post by LewRockwell on 2009-07-10
> **windy81 said:**
> im assuming i add those mapping lines in "gksudo gedit /boot/grub/menu.lst"  ?? ????

yes, except notice that I've changed it back from sd to hd

and I also moved the rootnoverify line(shouldn't make a difference!?!)

.

---

### Post by windy81 on 2009-07-10
ok it looks like this now
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
savedefault
chainloader    +1

```

one question, is the spaces between "rootnoverify" and  "(hd1,0)" crucially important ?

---

### Post by windy81 on 2009-07-10
that worked perfectly Lew, thank you very much. 
I'm now going to update this thread so that the 1st post explains how to do it all. and put [Solved ] in the title :)

---

### Post by LewRockwell on 2009-07-10
> **windy81 said:**
> that worked perfectly Lew, thank you very much. 
I'm now going to update this thread so that the 1st post explains how to do it all. and put [Solved ] in the title :)

It seems that although the title to the original post can be edited...it doesn't change/update the overall thread title...hopefully I am wrong and/or that will change

also, you might direct others to the thread we should have worked from first...lol...go figure...hey, we're all in this together!

[http://ubuntuforums.org/showthread.php?t=1036702](http://ubuntuforums.org/showthread.php?t=1036702)

.

---

### Post by LewRockwell on 2009-07-10
> **windy81 said:**
> ok it looks like this now
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
rootnoverify (hd1,0)
makeactive
savedefault
chainloader    +1

```

one question, is the spaces between "rootnoverify" and  "(hd1,0)" crucially important ?

I don't think "all" the spaces are critical but in some places they do make a difference(I just try to match the format and layout of the rest of the document/file/etc)

.

---

### Post by windy81 on 2009-07-10
have a look at the first post now Lew. I've tried to break it down so that people can understand it easily.

Tell me if

A] made any mistakes

and

B] if i should add something

regards

dylan

---

### Post by LewRockwell on 2009-07-10
> **windy81 said:**
> have a look at the first post now Lew. I've tried to break it down so that people can understand it easily.

Tell me if

A] made any mistakes

and

B] if i should add something

regards

dylan

Good job editing/updating your first post Dylan! That sure makes it easier for others since they don't have to wade through the whole thing if they don't need to. You were giving me a run for my money as fast as you were coming back(not to mention that we were both googling and adding stuff at the same time).

Of course, this same situation has been hashed out hundreds of times on the interwebs over the course of the last few years...lol.

Hey, pay it forward and we're all in this together!

.

---

### Post by windy81 on 2009-07-10
indeed. googling it just gave me a hash of data, that i couldn't makes sense of. 
so thanks again, and i hope someone can get this thread and find it useful.

---

