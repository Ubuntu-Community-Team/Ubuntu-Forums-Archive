---
title: "can't boot from live cd... busybox?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by yolsl on 2009-01-29
Desktop computer, AMD64 Athlon 2.4Ghz, 2GB ddr2 ram, 300GB Toshiba HDD, ran Ubuntu no problem til I formatted my drive by mistake while using a partitioning program, I installed Ubuntu via the wubi.exe before, I just used a Windows application called PowerISO and extracted the .iso file available for download at ubuntu.com

Now I don't have Windows (or any operating system), no problem, but I'm trying to use the live cd to install ubuntu and every time I do it just goes to a black screen with white writing, apparently what I'm looking at is a busybox. I've searched for it and know what it is, but not really sure why it's coming up, or what I have to do from the busybox screen to actually install Ubuntu. Anyone know what's going on?

---

### Post by sanderj on 2009-01-29
Are you trying ubuntu 8.04? If so, have you tried ubuntu 8.10?

Have you tried the Safe Graphics boot options (I believe second option from the boot menu)?

---

### Post by stalkingwolf on 2009-01-29
First I would make sure that the CD and the rom are clean.  This has caused
me untold hours of frustration.  Most manufacturers suggest cleaning every 8 - 10 hours of use.

Then check to make sure your disk is not corrupted.  you may need to
redownload or reburn your ISO.  I have the best luck burning at 4x or lower.

I have had trouble with win installs when I partition and format with
gparted.  So I use Maxblast for them, great if you use a maxtor/seagate
drive.

if this is a wubi iso you are using, it might not work as a stand alone.

---

### Post by Nell on 2009-01-29
Which live cd are you using?Have you try to check cd for defects...
I've downloaded and burnt 4 corrupted cds before I get a working installation disc.
I'm using AMD64 Athlon too, but I don't know why the distro that works on my installation is the one that ends with "i386" instead of "amd64" :?
And also like Stalkingwolf mentioned..try to burn it with the lowest rate.

---

### Post by yolsl on 2009-01-29
While I'm not entirely sure what burning at a slower rate would have to do with the success of the install, I suppose I'll go back and try it again. I think I have a 24x drive, and I was using PowerIso with the burn speed set to "auto", so I don't really know what state the cd was in..

---

### Post by XanTrax on 2009-01-29
The alternate text installer has never failed for me before.  I know this sounds stupid but I have defintely seen different results of my installation when using the liveCD and the text installer.

---

### Post by GMachine_24 on 2009-01-29
I had this exact problem installing 8.04 last week and it drove me completely insane as all 'answers' to problems posted re: this busybox thing did not work . . . although I realize people were trying to be helpful 

From my experience, the problem is with the formatting and partitioning on your hard drive. This was my problem. I finally did a DOD wipe (only 3x) of the entire hard drive, which overwrote all data, killed all the partitions and formatting, etc. Then, when I attempted another install from one of the Ubuntu 8.04 CDs I had created (I burned several copies, thinking the CD might be the problem, to no avail), everything went fine. Doing this will also allow you to boot "live" to Ubuntu 8.04 if that is what you want.

You can download the dban program from here:

