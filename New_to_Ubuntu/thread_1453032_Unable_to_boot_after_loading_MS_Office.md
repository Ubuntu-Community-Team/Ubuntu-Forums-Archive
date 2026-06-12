---
title: "Unable to boot after loading MS Office"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by electeng33 on 2010-04-12
I have just successfully loaded Ubuntu, dual booting with WindowsXP.  It booted properly.   I then loaded MS Office on to WinXP and now find that I cannot open Ubuntu.   With Windows I would reload the programme, but I am unsure whether this is the best approach with Ubuntu .    Is there anyone able to advise me please.

---

### Post by sydbat on 2010-04-12
> **electeng33 said:**
> I have just successfully loaded Ubuntu, dual booting with WindowsXP.  It booted properly.   I then loaded MS Office on to WinXP and now find that I cannot open Ubuntu.   With Windows I would reload the programme, but I am unsure whether this is the best approach with Ubuntu .    Is there anyone able to advise me please.How have you installed Ubuntu? Via wubi* or in it's own, separate partition?

*wubi installs Ubuntu like it is a program for Windows.

---

### Post by electeng33 on 2010-04-13
I loaded Ubuntu from a boot/installation disc (£! plus postage) and after taking advantage of its facility for viewing its operation etc. I clicked on 'install' and followed the instructions.   There was only one option for dual boot and it did not tell me where it was placing Ubuntu.   

I have since tried to find, using WinXP explorer, where Ubuntu is stored, but it seems to be invisible - I suppose this is because of a different filing mechanism.   However I assumed that the disc had placed it on a different partition of the hard drive from the Windows operating system, as in the Ubuntu details I have read that the two systems should be kept on different drives.    I loaded MS office on the same drive as WinXP.

Another factor which I omitted to mention on my query, which may have some significance, is that on trying to boot Ubuntu I get the small motif in the centre of the screen.   After a short time that disappears then the screen goes completely black,  then two line of code appear at the top but within a second or two they disappear and the screen then remains completely black.   I have to switch off the computer manually. to start again, and can boot WinXp quite normally

I hope this has given the additional information you need, but if there is anything else, please advise.

Thanks for your interest.

---

### Post by electeng33 on 2010-04-14
> **sydbat said:**
> How have you installed Ubuntu? Via wubi* or in it's own, separate partition?

*wubi installs Ubuntu like it is a program for Windows.


Many thanks for your response.   

I loaded Ubuntu  from a boot/installation disc (£! plus postage) and after taking  advantage of its facility for viewing its operation etc. I clicked on  'install' and followed the instructions.   There was only one option for  dual boot and it did not tell me where it was placing Ubuntu.   

I have since tried to find, using WinXP explorer, where Ubuntu is  stored, but it seems to be invisible - I suppose this is because of a  different filing mechanism.   However I assumed that the disc had placed  it on a different partition of the hard drive from the Windows  operating system, as in the Ubuntu details I have read that the two  systems should be kept on different drives.    I loaded MS office on the  same drive as WinXP.

Another factor which I omitted to mention on my query, which may have  some significance, is that on trying to boot Ubuntu I get the small  motif in the centre of the screen.   After a short time that disappears  then the screen goes completely black,  then two line of code appear at  the top but within a second or two they disappear and the screen then  remains completely black.   I have to switch off the computer manually.  to start again, and can boot WinXp quite normally

I hope this has given the additional information you need to be able to advise me, but if there  is anything else, please advise.

Thanks for your interest.

---

### Post by coffeecat on 2010-04-14
> **electeng33 said:**
> Another factor which I omitted to mention on my query, which may have  some significance, is that on trying to boot Ubuntu I get the small  motif in the centre of the screen.   After a short time that disappears  then the screen goes completely black,  then two line of code appear at  the top but within a second or two they disappear and the screen then  remains completely black.   I have to switch off the computer manually.  to start again, and can boot WinXp quite normally

Hi. Sorry that you're having an unfortunate introduction to Ubuntu.

