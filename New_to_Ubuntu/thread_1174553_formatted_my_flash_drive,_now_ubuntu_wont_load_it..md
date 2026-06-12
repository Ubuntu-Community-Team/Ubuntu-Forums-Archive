---
title: "formatted my flash drive, now ubuntu wont load it."
date: 2009-05-31
forum: New to Ubuntu
---

### Post by djmh on 2009-05-31
well its a 512 dell, there were a bunch of files on it... i wanted to free up some space to put portable apps on,but when i went to delete the files ubuntu wouldn't let me, so i googled around and tried sudo r-m and all that (i was careful and selected the correct drive) but even that wouldn't work, it just asked for my password then went back to $
i assumed it worked, but after opening my drive the files were still there.
so i tried ch mod 777 next - but that said it couldn't find the folder ( which i thought raised a red flag ) but either way, that didnt work either
so i found another post that said to get gparted and format the drive - so i did .. i think...
what i did was found my flash drive in gparted and deleted the partition then went on to make a new partition ( fat 16 ) and i got an error that it couldnt complete the operation, so i just restarted seeing if maybe it would refresh the drive and let me make a partition ( lol, i resorted to restarting - can you tell i used to use windows? )
but upon restarting my flash drive lights up showing its connected, but nothing else, i cant see it in my filesystem, or gparted
so can i get my flashdrive back, or did i essentially brick it ?
thanks for all your help,let me know if i can provide any more details.

and for future reference how do i make it easier to put files on, and remove files from my drive hopefully without having to use terminal ( though i dont mind if i have to) but i really would prefer to just hit delete and have my files deleted, no extra hassle - all beacause i have a netbook, and i plan on running most of my programs on my flash drive ... to free up hd space.
or is that not a possible solution with ubuntu ?

---

### Post by Sir Jasper on 2009-05-31
Hi,

I would suggest you try FAT32 (Not FAT16) and reformat your USB Flash Stick using Gparted. Make sure it is not mounted before you try to format it.

Once properly formatted you should be easily able to copy, paste or delete files.

My regards

Let us know of any progress, problems or misunderstanding by me.

---

### Post by djmh on 2009-05-31
well, i would reformatt it. but when i plug it in ubuntu dosent recognize it.
what i mean is,i get a connectivity light on the drive itself - but it wont show any options to open a folder, and it isnt visible in gparted.
basically i cant access it at all, the computer is showing that it is not even there though it is.

i think i see a potential problem though, i formated it when it was still mounted.

is there any way to get my drive back ?

---

### Post by djmh on 2009-05-31
ok, now the drive is showing up, i click on it and it says unable to mount drive - so im assuming it isnt mounted, so im going to try a fat 32 format.
so i click on the unallocated sector,choose new>fat 32>primary partition(should it be extended partition ? ) cool, it says all operations worked - thanks for the fat32 tip, that must have been it :)

---

### Post by djmh on 2009-05-31
well, evrything worked in gparted like you probably read, but now i go to place>computer>usb drive
and i get an error: Unable to mount location
Can't mount file

any suggestions ?

---

### Post by durand on 2009-05-31
In a terminal (Applications > Accessories > Terminal), type dmesg and see if there are any related errors towards the end of that output.

---

### Post by mike555 on 2009-05-31
Is this thumbdrive one that has " U3 " on it ? if so you can only format it with a little U3 removing program in Windows ....... then you can reformat it fat32 . you can get the removing program from the thumbdrive makers site or just do a search for it...

---

### Post by djmh on 2009-05-31
when i run dmesg i get :

> [ 1443.668893] [drm:i915_get_vblank_counter] *ERROR* trying to get vblank count for disabled pipe 0
[ 1443.677364] mtrr: no MTRR for d0000000,10000000 found
[ 1446.508319] [drm:i915_setparam] *ERROR* unknown parameter 4
[ 1446.508372] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 1447.729615] [drm:i915_getparam] *ERROR* Unknown parameter 6
[ 1460.398889] [drm:i915_getparam] *ERROR* Unknown parameter 6
richie@richie-netbook:~$ 


those errors

and no it is not u3

---

### Post by durand on 2009-05-31
Doesn't seem to be related. You can try mounting the usb drive manually. You need to know what the drive is called or just use some trial and error.

```
mkdir usb_drive
sudo mount /dev/sdb1 usb_drive
```
You might need to change sdb1 to something else like sdc1 or maybe sdb2 if there is a hidden partition on the usb drive.

---

### Post by djmh on 2009-05-31
i can see the usb drive in computer it is call

USB Drive

so your code reads

mkdir usb_drive
sudo mount /dev/sdb1 usb_drive


should mine be

mkdir USB Drive
sudo mount /dev/sdb1 USB Drive


btw, in gparted it is call /dev/sdb1

---

### Post by djmh on 2009-05-31
if this dosent work im just going to chuck this old drive - its only 512, theres no reason to have evryone trying to fix it.
ill just pick up a 4 gig ...

but what did i do wrong with this drive ? - cause i cant afford to keep bricking flash drives.

so what do you think went wrong when i could delete files and stuff off the drive ? ( see original post )

