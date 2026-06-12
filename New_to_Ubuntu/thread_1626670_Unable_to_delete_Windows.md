---
title: "Unable to delete Windows"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by beew on 2010-11-20
Hi,

When I started playing with Ubuntu about 5 months ago I created a dual boot with Windows XP just in case. Now for 5 months I have logged in to Windows only twice to update my antivirus. I think it is time to get rid of Windows either to dual boot with another Linux or give the whole hard drive to Ubuntu.

But I am not able to delete the Windows partition. The unmount option in gparted is greyed out and it says there are bad sectors and it couldn't read the content of the partition. 

I have encountered the same problem when I created the dual boot. I ran check disk and defraged several times in Windows and it didn't report any error. The original partitioning for the dual boot was created in Windows using Easeus parition manager since I couldn't do it with gparted from the live usb.

I cannot find the posts now but I have asked about the bad sectors in the forum and on someone's advice, did some tests using some "smart tools "and he said the error message is most likely a false alarm based on  the outputs.

Thanks in advance for any advice.

---

### Post by Hippytaff on 2010-11-20
You could back up all your important stuff and do a fresh install? :-)

---

### Post by acrazyplayer on 2010-11-20
Gparted is very picky I have come to learn. 

Maybe try using cfdisk in a terminal. It's a lot like gparted,  just read everything twice before you push "write" and afterwards try gaprted again and see if it works then. 

For example I could not for the life of me format a usb stick with gparted, then I used cfdisk and it deleted everything on the usb drive but it didnt do so well creating a fat32 partition so I then used gparted and it worked fine. 

Good luck and after you delete windows make sure you run "sudo apt-get update-grub" so its not an empty option to boot from

---

### Post by Garandir on 2010-11-20
Boot from the LiveCD, you can use Gparted from there and delete it.

---

### Post by beew on 2010-11-20
> **Garandir said:**
> Boot from the LiveCD, you can use Gparted from there and delete it.

If it works I wouldn't have started this thread. ;)

---

### Post by beew on 2010-11-20
> **acrazyplayer said:**
> Gparted is very picky I have come to learn. 

Maybe try using cfdisk in a terminal. It's a lot like gparted,  just read everything twice before you push "write" and afterwards try gaprted again and see if it works then. 

For example I could not for the life of me format a usb stick with gparted, then I used cfdisk and it deleted everything on the usb drive but it didnt do so well creating a fat32 partition so I then used gparted and it worked fine. 

Good luck and after you delete windows make sure you run "sudo apt-get update-grub" so its not an empty option to boot from

I will take a look at cfdisk, thanks.

I however never have had a problem with formatting usb sticks with gparted. I do it a lot. Actually I am now posting from a Fedora live usb which I have formated with gparted.

---

### Post by beew on 2010-11-20
> **Hippytaff said:**
> You could back up all your important stuff and do a fresh install? :-)


I could also backup all my stuffs and buy a new computer. :p

---

### Post by garvinrick4 on 2010-11-20
See what the partition # for Windows is in Ubuntu:   (This is a +1 on post #2)
```
sudo fdisk -l
``` (lower case L)
Do a fresh install of Ubuntu to that partition sda# (whatever it is) using manual install.
Use a version of Ubuntu you are not using. Will reformat for you while installing:
If you decide later you just want to have 1 install instead of 2 installs can do that in gparted: Just make sure you install grub2 to sda not sda1 or sda5 but sda
Enjoy your Ubuntu and always as has been said; Backup your home before messing with drive at all times.

---

### Post by Hippytaff on 2010-11-20
> **beew said:**
> I could also backup all my stuffs and buy a new computer. :p

That's always an option - I wish I could afford to do that :-)

---

### Post by randumnumber on 2010-11-20
> **Hippytaff said:**
> That's always an option - I wish I could afford to do that :-)

You know thats a good idea, thats what im going to do. New computer here i come.

---

### Post by DogMatix on 2010-11-20
> **beew said:**
> I could also backup all my stuffs and buy a new computer. :p

Sometimes a fresh install feels like a new computer ;)

---

### Post by Hippytaff on 2010-11-20
> **DogMatix said:**
> Sometimes a fresh install feels like a new computer ;)

