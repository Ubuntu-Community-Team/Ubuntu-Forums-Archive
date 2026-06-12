---
title: "Cannot install Kubuntu"
date: 2009-07-22
forum: New to Ubuntu
---

### Post by mytorciar on 2009-07-22
Hi,
I am a Linux noob. Over the years I have been trying to use Ubuntu on a dual boot with XP and after a while had to get rid of it.

Yesterday I tried the Live CD of Kububtu9.04 and liked it, so i decided to use Wubi to install Kubuntu inside windows xp. The installation went on smoothly till it asked for a reboot. On reboot the splash screen came up for some time, then a display of the cursor as a BIG X and a window showing that it was installing - the message inside the box was that it was trying to format the /host disk for making a swap file. This was endlessly shown, with the progress remaining at 0%. This went on for quite some time and I had to hard boot the machine. 

Same thing went on the next time for many minutes and I gave up for i did not want to fiddle around and lose data.

System Info:

C:/ fat32 - where I was trying to install thru wubi - free space around 6 GB.
D:/ NTFS - where XP2 pro SP2 is installed.
E:/Fat32
I:/ntfs - Windows programs are installed.

Ram 1GB, HDD 160GB, DVD-ROM etc. Onboard video - no separate card. Monitor LCD AOC 617SW.

This is after when i had failed to install UBUNTU 9.04 thru Wubi. After install it would just give a blank screen. I read somewhere that KUBUNTU might be better because of KDE. I had searched for the solution but could not get it on the Net.

Do I give up on Ubuntu / Kubuntu or is there some way I can progress.

Thanks.
Mytor

---

### Post by perito on 2009-07-22
try installing it without wubi? Put the live CD and install Kubuntu?

---

### Post by Nburnes on 2009-07-22
Download the iso for Kubuntu, then put it in the same folder or on your desktop next to Wubi Installer, then run Wubi and it should install just fine.

Mine used to stay stuck at 0% also until I read the Wubi wiki and it said it was easier to do it this way.

Or if you have the Live CD with you just load it into Windows and run Wubi off of that.

Edit: NVM I'm dumb, need to learn how to read next time :(

---

### Post by mytorciar on 2009-07-22
> **perito said:**
> try installing it without wubi? Put the live CD and install Kubuntu?
thanks. but i don't want to do a full install at the moment. still in the trying stage!!

---

### Post by mytorciar on 2009-07-22
thanks. i will try putting the iso and wubi together today.
2) is there any way to save the settings on the hard disk if u r running the live cd or each time you use the live cd you have to do the settings again - this would be really tedious. Especially if one wants to try programs and paly around?
Sure will appreciate the help.

---

### Post by dk06 on 2009-07-22
Tutorial:

[http://www.youtube.com/watch?v=nzb8EGhfLiM](http://www.youtube.com/watch?v=nzb8EGhfLiM)

Be sure to read the instructions too

---

### Post by mytorciar on 2009-07-23
> **dk06 said:**
> Tutorial:

[http://www.youtube.com/watch?v=nzb8EGhfLiM](http://www.youtube.com/watch?v=nzb8EGhfLiM)

Be sure to read the instructions too

I saw the video. Thank you. But the video is nothing too great. all the instructions were followed. After the first install reboot the computer just sits there with the hard disk swap file creation as 0%.

I cant make out what to do next.
Anyway thanks.

---

### Post by dk06 on 2009-07-24
> **mytorciar said:**
> I saw the video. Thank you. But the video is nothing too great. all the instructions were followed. After the first install reboot the computer just sits there with the hard disk swap file creation as 0%.

I cant make out what to do next.
Anyway thanks.


[B]
Maybe you have a bad ISO
or 
Maybe Wubi only works with Ubuntu <---not sure, you may want to google it


If it were me in your situation, I would re-download the ISO image
or 
Get Ubuntu instead
[/B] 
[B][U]
Step 1[/U][/B]
[B]
Get the Firefox Add-On called DownThemAll[/B]
[https://addons.mozilla.org/en-US/firefox/addon/201](https://addons.mozilla.org/en-US/firefox/addon/201)

[B]
_Step 2_[/B]
[B]
Re-Download [/B]the Kubuntu ISO
[B]
USE The DownThemAll Firefox Add-On to download it[/B]
[http://www.kubuntu.org/getkubuntu/download](http://www.kubuntu.org/getkubuntu/download)
&[B]
Check the MD5(using the DownThemAll Add-On)[/B] <---This will verify the integrity of the ISO
(you can put the md5 checksum in at the same time you download it)

_MD5s:_  [http://cdimage.ubuntu.com/](http://cdimage.ubuntu.com/)
(make sure the checksum (MD5) your using to check is same version of kubuntu as the iso you are downloading)

Now you should have a good ISO to install with

---

### Post by bubsy100 on 2009-08-04
Dear all ,
 
i have the same problem with installing kubuntu inside windows 
although i have the original live cd ( received it from shipping service )
 
please can any body help us ?
 
2 - is the swap partition means that , it will be format all my hard disk and 
  lost  all Data on HD ??
 
be note that I had installed ubuntu on my pc and run in good 
 
please find help for us

---

### Post by Clorow on 2009-08-04
If it's formatting /host for swap, **that's your Windows installation! Don't format it!**

You might want to go into advanced partition mode for the installation, and create a partition for / and a partition for swap yourself. But be careful, as any partitioning tool can be a weapon of mass destruction if you're not careful.

---

### Post by bubsy100 on 2009-08-04
THANK U FOR REPLY 
 
that mean i will not lost any data on my hard disk ? formationg host swap only not 
any other partion of HD  ?????
 
please help me about installing problem ?

---