First thing. That won't have been caused by installing MS Office on Windows. I'm prepared to blame Microsoft for a lot of things, but not that! :wink: What you describe is likely to be a failure of the xserver, the underpinnings of the GUI desktop. The small motif (a white Ubuntu logo on a black background. Am I correct?) is generated on screen before the xserver starts up. After the xserver does start, what you should see is the login screen. The two lines of code are probably some error messages. The commonest cause of an xserver failure is a proprietary video driver.

Question: did you do an update in Ubuntu the last time you used it before this happened? And, in particular, did you install a proprietary video driver through System > Administration > Hardware drivers? Also: what is your video device? (My guess - ATI. :p)

---

### Post by electeng33 on 2010-04-15
Thanks 'Coffeecat' for your response.   Yes, I do get the small white motif in the centre of the screen with a black background.   Then after some delay the two lines of text flash on the screen and disappear.   After that the screen remains black.

I may have upgraded in Ubuntu (I must be more careful to log these events) at Ubuntu's invitation - I do remember receiving an invitation.   However I did not attempt any video driver installation in Ubuntu.

I did install a video controller driver which WinXP's wizard found, before I installed  Ubuntu, but cannot see it listed in WinXP device manager.    In device manager the only reference to 'video' is 'Sound, Video and Game Controllers' and the only sub-headings containing 'video' are 'Legacy Video Capture  Devices' and 'Video Codecs'.

I hope these details will throw more light on my problem and help its solution.   I expect the references to WinXP are irrelevant, but if I need to provide more details in any respect do please let me know.

From what I have seen of Ubuntu so far, I really do want to sort this problem and get away from the dependence on the Microsoft commercial machine - so I will be most grateful for any further advice you can offer.

---

### Post by m4tic on 2010-04-15
I would suggest you reinstall ubuntu again so you understand where what is. I typically select the custom disk partitioning option on the install wizard. This way you can have more control on how your disk is used. So you can start again fresh, this time i'm positive you'll be more observant

---

### Post by coffeecat on 2010-04-15
You haven't told us the make and model of your graphics card. This may not be the cause of your problem, but I still think it the most likely, and we need to know details to do some trouble-shooting. If you don't know what the card is, let's do some detective work.

In Windows XP: open a 'My Computer' window. Right-click on the little icon of a computer at top left of the window and choose 'Properties'. Click on the Hardware tab of the System Properties window and then click on the 'Device manager' button. In the Device Manager window, click on the '+' to the left of 'Display Adapters'. The name of your card chipset should now be visible. Post this. Double-click on the device name that dropped down and a Properties window should open. Post any further details that seems relevant.

But it's easier in Ubuntu! :p Personally, I'd prefer to see the information that appears with the following. Boot up with your live Ubuntu CD. Once you are in the desktop, open a terminal (Applications > Accessories), and try this command:

```
lspci | grep -i vga
```... and post the output. If you get nothing, try...

```
lspci
```... and look for a line that refers to your video controller. (I'm hoping that all video card lines in lspci contain the string 'VGA' or 'vga' but you can't trust all manufacturers.)

Lastly, even though you think you didn't install a proprietary video driver, let's be sure it didn't get installed somehow. (I'm still putting money on an ATI card and the proprietary fglrx driver.) Although you can do this from the live CD, the way I suggest is a little more straightforward. Shutdown from the live CD and reboot the computer without the CD. At the grub menu, choose Ubuntu, but what is probably the second choice: "recovery mode". Don't be alarmed by the scrolling text. When you get to a simple menu, choose 'root console without networking' (or words to that effect.)

