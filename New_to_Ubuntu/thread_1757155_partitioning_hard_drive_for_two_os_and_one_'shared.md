---
title: "partitioning hard drive for two os and one 'shared drive'"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by shin333 on 2011-05-13
Hi, I'm completely new to ubuntu but I'm loving how quick it is and want to try to move over from my vista. Right now, I'm trying to partition my hard drive. One for Ubuntu and one for vista since I have it on dual boot. (ubuntu is installed in Vista with about 15gigs). I want to have one drive for ubuntu, one for vista, and one for my files. I'm hoping the third drive (the one that has all my files) can be shared between the two os? I did a search for this topic but all the ones that I found seem to be dated too far back so I'm not sure if the advice is still good. 

Also, I want to move over to Ubuntu eventually since I only use my computer for watching movies, writing documents, playing old computers games and football manager (game's addictive) and from what I can tell. I might have to keep vista just for my game addiction. 

If anyone knows how to partition the hard drive that would be great. I'm completely new to partitioning so go easy on me. Thanks alot

---

### Post by coffeecat on 2011-05-13
First of all, here's a useful link for you:

[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

Follow all the links in it - you will learn a lot. :)

My suggestion for your situation and your described needs: Assuming that Vista is on the first partition, sda1, create a second primary partition, sda2, formatted NTFS. This will be for your shared files. Vista will see it as D: or E: or whatever and you will be able to access it read/write in Ubuntu from the Places menu, or you can arrange to have this partition mounted on bootup.

Then create one extended partition for everything else. This will be sda3 and you can create as many logical partitions as you wish in it. Linux, unlike Windows, can boot from a logical partition. As a minimum, you need a swap partition and your Ubuntu root partition formatted ext3 or ext4. With a separate data partition you probably don't need a separate home partition, but others may have different ideas.

I haven't given any figures for sizes. If you tell us what size your HD is and what the current size of the Vista partition is, we can go into detail.

---

### Post by shin333 on 2011-05-13
I have 286gigs partitioned for vista. about 100 gigs free within that 286 gigs so far (I have absolutely no idea what's taking up the rest of the space!) and also got a 11.6 gig drive from HP for HP recover (I'm using a HP laptop.) I'm trying to slowly migrate over to Ubuntu but i know that it's a learning process so I'm just dual booting for now until i'm completely comfortable.

---

### Post by pSYcl0Ne on 2011-05-13
I suggest you go with what the other post above recommends, but stick to having a /home partition also. it's really handy if something goes wrong and you need to reinstall.


_My Vision:_
Keep Vista as is
Partition the hundred into about 10 or 15gb /
/swap = APPROX whatever your RAM is (i have equal to 5gb /swap to 2gb Ram0
/home about 20 - 40
and an ntfs/fat for sharing between. 

thats just how would maybe do it anyway (well actually Vista would be long gone for me *lol)- there's some good stuff to read about partitioning preferences all over the place- it's all up to you. Just try to plan ahead for if anything goes wrong so you minimize loss of data you'd rather keep.

A hundred people will tell you a hundred different things. Just plan it out to keep your stuff safe.

---

### Post by coffeecat on 2011-05-13
> **shin333 said:**
> I have 286gigs partitioned for vista. about 100 gigs free within that 286 gigs so far (I have absolutely no idea what's taking up the rest of the space!) and also got a 11.6 gig drive from HP for HP recover (I'm using a HP laptop.) I'm trying to slowly migrate over to Ubuntu but i know that it's a learning process so I'm just dual booting for now until i'm completely comfortable.

It's sounds as though you have a 320 GB drive with two partitions and you would need to shrink the main Vista partition to make room for other partitions. (Your "gigs" are probably GiB - Gibibytes. 320 GB - gigabytes -  are the same as 298 GiB.) However, since you've used up about 180 GiB, the filesystem is likely to be fragmented and difficult to shrink.

First thing. Boot up an Ubuntu live CD and choose "try Ubuntu". If you run the latest 11.04 CD and get the Unity desktop (dock-like launcher on the left), tap the Windows key, type "gparted" and open Gparted from the Applications section of the dash (the black thing). If, however, you get a classic Ubuntu desktop (Applications - Places - System menu at the top) when you boot up, open Gparted from System > Administration. Once Gparted has opened, take a window screenshot by pressing the Print/SyReq key with the AltGr key and post the screenshot. That's a way of seeing what your partition layout is like now.

Second - if you have not done so yet, **make a set of recovery DVDs **from a utility which HP should have included in your Vista install. You will be editing partitions. Things can go wrong. If you lose your HP recovery partition you have lost the ability to restore Windows if you don't have recovery DVDs.

Third - have a look at this link:

[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

Pay particular attention to what it says about Gparted sometimes making Vista unbootable if you use Gparted to shrink the Vista partition. It's far preferable to use Vista's disk management but in your situation it might not allow you to shrink the partition by much unless you follow some of the measures there. Also - with about 180GiB used in your C: partition, that must be a lot of personal files. Ideally they would be better on a separate NTFS data partition as I described earlier, but that means backing them up to an external storage medium. Do you have backups?

---

### Post by shin333 on 2011-05-14
I'll work on the recovery DVDs. Sounds like a good plan. of the 180 GB, probably about 40 is music and 20 is downloaded stuff. I'm trying to find someone with a external harddrive so that I can move stuff over before attempting partitioning. Right now I actually wouldn't even mind reinstalling a fresh windows vista (never tried windows 7 so don't know if its good or if my computer can handle it well). But I know I want both windows and ubuntu for now. I'll work on posting screenshots like you asked. Not infront of the laptop right now.

Also, separate note, since I'm new to linux I heard that ubuntu 10.10 is easier and more stable than the newer ubuntu version. Not sure if I should stick with the stable old version or try the new version. Any advice? (Remember, I'm a linux virgin)

---

### Post by coffeecat on 2011-05-14
> **shin333 said:**
> Also, separate note, since I'm new to linux I heard that ubuntu 10.10 is easier and more stable than the newer ubuntu version. Not sure if I should stick with the stable old version or try the new version. Any advice? (Remember, I'm a linux virgin)