This is true, that's what I tell myself anyway :-)

---

### Post by karthick87 on 2010-11-20
Install Gparted partition Manager,and delete  the windows partition

**[CLICK HERE TO INSTALL GPARTED]("apt://gparted")** 

After installing open it from  from System-->Administration-->Gparted

Unmount your windows drive by right clicking windows partition and then click delete..

[IMG]http://imagebin.org/124143[/IMG]
[IMG]http://imagebin.org/124143[/IMG]

---

### Post by Hippytaff on 2010-11-20
I thought the op was having trouble with Gparted :-s

---

### Post by farsight on 2010-11-20
When you installed the ubuntu OS, did you use the wubi tool by chance? I saw you said you had made the partition using a different tool to gparted, but wasn't sure how you had installed. I am not sure, but it might offer a reason why you cannot delete Window, as Ubuntu is installed within Windows.

---

### Post by Hippytaff on 2010-11-20
> **farsight said:**
> When you installed the ubuntu OS, did you use the wubi tool by chance? I saw you said you had made the partition using a different tool to gparted, but wasn't sure how you had installed. I am not sure, but it might offer a reason why you cannot delete Window, as Ubuntu is installed within Windows.

That would make sense :-)

---

### Post by beew on 2010-11-20
No, it isn't WUBI. It is a genuine dual boot with separate partitions on the hard drive.

I did the partition in Windows first and that's all. No, no Wubi, you won't catch me dead doing that. I hate the idea with a passion. :)

---

### Post by Hippytaff on 2010-11-20
in that case -if gparted doesn't work, then I'd probably use a livecd to back everything up and then reinstall ubuntu - I tend to rely on fresh installs when things go belly up...hence a separate home partition

---

### Post by beew on 2010-11-20
> **Hippytaff said:**
> in that case -if gparted doesn't work, then I'd probably use a livecd to back everything up and then reinstall ubuntu - I tend to rely on fresh installs when things go belly up...hence a separate home partition


There is actually another way, which is to take out the hard drive, plug it into a Windows machine and then try to use some Windows tools to remove the XP partition. But I want to use Linux solutions as much as possible.

I don't want a fresh install because my Ubuntu is highly tweaked and optimized.  I care more about the root partition than the /home partition which is only 20G anyway. I have no useful data on it (all in external drive) If I have to go fresh install I would rather just leave XP alone.

EDITED: also garvinrick4's "fake clean install" method is a lot more attractive than a real clean install.

---

### Post by beew on 2010-11-20
If nothing works I wonder if it would be possible to use something like clonezilla to create a image of the Lucid partition and then wipe the whole thing and restore the image on the drive. I wonder how risky would that be.

---

### Post by Hippytaff on 2010-11-20
you can use the disc creator in ubuntu to make an iso of your current setup I think...or I know that remastersys can do it :-)

---

### Post by Quackers on 2010-11-20
Please excuse me if you have tried this already, but did you run a chkdisk on the Windows partition? If so, did it find errors and did you keep running it until there were no errors reported?

---

### Post by Hippytaff on 2010-11-20
> **Quackers said:**
> Please excuse me if you have tried this already, but did you run a chkdisk on the Windows partition? If so, did it find errors and did you keep running it until there were no errors reported?

Quackers - long time no see :-) I don't think the op has tried that :-)

good to see you here again...where have you been?

---

### Post by beew on 2010-11-20
> **Hippytaff said:**
> you can use the disc creator in ubuntu to make an iso of your current setup I think...or I know that remastersys can do it :-)

The disk creator makes a live usb from an iso image as far as I know. Have you triedb using that to clone your hard drive?:confused:

---

### Post by Quackers on 2010-11-20
> **Hippytaff said:**
> Quackers - long time no see :-) I don't think the op has tried that :-)

good to see you here again...where have you been?

Hi Hippy, I have been (and am still) rebuilding my Natty testing install after a nasty update kiboshed it :-)

---

### Post by beew on 2010-11-20
> **Quackers said:**
> Please excuse me if you have tried this already, but did you run a chkdisk on the Windows partition? If so, did it find errors and did you keep running it until there were no errors reported?