[http://www.dban.org/](http://www.dban.org/)

It is easy to use and reliable. You will create a boot disk from a download and then choose which option you want to wipe your drive clean - I go for the short DOD wipe (the full DOD-standard wipe is 7x overwriting and can take forever).

Believe me when I tell you this is your problem and how to correct it. I wasted hours trying all these other suggestions.

--gm

---

### Post by dwel on 2009-01-29
i 'bought' ubuntu at the barnes and noble up the road from me. i have seriously seriously wanted to give linux a try. ive worked alot lately so i just assumed by it, for it came with a 45,000 page, how could i possibly mess it up, manual. 

to make a reeally long story tollerable.... 

ive got a core2duo, biostar mobo, wd800 hdd, sony dvd.

i get the 'abnormal exit' when i try to run the ubuntu livedvd.

after scores[no joke] of attempts[ubuntu] i dug up a copy of saybayon that id almost forgot that i burned last year. so i started goofin around[like i always do] and i got sayboyon livecd minied 3.4 to boot into the gui[ONCE and only ONCE].

now it gives errors as well as ubuntu's errors. ive read the forums, tried the boot params, cussed, swaped hard drives and cd drives and cables and video cards and power cords i even bought a coke instead of a pepsi and absomuthafrigglutely nothing i do or yell works.

> **GMachine_24 said:**
> I had this exact problem ......


--gm

i even zeroed out the drive. thrice.

any suggestions?

---

### Post by yolsl on 2009-01-30
GMachine_24, I'd format the drive but ... I don't really know how. There's no MS-DOS, and I can't really download/use a file on that drive because it has no operating system, it's just a blank drive.

-goes to try the text based installer

---

### Post by GMachine_24 on 2009-01-30
Hi. Perhaps I wasn't clear. You obviously can't download a file to the drive that doesn't work - I'm assuming you have another computer that you can use to download the dban software, burn it to a CD and then use it to boot the computer that you want to install Linux/Ubuntu on.

You can also try software from one of the hard drive manufacturers - Seagate, Western Digital, Hitachi, etc. - because they usually include formatting and partitioning software with a new hard drive. You can also download software from their Web site which allows you to do the same - you have to burn it to a CD to get it to work and boot from that.

If you download and burn the dban software to a CD, you then move the CD to the CD drive of the computer where you want to install Linux. Boot your computer from that CD and you will be given a screen with various options to overwrite your hard drive - as I mentioned earlier, I usually choose the quick DOD overwrite - unless I am selling a used hard drive in which case I choose the full DOD standard 7x overwrite.

If you can download the dban software and burn it to a CD and use it to boot your computer and wipe the hard drive - if you try this and cannot figure out what to do or how, post again and I will respond.

-gm

---

### Post by GMachine_24 on 2009-01-30
Hi. This is a message for dwel.

The problem yoisi is having is a specific problem that - if I am correct - ends you up at a command prompt below the following lines on your screen


```


(initramfs)

BusyBox v.1.10.2 (Ubuntu 1:1.10.2-1ubuntu6)
built in shell (ash)

Enter 'help' for a list of built-in commands.


```


The initramfs refers to the initial ram file system (which replaced initrd or initial ramdisk) as the file system used by the Linux kernel during system boot. There is more information about this here:

[http://en.wikipedia.org/wiki/Initrd](http://en.wikipedia.org/wiki/Initrd)

Unless you get the specific error cited above, the steps I suggested weren't meant for you.

Re: the hardware configuration you list . . . is this a system you had up and running before as a Windows box? In other words, do you have a configuration that you know is good - because I know what it's like to try to find a hardware problem, especially if more than one piece of hardware is bad.

What version of Ubuntu are you installing and is it 32-bit or 64-bit?

There are probably more questions but perhaps this will give us a place to start.

---

### Post by LowSky on 2009-01-30
How to solve this issue
1. use bootable usb
2. Switch the cable for the disc drive. Most people who have this issue have built their own PC and the use the wrong IDE cable. Ubuntu Has some odd issue which messes up people who use cables meant for IDE33/66, So simple fix is use the correct cable.

Use a 80 Pin cable over an 40 pin cable, you can tell the difference by the smothness of the ribbon cable 80 is much smoother then a 40 pin cable.

---

### Post by yolsl on 2009-01-31
(after burning the dban cd as instructed) >.>

Okay, Ubuntu did install correctly after minor preparations...

I used dban which worked, but, after using it I tried booting from the cd again and it still didn't work -_- I tried the text based installer (after realizing that the file was called "alternate-amd64.iso" instead of having 'text based installer' or something similar) and it worked up until it had to install the file, to which the installer told me it couldn't read the file from the cd and to check the validity of my cd-rom drive.

I pulled out my cd-rom and put in a drive from another computer, tried booting from the exact same cd only with the new cd-rom drive and everything worked fine, so I figure the cd-rom was actually the problem. I'm not entirely sure what happened about the Busybox ... thing. But I didn't encounter it after doing this. I'm still curious about finding an 'actual' solution to it since a few people I know are telling me the same thing happened to them, I've told them about what I did though and haven't heard back.

I was installing version 8.04, and yeah the 64 bit. The drive previously had windows xp media center edition on it but I removed all the info on my C drive by mistake leaving the computer unable to start so I tried to install Ubuntu, encountered this busybox and posted... suppose I should've been more specific with my story.

---

### Post by GMachine_24 on 2009-02-01
It seems you had two problems - always much tougher to solve than a single problem.

As I mentioned, I had the "busybox" problem when I installed Ubuntu 8.04 to a computer with a hard drive that had been previously used in a Windows system as a back up - and using the dban software to wipe the drive clean and remove all formatting and partition information was the only thing that worked for me.

Undoubtedly there are other utilities that will accomplish the same thing - and it seems Ubuntu should be able to install on a drive, even if it's a used one. There are choices during set up that allow you to reformat the entire drive, or just part of it, . . . but for some reason Ubuntu hangs during the initial boot and kicks you out to a command line.

If you have a bad CD or CD-ROM that will drive you crazy and, as you found, the only solution is to replace the one that is bad.

---

### Post by dwel on 2009-02-02
GMachine_24,

i believe it was [1476]error 
i did , however, successfully install sabayon 3.5.1 on that computer finally.
any reason as to why ubuntu wont?

---

### Post by GMachine_24 on 2009-05-14
Dwel:

Sorry to take so long to reply - you probably won't see this. But, anyway, I don't know what the specific problem might be with Ubuntu - if it is even that. It might be a combination of a hard drive and software problem - although, typically, it's been my experience that 90 percent of the time a problem has to do with software . . . hardware mostly works ok in my experience.

GM

---

### Post by dwel on 2010-04-28
> **GMachine_24 said:**
> Dwel:

Sorry to take so long to reply - you probably won't see this. But, anyway, I don't know what the specific problem might be with Ubuntu - if it is even that. It might be a combination of a hard drive and software problem - although, typically, it's been my experience that 90 percent of the time a problem has to do with software . . . hardware mostly works ok in my experience.

GM


I finally got Ubuntu studio 9.10 running.

---

### Post by GMachine_24 on 2010-08-29
Great to hear.

Hope it didn't take you until this past Spring!!

---