When you get a simple console prompt (#) type the following command:

```
ls /etc/X11
```Does it include a file called xorg.conf? (If you get an error, you've made a typo - that's capital-X, eleven.) If you can see xorg.conf, try:

```
cat /etc/X11/xorg.conf
```Look for a line that says 'Section "Device" '. A few lines below this will be a line that says 'Driver "*somethingorother*" '. What is *somethingorother*? If all you get is a series of lines that start with a # character, then please say that's what you get.

Once you've made a note of what you've found, you can reboot the machine with:

```
reboot
```

Who said Linux is not intuitive? :wink:

---

### Post by Merk42 on 2010-04-15
Is there a listing for Ubuntu under Add/Remove Programs?

This will tell us whether you installed via WUBI or to its own partition.

---

### Post by electeng33 on 2010-04-21
Thanks m4tic for your suggestion, I had thought that I might be forced to do that because that is what I would have done in case of anything similar with Windows.   I have had several other responses to my query from which I hope that there may be a more direct and also more instructional way of solving the difficulty.   I will follow these through first in the hope of avoiding re-installation.

Regards

---

### Post by electeng33 on 2010-04-21
Many thanks coffeecat for your detailed guidance which I found most helpful.

_Using WinXP_     Clicking on Display Adaptors - Intel(R) 82845G/GL/PE/GV
                       The properties window indicated 'working satisfacgtorily' and 'enabled'.   
                       By selecting  other tabs, various lines of information were revealed which                               unfortunately meant nothing to me. 

_Using live Ubuntu CD_

---

### Post by electeng33 on 2010-04-21
Sorry, pressed the wrong key, but to continue with reply:-

_Using live Ubuntu CD_
                    Command lspci | grep -i vga got the result - 00:02 vga compatible controller: Intel Corporation 82845G/GL.[Brookdale-G]GE Chipset Integrated Graphics Device (rev03)

_Using Ubuntu - recovery mode._
                    Inserting command ls/etc/X11  did not give a line containing a file xorg.conf

                    What was given was:-

x          xsession       xsession.options   xwrapper.config   cursors                          rgb.txt
            xresources   xsession.d            app-defaults        default-display manager  programmes

x.int
xkb
                 (in the above I may have incorrectly spelt 'programmes' the English way - but I did not think it was significant enough for me to re-check)

Although I did not understand much of what I was doing regarding the Ubuntu checks, I found it an interesting introduction, and I thank you again for your time spent in sending me such detailed guidance.

Regards.

---

### Post by electeng33 on 2010-04-21
Thank you mark42 for your interest 

In answer to your query, there is no listing for Ubuntu in WinXP Add/Remove programmes.   You will have noted that I have not been able to see Ubuntu in any file partition using WinXP but I suppose that it will be possible using my Ubuntu disc to find where it is located on my hard drive.

If you need any further details that I can give to enable you to suggest a solution to my problem, please let me know.

Regards

---

### Post by coffeecat on 2010-04-21
> **electeng33 said:**
> _Using WinXP_     Clicking on Display Adaptors - Intel(R) 82845G/GL/PE/GV

> **electeng33 said:**
> _Using live Ubuntu CD_
                    Command lspci | grep -i vga got the result - 00:02 vga compatible controller: Intel Corporation 82845G/GL.[Brookdale-G]GE Chipset Integrated Graphics Device (rev03)

Well - at least Windows and Ubuntu agree.

First - you won't have an /etc/X11/xorg.conf file. That's OK. You won't need one with that Intel video chip which uses the Intel open-sourced driver. You only need an xorg.conf file when using the proprietary driver for nvidia or ATI cards or in certain special cases. My intuition about an ATI card was wrong.

Anyway, the Intel 845G video chipset used to be good enough (albeit a bit sluggish - I used to use one) and well supported, but I've seen threads lately where people were having problems with it. It's getting to be very old now, and as with much older hardware, driver support tends to drop off the end, which is a pity.

My guess is that an update to either the kernel or the xserver has broken video for you. I'll have a search around the forum and see if I can find anything useful. In the meantime, can you confirm that you are using version 9.10 of Ubuntu, the Karmic Koala? With no xorg.conf, I'm guessing that's the case. And... When you first boot up, when you get to the menu where you choose which operating system to boot into, do you get a choice something like:

Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-17-generic

The numbers may differ slighty - you may have 2.6.31-19 or -16 or even -14. If booting into the -20 kernel fails, try booting into the -19 kernel or any lower-numbered one. Not the 'recovery mode' option, though.

---

### Post by electeng33 on 2010-04-21
Thanks coffeecat for your further response.

Yes, I am using 9.10 Karmic Koala version

On boot up I get the following two lines:-
     2.6.31-14 generic
     2.6.31-14 generic (recovery mode)
so I am unable to try to boot to a lower number

I hope this is of further help 

Regards.

---

### Post by coffeecat on 2010-04-22
This:

> **electeng33 said:**
> On boot up I get the following two lines:-
     2.6.31-14 generic
     2.6.31-14 generic (recovery mode)

.... tells us that you haven't done any updates since installing Ubuntu. The 2.6.31-14 kernel is the version that came with the live CD. Which means that an update hasn't broken the system.

To be honest, I'm not sure what to suggest next. Something has gone wrong - that's clear - but it could be one of a large number of things, and that would take a lot of investigating from the recovery console to discover, which is not easy. It might be quicker simply to reinstall. That way you could check that you can still get the GUI desktop in the live session.

---

### Post by electeng33 on 2010-04-27
Thanks coffeecat for your further suggestions.

I re-installed Ubuntu, and was delighted to find that it worked.   Some four times I shut down and re-opened in connection with checking readability of Office 97 with Open Office and vice versa.

Imagine my disappointment when a few hours later I switched on the PC again and found that Ubuntu would not boot.   It has gone back to the same condition as before  I re-installed Ubuntu - except that this time I had not loaded Office 97 because it was already installed.  On switch on I now have a menu with two sets of Ubuntu items.   I can boot up with WinXP but not with either of the Ubuntu items.

Does this mean that I now have two versions of Ubuntu on my hard drive?   As I mentioned in an earlier note I cannot find the Ubuntu system which is I suppose because I am totally new to Ubuntu and do not know where to look, and what commands to use to get the information - or is it simply that the system files are hidden by default, as they are in Windows systems.   If the installation disc has overwritten my first installation of Ubuntu, I need to know how to remove one set of Ubuntu items on the menu.   if I have got two Ubuntu systems installed, I suppose I need to remove both of them and start again.

Any thoughts on a solution to these problems will be most gratefully received.

---

### Post by coffeecat on 2010-04-28
> **electeng33 said:**
> Imagine my disappointment when a few hours later I switched on the PC again and found that Ubuntu would not boot.

Lightning striking in the same place twice? :( I wonder if there's a bad sector on the hard drive where you've installed Ubuntu, because I cannot think of any other rational explanation. Please believe me - Ubuntu just doesn't do this, especially if you haven't installed any updates, **unless** there's a hardware problem.

However, if it is a bad hard drive, you will have had to install Ubuntu the second time where it was installed the first time - i.e. on the same partition. So we need to clarify this following:

> **electeng33 said:**
> On switch on I now have a menu with two sets of Ubuntu items.   I can boot up with WinXP but not with either of the Ubuntu items.

Does this mean that I now have two versions of Ubuntu on my hard drive?

With a fresh install of Ubuntu, you should have three non-Windows entries:

Ubuntu, Linux 2.6.31-14-generic
Ubuntu, Linux 2.6.31-14-generic (recovery mode)
Memory test (memtest86+)

And, as you install each new kernel with an update. you'll get two more entries for each kernel. Something like:

Ubuntu, Linux 2.6.31-20-generic
Ubuntu, Linux 2.6.31-20-generic (recovery mode)

... if it was the -20 kernel that was in the update. But you haven't updated. When you say "two sets of Ubuntu items", do you mean two -14 entries as above, or four altogether? Because, if four, you may indeed have two installations on adjacent partitions.

Let's do some investigation. Boot up with the live CD and open a terminal (Applications > Accessories) and post the output of:

```
sudo fdisk -l
```You really need to be connected to the internet in the live session to post that output, in order to do a copy and paste into the message box. Please enclose the output in code tags by highlighting the text and clicking on the # icon in the message toolbar.

A few comments: We've (more-or-less) established that you haven't installed using Wubi. If you'd installed with Wubi, Ubuntu would appear in Windows' Add/Remove programs utility. Also - you'd have a C:\ubuntu folder. Perhaps you'd like to double-check that because Wubi is different from...

A conventional dual-boot. With this, the installer shrinks the Windows C:\ partition to make room for two partitions for Ubuntu: a swap partition and a root partition, formatted with the Linux filesystem ext3 or ext4. Windows knows nothing about ext3/4 (or Linux swap for that matter) so that is why you don't see them in My Computer. In fact, you can see the Linux partitions if you drill down deep into an admin utility in Control Centre, where they'll appear as "healthy partitions" but of unknown type.

Anyway, the output of 'sudo fdisk -l' should clarify things.

---

### Post by electeng33 on 2010-05-10
Thanks Coffeecat for your latest reply.

My Grub menu screen says:-

Ubuntu 2.6.31-14-generic
Ubuntu 2,6,31-14-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest 86+.serial console 115200)
Windows XP (on/dev/sda1)
Ubuntu 2.6.31-14, Linux (on/dev/sda11)
Ubuntu 2.6.31-14, Linux (recovery mode) (on/dev/sda11)


The output from sudo fdisk -l was:-

Disk/dev/sda: 88.0 G B 80026361856 bytes, 255 heads, 63 sectors/track, 9729 cylinders   units = cyloinders of 16865*512 = 8225288 bytes
Disk identifier:  0xcba8cba8

Device Boot  Start  End     Blocks      ID     System

dev/sda1         1     261    2096451     6       FAT 16
dev/sda2      262   9729  76051710     f    W95 Ext'd (LBA)
dev/sda5      262   2174  15366141     b   W95 FAT 32
dev/sda6     2175  2978  6393838+     b   W95 FAT 32
dev/sda7     4888  5682  12169206     b   W95 FAT 32
dev/sda8     5603  7117  12169206     b   W95 FAT 32
dev/sda9     7118  7714    4795371     b   W95 FAT 32
dev/sda10   8633  9729    8811621     b   W95 FAT 32
dev/sda11   2971  4833    8538516   83    Linux
dev/sda12   4034  4087    433723+   82    Linux swap/Solaris
dev/sda13   7715  8586  7004308+   83    Linux
dev/sda14   8587  8632    369463+   84    Linux swap/Solaris

Partition table entries are not in disk order


Just in case this has any relevance to my problem with Ubuntu, through looking at Device Manager in Windows XP, I find that Ethernet controller and Multimedia Audio Controller have yellow marks against them.   I have not been able to find drivers, but as I have a network ID card, and I do not need sound at all, and as Windows XP still runs neither of these are a problem. 

I shall be very grateful for any further advice you may be able to offer.

Regards.

---

### Post by sydbat on 2010-05-10
> **electeng33 said:**
> Thanks Coffeecat for your latest reply.

My Grub menu screen says:-

Ubuntu 2.6.31-14-generic
Ubuntu 2,6,31-14-generic (recovery mode)
Memory test (memtest 86+)
Memory test (memtest 86+.serial console 115200)
Windows XP (on/dev/sda1)
Ubuntu 2.6.31-14, Linux (on/dev/sda11)
Ubuntu 2.6.31-14, Linux (recovery mode) (on/dev/sda11)


The output from sudo fdisk -l was:-

Disk/dev/sda: 88.0 G B 80026361856 bytes, 255 heads, 63 sectors/track, 9729 cylinders   units = cyloinders of 16865*512 = 8225288 bytes
Disk identifier:  0xcba8cba8

Device Boot  Start  End     Blocks      ID     System

dev/sda1         1     261    2096451     6       FAT 16
dev/sda2      262   9729  76051710     f    W95 Ext'd (LBA)
dev/sda5      262   2174  15366141     b   W95 FAT 32
dev/sda6     2175  2978  6393838+     b   W95 FAT 32
dev/sda7     4888  5682  12169206     b   W95 FAT 32
dev/sda8     5603  7117  12169206     b   W95 FAT 32
dev/sda9     7118  7714    4795371     b   W95 FAT 32
dev/sda10   8633  9729    8811621     b   W95 FAT 32
dev/sda11   2971  4833    8538516   83    Linux
dev/sda12   4034  4087    433723+   82    Linux swap/Solaris
dev/sda13   7715  8586  7004308+   83    Linux
dev/sda14   8587  8632    369463+   84    Linux swap/Solaris

Partition table entries are not in disk order


Just in case this has any relevance to my problem with Ubuntu, through looking at Device Manager in Windows XP, I find that Ethernet controller and Multimedia Audio Controller have yellow marks against them.   I have not been able to find drivers, but as I have a network ID card, and I do not need sound at all, and as Windows XP still runs neither of these are a problem. 

I shall be very grateful for any further advice you may be able to offer.

Regards.To me, and I could be wrong, this looks like a wubi install. My first try with wubi did the exact same thing...which is why I do not recommend wubi.

electeng33 - Just to clarify everything - When you installed Ubuntu 9.10 each time, were you in Windows XP? By this I mean, did you boot into Windows, insert the CD and launch the Ubuntu program?

If not, did you go into your BIOS and set it to boot from CD, then run the live desktop and do the installs that way?

As I stated, I am trying to clarify how you have installed Ubuntu because, as coffeecat mentions, what has happened twice to you is extremely unusual. 

In my experience, wubi installs are at the mercy of Windows because when you change something in Windows it can adversely effect the wubi install.

---

### Post by coffeecat on 2010-05-11
> **sydbat said:**
> As I stated, I am trying to clarify how you have installed Ubuntu because, as coffeecat mentions, what has happened twice to you is extremely unusual. 

In my experience, wubi installs are at the mercy of Windows because when you change something in Windows it can adversely effect the wubi install.

@electeng33, I think I'll wait for your response before adding anything. We do really need to know whether this is Wubi or not.

---

### Post by electeng33 on 2010-05-13
Thanks to both Coffeecat and Sydbat for your further comments.

In order to install Ubuntu I first set the BIOS to include CD in the boot sequence.   The Ubuntu screen appeared and invited me to look around Ubuntu before installing, which I did for my first install.  I then, from the Ubuintu desktop took the option to install Ubuntu.

I took out the CD and ran Ubunto from the hard drive satisfactorily at first.   Then after the PC had been shut down a few time, I could no longer boot from the hard drive.

I was still able to boot from the CD, and using the same procedure as for the first install, in installed again.   I got the same result, that I could then boot from the hard drive but after a few shut downs I could no longer boot from the hard drive.

I hope I have fully answered your queries, but if there are any other details that would help please do let me know.   I am quite prepared to wipe the hard drive clean, and re-stall Windows XP the Ubuntu, if that is necessary.

Your comments that this problem is quite unusual with Ubuntu is very encouraging, and I have already seen enough to make me want to persevere and get away from the dependence on Windows.

One other point is passing - whilst preparing my last reply, I saw a new thread in which the enquirer was asking about a manual.   A reply was given showing an address from which a 150 page publication was downloadable.    I thought I would return to that after having made my last reply.  This was a big mistake, because beginner enquiries were coming in so fast, that I was unable to find the enquiry again.   I would like to know more about that commands that are available , a few of which I have used in following your previous instructions.   If you are able to point me in the right direction that would also be most helpful.

Many thanks for your interest.

---

### Post by coffeecat on 2010-05-18
@electeng33, my apologies for not getting back before. I hope you are still following the thread. Anyway....

> **electeng33 said:**
> In order to install Ubuntu I first set the BIOS to include CD in the  boot sequence.   The Ubuntu screen appeared and invited me to look  around Ubuntu before installing, which I did for my first install.  I  then, from the Ubuintu desktop took the option to install Ubuntu.

Well, that certainly does sound like a conventional install rather than a Wubi one, but I have no further thoughts on why two Ubuntu installations should go wrong after a time.

> **electeng33 said:**
> The output from sudo fdisk -l was:-

Disk/dev/sda: 88.0 G B 80026361856 bytes, 255 heads, 63 sectors/track, 9729 cylinders   units = cyloinders of 16865*512 = 8225288 bytes
Disk identifier:  0xcba8cba8

Device Boot  Start  End     Blocks      ID     System

dev/sda1         1     261    2096451     6       FAT 16
dev/sda2      262   9729  76051710     f    W95 Ext'd (LBA)
dev/sda5      262   2174  15366141     b   W95 FAT 32
dev/sda6     2175  2978  6393838+     b   W95 FAT 32
dev/sda7     4888  5682  12169206     b   W95 FAT 32
dev/sda8     5603  7117  12169206     b   W95 FAT 32
dev/sda9     7118  7714    4795371     b   W95 FAT 32
dev/sda10   8633  9729    8811621     b   W95 FAT 32
dev/sda11   2971  4833    8538516   83    Linux
dev/sda12   4034  4087    433723+   82    Linux swap/Solaris
dev/sda13   7715  8586  7004308+   83    Linux
dev/sda14   8587  8632    369463+   84    Linux swap/Solaris

Partition table entries are not in disk order

That confirms that you have two separate Ubuntu installations. They are in different parts of the hard drive - they are not contiguous - which is interesting. Did you re-use pre-existing partitions? Also, that's the oddest partition setup for Windows I've ever seen. Is that some sort of manufacturer's setup? They've somehow managed to put Windows in no less than 6 logical partitions, and FAT32 ones to boot. That's quite weird. My guess is that the FAT16 sda1 partition is a Windows boot partition and one of the six logicals is Windows C:\ but I have no idea why they should do that. A more usual arrangement would be to put Windows XP on a single primary NTFS partition, often accompanied by a hidden (also primary NTFS) restore partition.

> **electeng33 said:**
> I am quite prepared to wipe the hard drive clean, and re-stall Windows XP the Ubuntu, if that is necessary.

Re-installing Windows will not help your Ubuntu problems. You also have the complication of that odd partition layout. How would you re-install Windows if you were to do so? With a Microsoft install CD, or some sort of OEM manufacturer's restore utility?

> **electeng33 said:**
> One other point is passing - whilst preparing my last reply, I saw a new thread in which the enquirer was asking about a manual.   A reply was given showing an address from which a 150 page publication was downloadable.    I thought I would return to that after having made my last reply.  This was a big mistake, because beginner enquiries were coming in so fast, that I was unable to find the enquiry again.   I would like to know more about that commands that are available , a few of which I have used in following your previous instructions.   If you are able to point me in the right direction that would also be most helpful.

That sounds like the Getting Started with Ubuntu Manual. Link for you:

[http://ubuntu-manual.org/](http://ubuntu-manual.org/)

---

### Post by electeng33 on 2010-05-21
Thanks Coffeecat for your further helpful comments, yes I am still following this thread hoping to find the way to get Unubtu installed and working on my hard drive.   Actually -- the hard drive partitioning is my own work!!   

I bought a larger (80GHb) hard drive and divided it into seven partitions using fdisk, the first FAT16 and the remainder FAT32.   The current WinXP indication of partitions is:-
                     C:   2.2 Gb
                     D: 15.7 Gb
                     E:   6.5 Gb
                     F:  12.4 Gb
                     G: 12.4 Gb
                     H:  12.4 Gb 
                      I:   9.0 Gb  

               TOTAL  70.6 Gb !!! 

 I loaded Win98 second edition on the C:.   Later I loaded WinXP onto the D: from a CD I had purchased, using a dual boot arrangement - this was so that I could become accustomed to using WinXP, whilst retaining Win98 for work that I did not want to be disrupted in case of problems with WinXP

Then I heard about Ubuntu, read that it could be dual booted with Windows, got a Ubuntu CD and booted from the CD.   It looked very interesting, so I loaded it on to the hard drive.   Incidently the boot up menu then changed to that which I have indicated in an earlier reply, and on selecting WinXP another menu appears offering a choice of  WinXP or Win98.  Somewhere along the line my Win98 stopped working (which I think may have been before loading Ubuntu), but that did not bother me as I had by then become accustomed to working with WinXP and ceased to use Win98.

I was not aware that Ubuntu would create further partitions, and I expected to be able to tell it which FAT32 partition to use.   I believe during the installation process I would have had that opportunity, but when the custom installation invitation appeared there were a number of questions I did not know how to answer, so I went back to the automatic Ubuntu installation.

I dont whether all this is any help, but I have recounted as fully as I can in the hope that it may shed light on the problem.     

Although the problem still exists, each time I have received comments I  have gained a little more knowledge of Ubuntu, which is very helpful.

---

### Post by electeng33 on 2010-07-27
Thanks to those who have tried to help me over my dual operating system problem.

I have been out of touch for some time owing to a WindowsXP crash which required cleaning the hard drive, and reloading, etc..   During this time I installed a second hard drive 180Gb which I intend for Ubuntu.   Previously I had  Windows XP and Ubuntu  loaded on the same  80Gb hard disc.

The WindowsXP reload went satisfactorily, and is now up and running.

I have today loaded Ubuntu on the second hard drive.   After loading I shut down and tested that I could boot Ubuntu from the hard drive.   Ubuntu loaded just as it should do.

Then I shut down again, re-started and selected WindowsXP to check that Windows XP was still working.   I got a message that Windows needed to alter system files - it flashed up and then disappeared.   WindowsXP duly booted.

I wondered what Windows had done to which system files, so shut down again, re-started and selected Ubuntu.    It failed to boot just as it did some time ago when I first raised this problem, only I incorrectly thought at that time it was due to my loading Microsoft Office.   

On starting up WindowsXP a second time I did not get a message about system files, so I cannot look at it again - but I can remember there was no information about which files were altered.   

I am hoping that now someone may be able to assist me, as I am sure there must be others who have encountered this problem.

I will be most grateful for any suggestions anyone out there can make.

---

### Post by wilee-nilee on 2010-07-27
> **electeng33 said:**
> Thanks to those who have tried to help me over my dual operating system problem.

I have been out of touch for some time owing to a WindowsXP crash which required cleaning the hard drive, and reloading, etc..   During this time I installed a second hard drive 180Gb which I intend for Ubuntu.   Previously I had  Windows XP and Ubuntu  loaded on the same  80Gb hard disc.

The WindowsXP reload went satisfactorily, and is now up and running.

I have today loaded Ubuntu on the second hard drive.   After loading I shut down and tested that I could boot Ubuntu from the hard drive.   Ubuntu loaded just as it should do.

Then I shut down again, re-started and selected WindowsXP to check that Windows XP was still working.   I got a message that Windows needed to alter system files - it flashed up and then disappeared.   WindowsXP duly booted.

I wondered what Windows had done to which system files, so shut down again, re-started and selected Ubuntu.    It failed to boot just as it did some time ago when I first raised this problem, only I incorrectly thought at that time it was due to my loading Microsoft Office.   

On starting up WindowsXP a second time I did not get a message about system files, so I cannot look at it again - but I can remember there was no information about which files were altered.   

I am hoping that now someone may be able to assist me, as I am sure there must be others who have encountered this problem.

I will be most grateful for any suggestions anyone out there can make.

Just to make this easier could you start a new thread with this information and post the bootscript in my signature in code tags as described. You can also set it in code tags by highlighting the txt and clicking on the # in the reply panel.

These sort of problems are sometimes fixed in a couple of posts other times pages of responses, this is why a new thread would be appropriate, it is a different problem, and the thread title is a misnomer.

---