10.10 uses the classic gnome desktop which is familiar to most on this forum. The newer 11.04 defaults to the new Unity desktop (if you have 3d-capable graphics card/driver combination), although you can choose classic gnome on the login screen. It's the change that's upsetting some, and the upset ones tend to be more voluble. :) Don't believe everything you read, and that includes my post! :p

All I can say is that after a short learning period, I found that I preferred the new Unity desktop and it's been every bit as stable for me on four different machines as the older 10.10 release.

I suggest you burn CDs of both the 10.10 and 11.04 ISOs and try running both live to see how you get on. One point to remember is that with some graphics cards, the 11.04 live CD will default to classic gnome. This is particularly so with nvidia graphics which need the proprietary driver (or an experimental package) installing before you can get Unity.

Here are a couple of links to help you find your way around Unity:

[http://omgubuntu.co.uk/natty/](http://omgubuntu.co.uk/natty/)

[http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity](http://castrojo.tumblr.com/post/4795149014/the-power-users-guide-to-unity)

---

### Post by YesWeCan on 2011-05-14
> **shin333 said:**
> Hi, I'm completely new to ubuntu 
Welcome.
Linux is excellent and will give you back control of your computer. Linux doesn't hold your hand like Windows so you need to be a little more careful about what you do.

A couple of things not mentioned yet. I think a defrag may enable Vista to shrink itself further. I'd use Vista to shrink not linux. Also, you need to be aware of Grub issues (Grub is the name for the linux bootloader + MBR replacement) with Vista. Windows 7 (which is MUCH better than Vista) is tolerant, mostly, of the Grub MBR but Vista can get upset during some upgrades and it may rewrite the MBR and then you wont be able to boot Ubuntu.

It isnt well publicized in here but you dont have to use Grub to boot Ubuntu. You can use your existing Vista bootloader. This prevents update problems. Somewhere in the Ubuntu install there is an advanced option to choose where to install Grub: do not choose MBR. Then boot Vista and download EasyBCD (free) and run it to add Ubuntu to your Vista boot menu. This is what I would do to keep Vista happy with your scenario.

I would prefer separate Hard drives and then Grub can go on a different HD from Vista. The important thing is not to install Grub on the Vista HD. Or you can install just Grub to any old HD or even a USB stick. Grub will boot both Ubuntu and Vista no matter where it is located.

Note also that that older web pages may refer to an older Grub (Grub legacy) and not the new Grub2. Both are called Grub which is a real dumb move; the new one, which is very different, should have been renamed to avoid confusion. Probably you should avoid tutorials more than a year old.

---

### Post by shin333 on 2011-05-14
I'm actually going to delete Ubuntu and reinstall it. I had it run off of Windows instead of making Ubuntu dual boot by using a liveCD. I'm also thinking of reinstalling windows which would be a pain but something i'm considering so that I have a brand new computer to work with. I'm actually moving all my important files to an external drive. Hopefully nothing will screw up. I love the inform so far. Lots of feedback in such a short time. that's awesome. I'll be able to apply all these changes after I have a new vista and ubuntu installed.

---

### Post by YesWeCan on 2011-05-14
Note that you need to install Vista first. Vista has to be the first OS on a HD or it will complain.

BTW, regarding Grub on a USB stick, the easiest way to set this up is simply to install Ubuntu to a USB stick. You need a 3 or 4GB stick. You can do this using the live CD using "System/Admin/Startup disk creator". Make sure you give it 100MB or more persistent storage area.
This gives you a bootable USB stick with grub on it. Just boot Ubuntu on the USB and in a terminal type 'sudo update-grub' and this will add selections for your Vista and HD Ubuntu to the USB Grub menu.

You can set up the bios to boot from USB first, then the HD. When the USB is there you will see the Grub menu with entries for Vista, HD Ubuntu and USB Ubuntu. When the USB stick is not there, Vista will boot.

I don't know how old your PC is (a laptop I presume?) so check that its bios can boot off USB.


So you have 3 choices now according to me:
1) Install Grub on HD MBR and deal with any Vista issues if they arise
2) Don't install Grub on MBR and instead add Ubuntu to Vista's bootloader
3) Don't install Grub to HD MBR and instead boot using a USB stick.