Yes, I did. That was the first thing I did when I created the partition in the dual boot. As I said in my very first post, gparted reported bad sectors and couldn't partition my hard drive when I tried to install Ubuntu so I had to create the partition in Windows. I ran chkdisk many times and defragged several times as well and there was no error reported.

---

### Post by farsight on 2010-11-20
Hey again,

This is a thread you might find useful if you are intending to go along the re-installation route. I've had it bookmarked for when something like this happens to me while I play around with the system. I haven't yet tested it, however if you do choose to follow it I wish you luck with the re-install :)

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5]("http://ubuntuforums.org/showpost.php?p=7157175&postcount=5")

Farsight

---

### Post by Hippytaff on 2010-11-20
> **Quackers said:**
> Hi Hippy, I have been (and am still) rebuilding my Natty testing install after a nasty update kiboshed it :-)
[off-topic]I'm up for a bit of Natty testing, but I'm not sure how to go about it....vm, or true partition, and also, i'm not sure or confident in submitting bug reports[/off-topic]

---

### Post by beew on 2010-11-20
> **farsight said:**
> Hey again,

This is a thread you might find useful if you are intending to go along the re-installation route. I've had it bookmarked for when something like this happens to me while I play around with the system. I haven't yet tested it, however if you do choose to follow it I wish you luck with the re-install :)

[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

Farsight

Thanks. I actually have that page bookmarked as well. But it is not that simple. 

You see I have installed a lot of stuffs from ppas and I even mix repos to get the versions of softwares I want (I am running 10.04 but there are quite a bit of 10.10 in it). I have, as you expect, got busted for dependency problems but so s far I had always been able to get myself out of it doing some gymnastics (;)) so my system is very optimized but its configuration is a bit unusual. It is just the way I want so I wouldn't risk losing that to do a clean install. I expect tons of errors if I try to reinstall the software using lovinglinux's script.:)

 Everybody says back up your /home partition but I couldn't care less about my home partition. The actual settings of my programs are not too complicated and I barely have any useful data stored.

If nothing works I would rather find something useful for XP to do than to risk losing my Lucid install.

---

### Post by Hippytaff on 2010-11-20
If thats the case, then save everything and do a fresh install :-)

---

### Post by beew on 2010-11-20
> **Hippytaff said:**
> If thats the case, then save everything and do a fresh install :-)

Why do you keep telling me to do a fresh install???I have explained already I don't want to do a fresh install. :confused:

---

### Post by Hippytaff on 2010-11-20
> **beew said:**
> Why do you keep telling me to do a fresh install???I have explained already I don't want to do a fresh install. :confused:

Sorry man :-) don't do a fresh install whatever you do :-D

---

### Post by RJ12 on 2010-11-20
Do you have better luck if you try Disk Utility? Sometimes that has happened to me and it usually works in Disk Utility.

Hope it helps :)

---

### Post by beew on 2010-11-21
> **RJ12 said:**
> Do you have better luck if you try Disk Utility? Sometimes that has happened to me and it usually works in Disk Utility.

Hope it helps :)


Tried that already. SMART status is "there are a few bad sectors". SMART test returned some outlandish output (like hundreds of bad sectors) which I have posted on the forum sometimes ago for advice, the verdict was that there was something wrong with the SMART test because there was no way the computer would still run  if the report was true. I tried to link to the post but couldn't find it.
That was a few months back and the computer is still running!

---

### Post by beew on 2010-11-21
Hello anyone??


But please don't tell me to do a fresh install. :)

---

### Post by Hippytaff on 2010-11-21
Are you sure you don't want to do a fresh install? :-D (Joke)

Looks like nothing is working for you, I don't know what else to suggest

---

### Post by beew on 2010-11-21
Oh no, here comes the smiling hippy dude again. :)

---

### Post by farsight on 2010-11-22
I know it isn't exactly the fix desired, but I guess the other option is to shrink the window's partition within windows using the disk manager. Another option to essentially ignore windows would be to delete its MBR, however given the number of Q.Q 's I see on here about MBR's going crazy, I'd steer clear unless you are pro ;)

---