how can i avoid this happening again, and when i get my new drive will it work right off the bat ? - like ill be able to delete all my files and have it work like a flash drive should ?
 or do i need to format it for linux ( i will be using it on windows once and a great while for transfering files at school though )

will u3 be a pain to remove, cause the drive ill get will probably have u3 on it.

---

### Post by durand on 2009-05-31
No, usb_drive is the folder you are mounting it to. So if you run ```
sudo mount /dev/sdb1 usb_folder
``` and then look in your home, there should be a folder called usb_folder with your usb stuff inside it, hopefully.

If it didn't work, post the error here.

I've never heard of a simple usb drive not working in linux so I dunno what you did..

---

### Post by djmh on 2009-05-31
sudo mount /dev/sdb1 usb_folder

gives me

mount point usb_folder does not exist


any suggestions ? - if not dont worry about it , i really apreciate your help though

yeah, i have used many usb devices in linux, (psp flash drives and portable hd) with no problems - till i got to this drive and it not wanting to delete files 

though i have read many other posts bout linux not wanting to delete files off a flash drive, do you know anything about this ?

cause that is what started my whole problem was not being able to remove folders and files, and i dont want that to happen again.

---

### Post by durand on 2009-05-31
You need to create the folder first. See post #9 on thi thread.
```
mkdir usb_folder
```

---

### Post by billgoldberg on 2009-05-31
> **djmh said:**
> sudo mount /dev/sdb1 usb_folder

gives me

mount point usb_folder does not exist


any suggestions ? - if not dont worry about it , i really apreciate your help though



Let me break it down to you.

First you create a directory *(folder)* to mount your drive to. This can be done in Nautilus *(the file manager)* or using the mkdir command.

External devices are usually kept in /media *(not in /home as another user suggested)*.

Now create a directory in /media to mount your usb stick to. 

Let's call that directory "usb_folder".

```
sudo mkdir /media/usb_folder
```

Now you can mount your usb device *(/dev/sdb1) *to that newly created directory (*/media/usb_folder)* using the mount command.

```
sudo mount /dev/sdb1 /media/usb_folder
```

In Nautilus, the drive will now be listed between the other ones.

---

### Post by djmh on 2009-05-31
WOW ! - i think it worked !!
thank you so much !
i entered the codes and got no errors, and now if i go to my home folder and go into usb_folder i am in my drive i think !

is that all there is to it ?
like now i can save files to my drive and evrything ?
and will it load my flash drive up on startup ?

man, you guys are the best at these forums, i have not had a problem go unsolved yet :)

---

### Post by djmh on 2009-05-31
uhhhm, yeah they are supposed to be in media arent they ? - i already made it in my home directory - how would i go about moving it ?

im asking before i break anything lol

---

### Post by durand on 2009-05-31
Unfortunately, it won't load your flask drive unless you add a line to /etc/fstab though you may have fixed the flash drive by mounting it like that. Try unplugging and plugging it in again. Does it mount as normal, without using the terminal?

---

### Post by durand on 2009-05-31
It doesn't have to be in media, but thats where things are normally stored. I just used home as a temporary location. To move it to media, you need to unmount it first and then do as billgoldberg wrote.

Unmount it with:
```
sudo umount /dev/sdb1
```

---

### Post by billgoldberg on 2009-05-31
> **djmh said:**
> uhhhm, yeah they are supposed to be in media arent they ? - i already made it in my home directory - how would i go about moving it ?

im asking before i break anything lol

You can unmount the drive in Nautilus and then use the mount command to mount the drive to the /media/usb_folder directory.

You can then remove the directory you created in /home.

---

### Post by djmh on 2009-05-31
so i unplugged it and there is still a 509.9 meg media sitting on my desktop - and i can still open it and everything, is that bad ?

when i plug it in it opens up my flash drive in the file browser !!

do i delete the 509.9 meg media or leave it ? or unmount it or what ?
but my flash drive seems to be working :)

---

### Post by durand on 2009-05-31
That *is* your flash drive. You can't delete it even if you tried. Unmounting it would unmount your flash drive so you won't be able to do anything with it.

---

### Post by djmh on 2009-05-31
oh alright, thank you for your help :)
lol, cant wait till i can start providing help to people too !

---

### Post by djmh on 2009-05-31
uhhhm when i pull my flash drive out, there is still a flashdrive drive on my desktop, is this ok ? - or is there something i should do ?
i can go into and evrything like the drive is still plugged in...but its not ...

---

### Post by djmh on 2009-05-31
oh, and if i plug the flash drive in i get another drive called flash drive that pops up .... no bug deal, but if i could get them all to go away when the flash drive is removed that would be preferable .

---

### Post by Sir Jasper on 2009-05-31
Hi again,

Very pleased your problem is sorted. If, at some stage, you decide to get a larger flash stick, then investigate the read and write speeds before you decide which one to buy. 

My regards

---

### Post by nandemonai on 2009-05-31
> **djmh said:**
> uhhhm when i pull my flash drive out, there is still a flashdrive drive on my desktop, is this ok ? - or is there something i should do ?
i can go into and evrything like the drive is still plugged in...but its not ...

You really should be ejecting it before you remove it. Failing to do so can cause corruption on the disk. This is because of delayed writes.

---