Enjoy :)

---

### Post by shin333 on 2011-05-15
so i'm trying to partition my harddrive with windows disk management in windows vista. I did a fresh install of vista and haven't installed ubuntu yet. I was going to install ubuntu after I partitioned my hard drive. I'm having trouble partitining. I have 293288 in MB before shrinking and have 91 percent of free space but apparently I can only shrink 176 MB. I have followed all the instruction on how to partition the hard drive on windows following this website: 
[https://help.ubuntu.com/community/HowtoResizeWindowsPartitions](https://help.ubuntu.com/community/HowtoResizeWindowsPartitions)

I also went to 
[http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/](http://www.howtogeek.com/howto/windows-vista/working-around-windows-vistas-shrink-volume-inadequacy-problems/)

I'm using perfectdisk to defrag my harddrive. I've defragged twice but I'm still not able to partition properly. 
The only step I couldn't follow on that site was I couldn't delete pagefile.sys in C: (probably cuz I just installed a fresh vista and it hasn't been saved yet) 

Any help would be great.

---

### Post by shin333 on 2011-05-15
Also, I'm looking into using my ubuntu CB and using Gparted to resize my partition but the problem is I don't have a windows vista CD. (I don't know how to make one and the only thing I have is the recovery drive that is partitioned seperately on my computer that I used to install a new fresh Vista) any advice on that?

---

### Post by shin333 on 2011-05-15
I managed to get all my partitioning done today. Thanks guys! Now if only I can get this wireless problem solved.......

---

