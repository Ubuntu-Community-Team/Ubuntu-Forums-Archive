---
title: "GRUB Being a @$*&amp;%! Please Help!!!"
date: 2011-06-06
forum: New to Ubuntu
---

### Post by Neoxhadowespio on 2011-06-06
Hello, me again. I'm typing from a small netbook I use. I need help with GRUB. This is the first time I've ever had a serious problem with my PC ever since I got Linux. And I must say, I love it. But what I was trying to do was recover lost data from my HDD using Testdisk. As some of you can imagine, I recovered the lost partition and restarted. That was the first time I was greeted with the message "unknown filesystem, grub rescue> _" :( So I finally got a Live USB and booted from that but then it gave me "Boot Error." Now, I checked everything and even got a different OS on there but still no marshmallow. Then I tried Rescatux and Super GRUB Disk but still the same damn message. I think this "Boot Error" might be a long term error because when the PC did work fine, if I restarted with the USB in the port (I carry Ubuntu Netbook along with other stuff in there) it would give me the message. I heard somewhere that you have to change the USB Emulation to .zip or something but my BIOS does not support it. I do not have an blank disk around and I won't be getting one too soon so please help!.

---

### Post by Neoxhadowespio on 2011-06-06
(bump!)

---

### Post by oldfred on 2011-06-06
If for whatever reason you cannot get a liveUSB to boot, then you only can try manual booting from rescue prompt.


Grub Rescue Prompt Megathread - drs305
[http://ubuntuforums.org/showthread.php?t=1594052](http://ubuntuforums.org/showthread.php?t=1594052)

---

### Post by Neoxhadowespio on 2011-06-07
Well, I figure I have a partition table or disk error, thanks to the guide. But that is obvious, did I not mention before?

---

### Post by oldfred on 2011-06-07
Then you are going to need a bootable liveUSB or CD to be able to make any repairs.

---

### Post by Neoxhadowespio on 2011-06-07
I have no blank disk. I only have USBees.

---

### Post by oldfred on 2011-06-07
Create a bootable USB flash drive. 

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Neoxhadowespio on 2011-06-08
Have you not actually read my post? Someone else, please help!

---

### Post by verymadpip on 2011-06-08
Try making the bootable USB on another machine, if you can get to one.
Check the integrity of the download (MD5sum)
Have a look at this for GRUB rescue:
[http://ubuntuforums.org/showthread.php?t=1769025&highlight=grub+device](http://ubuntuforums.org/showthread.php?t=1769025&highlight=grub+device)
(have to be running Live CD or USB)

I don't know anything about recovered data & such like.
I also don't know anything about .zip USB emulation & BIOS stuff that you're talking about.

If you think it's along term issue it my have to do with the integrity of what's on your USB, or even a hardware problem perhaps?

Boot info script would be useful, it would allow more people to try & help you.  Of course you need to be able to boot something to get that info.
Unfortunately that kind of stuff is mostly gibberish to me as I'm a Newb myself :). 

Do keep us posted on your progress.  Relax a little.  It will come good with help from these forums.


Sorry I can't be more help to you.

---

### Post by FormatSeize on 2011-06-08
> **Neoxhadowespio said:**
> Have you not actually read my post? Someone else, please help!
Your post, by and large, is a rant, and it's quite difficult to discern whether you are trying to get past the "grub rescue" prompt when you boot from your hard drive, or whether you are trying to figure out how to fix the "boot error" that you get when you boot from the Live USB. 
 
The information has been provided for you to boot manually from the grub rescue prompt. If you do not want to boot manually from the grub rescue prompt, then you don't want to fix your problem(s). Additionally, information has been provided for you to make repairs using a Live USB. If you do not want to boot from a Live USB and fix your problem, then there's nothing we can type to fix your problem(s).
 
Lastly, if you can not boot into a Live USB environment, that's due to one of the following:
1. You do not want to boot into a Live USB environment
2. The boot stick has errors, and you need to create another one
3. The boot stick itself is faulty, and you need to either try another, or acquire another
4. You have hardware issues making it impossible to do anything meaningful with your software (this happened to me about a month and a half ago. First, my computer wouldn't boot, then it wouldn't boot from a Live CD. Soon enough, it stopped booting from USB, and it was time to replace it).

---

### Post by Neoxhadowespio on 2011-06-08
Kind thanks and good luck to verymadpip. I do not know what a "boot script" is though. Formatseize, I just want to access my PC again, you are correct about being unclear and my apologies. I'm sorry if I'm a bit angry or something. I thing it might be an unlucky thing going on here. I'm pretty sure the issue is software based since the box is well maintained and fairly recent.

---

### Post by YesWeCan on 2011-06-08
> **Neoxhadowespio said:**
> ... I was greeted with the message "unknown filesystem, grub rescue> _"

So did you try the instructions Oldfred gave you or not?

At the 'rescue>' type 'ls' to get a list of the partitions that Grub can detect. Idebtify the one which contains /boot. Then do the following:
```
set prefix=(hdX,Y)/boot/grub  [COLOR=DarkOliveGreen]# Example: (hd0,1) , (hd1,5)[/COLOR]
set root=(hdX,Y)
insmod linux
linux /vmlinuz root=/dev/sdXY ro  [COLOR=DarkOliveGreen]# Example: root=/dev/sda1 , /dev/sdb5[/COLOR]
initrd /initrd.img
boot
```If you cannot boot Ubuntu this way then you cannot boot Ubuntu.

---

### Post by Neoxhadowespio on 2011-06-09
Unknown Filesystem error, as always.

---

### Post by oldos2er on 2011-06-09
> **Neoxhadowespio said:**
> . I do not know what a "boot script" is though. 

Boot info script and instructions on using it are here: [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by verymadpip on 2011-06-09
I think it might help if we could see the output of your commands, probably for each step in the process.

I guess the first thing is to see if we can find where /Boot is, if it is anywhere to be found of course.  So if you could type ls (small L, small S) at the rescue>_ prompt & paste the output here we may be able to move forward.

I'm shooting in the dark with interpreting the output (unless it is  dazzlingly clear).  I am certain that another forum member will be able  to though.


Did I read correctly when you wrote you had put a different OS on the drive?  Let's not go into that now :D

---

### Post by Neoxhadowespio on 2011-06-09
(sigh!) It is impossible to boot from an USB (Boot Error)! I have NO BLANK DISK! When I preform the "ls" command, I get the Unknown Filesystem error! I recovered a lost partition that once used Windows. You could say the I simply installed another OS.

---

### Post by verymadpip on 2011-06-09
I've reached the limit of my knowledge.
Sorry I can't help.

Good luck bud.

---

### Post by Neoxhadowespio on 2011-06-11
One more time, I cannot boot into Ubuntu. I run into "error: unknown filesystem. grub rescue>_" Now, when I type "ls" I get the following: (hd0) (hd0,msdos5) (hd0,msdos1). Now I tried for all three "ls (hd0)/boot" but the error comes back. I do not recall any other codes. Possible recovery methods now: 1. USB Drive, 2. CD Drive, 3. Floppy, 4. Some extremely complicated network boot theory which will never work, 5. Send the PC to a professional. Response: 1. No matter what I do, Unetbootin, Startup Disk Creator, Super GRUB Disk, Rescatux, Ubuntu Live USB, whatever. I get the same message: "Boot Error." 2. No black CD, 3. No Floppy or Floppy Port, 4. No other computer, why bother, 5. This will be expensive, my father will be angry with me and I will have to go back to using Windows Vista. And you know how much that sucked. My father is Anti-Linux. Besides, even if we do keep Linux somehow, they probably wouldn't be able to repair it. I live in a small town where most people don't even know what an OS is!

---

### Post by oldfred on 2011-06-11
If you properly created a bootable USB flash drive or a bootable CD then you must not be selecting the USB drive as the bootable device, assuming USBs are bootable. Otherwise you have to then use a CD.

On my system I have many choices in BIOS to choose USB bootable devices and none of them work with a flash drive. I also was lost for a while but left it in and one day was changing which drive to boot from with my one time boot key (f12 on my system) and I did not just see my hard drives but also my flash drive. It has to be plugged in, has to be bootable and you have to select it in BIOS or one time boot key.

If you keep getting the same error you must still be trying to boot from hard drive.

---

### Post by Neoxhadowespio on 2011-06-12
Oh yeah, did that alright! And thanks for not giving up on me :)

---

### Post by Neoxhadowespio on 2011-06-12
(bump!)

---

### Post by jimwill on 2011-06-12
You did say that you were sure it wasn't a hardware problem, or I would suggest that. 
The only other thing I could suggest (also being a noob) is to use a windows boot disk/cd. If you don't have one maybe a friend could make one for you from their computer. Since you did a recovery of a windows system you *may* be able to do a repair of it. Then you could search for a program (can't remember the name) that allows windows to access linux partitions. If you can get that far then you would have some clue as to what you may need to do to get back to linux! (can't blame you for preferring it, I do to!)

---

### Post by Neoxhadowespio on 2011-06-12
I will consider that when all hope is lost. (No offense intended!)
Also, I would like to add that I had installed Rescatux on the USB Drive and (from another PC, of course) I was able to boot it just fine. And one more thing, it was minor so I did not say before but when I use "Startup Disk Creator", I get the message "An uncaught exception was raised: Invalid version string 'GNU/Linux'." Does this mean anything?

---

### Post by verymadpip on 2011-06-12
Is it possible for you to make an Ubuntu bootable USB with Unetbootin (rather than startup disk creator) on this other PC my friend?  Have you tried to do that?
This is so you can run a live session (or reinstall if necessary).

Of course you will then have to do as oldfred has already said: make sure you have your BIOS settings correct to boot from the USB.  (hard disk boot priority I would imagine).

---

### Post by oldfred on 2011-06-12
If you can boot into your system with Rescatux then reinstall grub2's boot loader to the MBR and see if then it works.

#reinstall from working (not liveCD) system - first find Ubuntu drive:
sudo fdisk -l
#if it's "/dev/sda"  then just run:
sudo grub-install /dev/sda

---

### Post by Neoxhadowespio on 2011-06-12
Yes, I have made my live flash drive using UNetBootin and I tried putting Rescatux using that as well.
Still, nothing! Yet I will try again...

---

### Post by Neoxhadowespio on 2011-06-12
Getting.very.angry.no.matter.what.it.wont.do.anything.else.other.than.give.me.damned.errors!!!!

---

### Post by oldfred on 2011-06-12
If you can boot Ubuntu or any Linux system with either a USB flash drive or with Rescatux into your drive then download and run this script. We can then see exactly what is installed where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by adrian15 on 2011-06-13
> **Neoxhadowespio said:**
> Then I tried Rescatux and Super GRUB Disk but still the same damn message. I think this "Boot Error" might be a long term error because when the PC did work fine, if I restarted with the USB in the port (I carry Ubuntu Netbook along with other stuff in there) it would give me the message. I heard somewhere that you have to change the USB Emulation to .zip or something but my BIOS does not support it. I do not have an blank disk around and I won't be getting one too soon so please help!.

I have read entire post (28 posts) and I have some ideas:

1) Boot error might be caused because usb boot device is not the first one. You have said that your usb device boots in a friend's computer. And you have said that your usb device was the first to boot in your boot order. And you have already tried to use F12 or equivalent key. We are going to discard this option.

2) Your pc cannot boot from a usb device. In order to test this you will need to build a usb device that does not depend on emulation like sometimes unetbootin does. I mean... Either dding rescatux iso directly to the usb hard disk device (Be aware of that), or probably building a persistent usb device.

3) Your pc can boot from a usb device but does not support emulation. I am talking about floppy emulation. From memdisk (syslinux) wiki:
> 
MEMDISK simulates a disk by claiming a chunk of high memory for the disk and a (very small - 2K typical) chunk of low (DOS) memory for the driver itself, then hooking the INT 13h (disk driver) and INT 15h (memory query) BIOS interrupts. 

So that means that your BIOS is lacking these interrupts.

You might confirm it if in the past you have booted System Rescue Cd from your system and tried to boot super grub disk or another tool from boot command line and it has failed before ever seeing the tool itself.

4) You do not have an active partition in your hard disk. It sounds stupid, isn't it? I have found some strange BIOSes that refuse to boot if there is not an active partition in your hard disk. It does not matter the boot order, it does not matter if usb boot is enabled or not. It just does not boot anything till it finds an active partition.

The only doubt about this scenario is that I do not remember it was associated exactly with:
```

Boot error:

```

The solution for this one would be to extract the hard disk, put it in another machine and activate a partition, probably the first partition.

You can use Super Grub Disk. Boot & Tools. Activate partition for this task.

5) Wrong USB hardware choosen. It might be that BIOS handles rear-usb but not front-usb and you are putting your usb device on front-usb?

I mean... Have you tried to boot from usb using all the female usb devices available on your computer?

-----------
That's it!

Do you remember anything about 3) (Emulation not working)?
Have you tried all the female usb devices? (5)
Try (4).
Now read 1 and 2 just in case.

Hope to hear good piece of news from you. It something of this does work I will consider adding it to Rescatux.

adrian15

---

### Post by Neoxhadowespio on 2011-06-13
> **oldfred said:**
> If you can boot Ubuntu or any Linux system with either a USB flash drive or with Rescatux into your drive then download and run this script. We can then see exactly what is installed where:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.
Absolutely nothing works from the USB.

---

### Post by Neoxhadowespio on 2011-06-13
> **adrian15 said:**
> I have read entire post (28 posts) and I have some ideas:

1) Boot error might be caused because usb boot device is not the first one. You have said that your usb device boots in a friend's computer. And you have said that your usb device was the first to boot in your boot order. And you have already tried to use F12 or equivalent key. We are going to discard this option.

2) Your pc cannot boot from a usb device. In order to test this you will need to build a usb device that does not depend on emulation like sometimes unetbootin does. I mean... Either dding rescatux iso directly to the usb hard disk device (Be aware of that), or probably building a persistent usb device.

3) Your pc can boot from a usb device but does not support emulation. I am talking about floppy emulation. From memdisk (syslinux) wiki:

So that means that your BIOS is lacking these interrupts.

You might confirm it if in the past you have booted System Rescue Cd from your system and tried to boot super grub disk or another tool from boot command line and it has failed before ever seeing the tool itself.

4) You do not have an active partition in your hard disk. It sounds stupid, isn't it? I have found some strange BIOSes that refuse to boot if there is not an active partition in your hard disk. It does not matter the boot order, it does not matter if usb boot is enabled or not. It just does not boot anything till it finds an active partition.

The only doubt about this scenario is that I do not remember it was associated exactly with:
```

Boot error:

```The solution for this one would be to extract the hard disk, put it in another machine and activate a partition, probably the first partition.

You can use Super Grub Disk. Boot & Tools. Activate partition for this task.

5) Wrong USB hardware choosen. It might be that BIOS handles rear-usb but not front-usb and you are putting your usb device on front-usb?

I mean... Have you tried to boot from usb using all the female usb devices available on your computer?

-----------
That's it!

Do you remember anything about 3) (Emulation not working)?
Have you tried all the female usb devices? (5)
Try (4).
Now read 1 and 2 just in case.

Hope to hear good piece of news from you. It something of this does work I will consider adding it to Rescatux.

adrian15

1) Thats not the case.
2) I installed Ubuntu this way.
3) Possible...
4) Let's hope not...
5) Doubt it, will try nevertheless.

So 3 and 4 then. Thanks! I finally feel like we are making progress.

---

### Post by Neoxhadowespio on 2011-06-14
(bump!)
Hey, dad's getting very angry.
I don't want Vista!

---

### Post by adrian15 on 2011-06-14
> **Neoxhadowespio said:**
> (bump!)
Hey, dad's getting very angry.
I don't want Vista!

I am waiting your feedback about 3) and 4).

:confused:

adrian15

---

### Post by StrayEddy on 2011-06-14
Unetboot puppy linux, and load everything in ram.

---

### Post by Neoxhadowespio on 2011-06-15
Sorry there.
Yeah, I've booted from CD but haven't been able to boot from USB. For number 4, the "Boot Error" comes only with the USB and it says only "Boot Error." So thankfully, thats probably not it. So number 3 now, what would be the solution to that?

---

### Post by Neoxhadowespio on 2011-06-15
But the funny thing is, the machine is fairly expensive and new, something like that shouldn't have been a problem.

---

### Post by adrian15 on 2011-06-15
> **Neoxhadowespio said:**
> Sorry there.
Yeah, I've booted from CD 

Burn [Super Grub2 Disk](http://www.supergrubdisk.org/super-grub2-disk/) as you would burn the Ubuntu cd to a CD.

Set your PC to boot from Super Grub2 Disk cd. Boot from it.

Choose Detect any OS (first option) and boot into your system from it.

:guitar:

If you are able to boot into your system anyone here will be able to help you to recover your grub from inside your system.

adrian15

---

### Post by Neoxhadowespio on 2011-06-15
...I have no blank disk at hand at the moment...
Any other way?

---

### Post by adrian15 on 2011-06-15
> **Neoxhadowespio said:**
> ...I have no blank disk at hand at the moment...
Any other way?

You can use a blank DVD disk instead.

adrian15

---

### Post by FormatSeize on 2011-06-15
This is not going to sound good: Your computer, in all likelihood, has simply given out on you. This could be through normal wear and tear, or through something being accidently broken during a previous rescue attempt. I've had this happen to me before, and I tried for about a week and a half on Google, these forums, and linuxquestions dot org trying even the most outlandish things to get my computer working again.
 
First, I couldn't boot from my DVD drive. Okay, so I thought I should format my disk drive and reinstall, thinking that it was a Grub issue. But that didn't work. So, I thought, I would just delete the entire filesystem from the command line. Then on my next boot, I got the Grub rescue prompt. Cool. I can just get the instructions on how to get past this and I will be good to go. But none of it worked.
 
I tried Hiren's Boot CD, Rescatux, and a few other system rescue things, and they all failed. At this point, I thought my DVD drive was bad (it wasn't, I'm actually using it in my newer computer). So I used a laptop to make a live USB to boot from. That worked. So now I would boot from USB when installing things and what not.
 
Then, that stopped working too. I never really accessed exactly what the problem was (I built it myself, and it was my first build, so that might say something). I am using both the DVD drive and the hard disk drive from that computer, and they work fine. I still have that computer, but it still simply refuses to boot. 
 
I hope this is not what happened to you. It's horrible to have something like that happen. But it could be a possibility.

---

### Post by Neoxhadowespio on 2011-06-15
:sad::sad::sad::sad::sad::sad:
I hope not... 
Also... no DVD either. In general, no CD-based media (at the moment).

---

### Post by adrian15 on 2011-06-16
> **Neoxhadowespio said:**
> Sorry there.
Yeah, I've booted from CD but haven't been able to boot from USB.

So let's suppose that getting a blank cd is an actual problem for you.

You have said that you have booted from CD. Which CD have you booted from? What other CDs do you have at hand that you can boot from?

Please specify the name and version of the bootable CDs as accurate as possible.

Thank you.

---

### Post by Neoxhadowespio on 2011-06-16
Very old Windows XP SP2 Install CD.
But never mind that, I got a blank disk!
And I burned Super GRUB2 Disk on it, and that worked too!
But then my excitement stops when "Detect any OS" fails to do anything :(
The other options don't seem to do anything either.

---

### Post by adrian15 on 2011-06-16
> **Neoxhadowespio said:**
> Very old Windows XP SP2 Install CD.
But never mind that, I got a blank disk!
And I burned Super GRUB2 Disk on it, and that worked too!
But then my excitement stops when "Detect any OS" fails to do anything :(
The other options don't seem to do anything either.

You should burn [Rescatux](http://www.supergrubdisk.org/rescatux/) and meet me at [#rescatux at irc.freenode.net](http://webchat.freenode.net/?channels=rescatux) just in case anything goes wrong.

Once you are in Rescatux cdrom you can also join the chat from inside it thanks to **Support -> Online Human Help (Chat)** option.

I think you just need to force a fsck but I am not quite sure and having a look at Rescatux grub-install log (**Support -> Share log** option) would help on understanding what's your problem.

And, of course, you can use [bootinfoscript](http://bootinfoscript.sourceforge.net/) from Rescatux (you will need to open a console because it is not integrated in Rescatux GUI yet).

Let's hope that we can meet both online at the same time at Rescatux's chat.

Your problem motivates me because it does not seem to be a current one. ;)

adrian15

---

### Post by Neoxhadowespio on 2011-06-16
(sigh) Another Disk?
Alright, I will try but I'm really stretching my luck...
Your Time Zone, please?

---

### Post by adrian15 on 2011-06-16
> **Neoxhadowespio said:**
> (sigh) Another Disk?
I thought SG2D was going to work. The problem why you need a new blank cd is that either you did not get a CDRW disk or that your USB does not boot.

> **Neoxhadowespio said:**
> 
Alright, I will try but I'm really stretching my luck...
Your Time Zone, please?

I'm in Spain. I will be online for the next two hours probably.

Please use a cable/wire to connect to internet when booting from Rescatux. I think that wireless does not work on Rescatux. If you do not have a cable you might need to copy the log file (logs folder at Desktop) to a usb but as long mount is not automatic you will need to mount it manually... I need to improve this!!!

adrian15

---

### Post by Neoxhadowespio on 2011-06-16
Okay. I cannot confirm the time... at this time. 
I will try to get the disk.

---

### Post by jtarin on 2011-06-16
I have seen something very similar to this several times in the past week with other people on the forum and USB booting.They solved their problem by choosing not USB Flash from the bios but as another hard drive. This is the way the bios was recognizing it.What does your bios list as alternate boot methods for first boot?

---

### Post by Neoxhadowespio on 2011-06-17
My BIOS is fairly limited. Just HDD CD USB and Network Boot (maybe one more). I am typing this from my all new Rescatux/Debian Live CD. First of all kudos to the developers of Rescatux. It works quite well. In fact I'm using it right now along with Iceweasel (which appearently does not support commas). And here is my report: Grub Options gives me two sub-options. Install and Update. I tried both and it fails. Error: Grub was not installed. Something went wrong :(. Filesystem Options gives me a "fsck" respectivly. I "fscked" all the partitions (lol!) and it told me that everything worked well. But Ubuntu still did not boot. As an added bonus (becuase I recovered a lost Windowz partition as you probably do not remember) I restored Windowz MBR. Although I know that it was a stupid move I had to reinstall GRUB anyway so it was worth a shot. If you wish to meet online my timzone is in AST (Atlantic Standered Time).

---

### Post by Neoxhadowespio on 2011-06-17
One hour difference (at my time) I am available right now (3:36 PM) or well after 5:30 PM today. Or if you want tommorow but I will most likely not be here.

---

### Post by oldfred on 2011-06-17
If you have a working version of Linux then you should be able to run the boot script. It will parse your drive and show us all sorts of data about it. Download zip file, extract it and in terminal where you extracted it run it per instructions:

Boot Info Script courtesy of forum members meierfra & Gert Hulselmans
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt in a New Reply, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.
Or You can generate the tags first by pressing the # icon in the New Reply Edit toolbar and then paste the contents between the generated [ code] paste here [ /code] tags.
V60 has improved formating and requires code tags to make it legible. New Version is a zip file that you have to extract to get .sh to run.

---

### Post by Neoxhadowespio on 2011-06-17
Rescatux is a stipped version of Debian. It can not deal with compressed files. Shouldn't Rescatux have Boot Script built-in?

---

### Post by oldfred on 2011-06-17
Try this:

Get last development version of Boot Info Script:
```
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'

```

I think adrian15 said he was going to add it, but it is not there yet.

---

### Post by Neoxhadowespio on 2011-06-17
Thank you. I will post the results soon.

---

### Post by Neoxhadowespio on 2011-06-17
Hmmm (comma) it does not seem to execute.

---

### Post by kidknapp on 2011-06-17
Did you try adding sudo in front of the wget or are you referring to the boot script itself?:o

---

### Post by jtarin on 2011-06-17
In the terminal change to directory where the script is located. Then run the script by issuing the command ```
./<nameofscript>.sh
```where "nameofscript" is the actual name.

---

### Post by adrian15 on 2011-06-18
> **Neoxhadowespio said:**
> Shouldn't Rescatux have Boot Script built-in?

It's on the TODO list although you should know that I do not like it all. I mean, yes, it is useful, but I do not like how it is coded.

I sometimes dream of having time to make an improved boot script info script so that I can reuse some of its code for other parts of Rescatux.

I will probably include the original script later in Rescatux.

adrian15

---

### Post by adrian15 on 2011-06-18
First of all I have to say that I postergate the problem that Neoxhadowespio cannot boot from usb. I think it is a secondary problem because he can boot from CD.

Yesterday I managed to get in touch with Neoxhadowespio. Here there is what I learnt.

What he said at the first post:
> **Neoxhadowespio said:**
> 
But what I was trying to do was recover lost data from my HDD using Testdisk. As some of you can imagine, I recovered the lost partition and restarted. That was the first time I was greeted with the message "unknown filesystem, grub rescue> _" :(


goes like this:

1. He had windows installed on his computer.
2. He installed Ubuntu on his computer. He does not know if he wiped all the hard disk but he remembers having used the slider in the partitioning part.
3. Windows no longer boot.
4. For several weeks he uses Ubuntu with no problem at all.
5. He decides to recover Windows without doing any Ubuntu backup by using Testdisk.
6. After using Testdisk neither Windows boots nor Linux boots.

So... you will ask yourself... What is his current situation if you do not have boot info script output?

Well, I have taken a look at his:
```

fdisk -lu /dev/sda

```
output and it is similar to this:

```

sda1 FAT16 16 MB
sda2 LBAEXT 360 MB
sda5 NTFS   360 MB

```

Yes, it is right MB. What I am not quite sure is if the the total hard disk is detected as 360 MB (That kb-unit based figures confuse me).

So in order to try to save the old ubuntu partitions I have told him to run:
```

gpart /dev/sda

```
.

If we are lucky after all the boot recovery attempts and after all the fsck he has done (Trying to try to recover something) we might find there the ubuntu partitions.

After that there is an option on gpart to apply these detected partitions to the partition table.

Once you have the partitions you can try to mount it and recover data or even the os (he says it was a customized os).

So I am waiting for his gpart output to see if we can recover anything.

adrian15

---

### Post by Neoxhadowespio on 2011-06-19
> **kidknapp said:**
> Did you try adding sudo in front of the wget or are you referring to the boot script itself?:o
Boot Script itself.

---

### Post by Neoxhadowespio on 2011-06-19
> **adrian15 said:**
> First of all I have to say that I postergate the problem that Neoxhadowespio cannot boot from usb. I think it is a secondary problem because he can boot from CD.

Yesterday I managed to get in touch with Neoxhadowespio. Here there is what I learnt.

What he said at the first post:


goes like this:

1. He had windows installed on his computer.
2. He installed Ubuntu on his computer. He does not know if he wiped all the hard disk but he remembers having used the slider in the partitioning part.
3. Windows no longer boot.
4. For several weeks he uses Ubuntu with no problem at all.
5. He decides to recover Windows without doing any Ubuntu backup by using Testdisk.
6. After using Testdisk neither Windows boots nor Linux boots.

So... you will ask yourself... What is his current situation if you do not have boot info script output?

Well, I have taken a look at his:
```

fdisk -lu /dev/sda

```output and it is similar to this:

```

sda1 FAT16 16 MB
sda2 LBAEXT 360 MB
sda5 NTFS   360 MB

```Yes, it is right MB. What I am not quite sure is if the the total hard disk is detected as 360 MB (That kb-unit based figures confuse me).

So in order to try to save the old ubuntu partitions I have told him to run:
```

gpart /dev/sda

```.

If we are lucky after all the boot recovery attempts and after all the fsck he has done (Trying to try to recover something) we might find there the ubuntu partitions.

After that there is an option on gpart to apply these detected partitions to the partition table.

Once you have the partitions you can try to mount it and recover data or even the os (he says it was a customized os).

So I am waiting for his gpart output to see if we can recover anything.

adrian15

You got everything correctly. My mail is full of spam and your here anyway so here are the gpart results:

Checking partitions...
Partition(Primary 'big' DOS (> 32MB)): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 006(0x06)(Primary 'big' DOS (> 32MB))
   size: 39mb #s(80259) s(63-80321)
   chs:  (0/1/1)-(4/254/60)d (0/1/1)-(4/254/60)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

It is unusual for the application to detect my HDD as 360 MB. It should be around 250 GB if I remember correctly.
Also it was truely silly of me not to preform a backup. I was new to Testdisk and I was following a YouTube video. 
gpart is scaring me right now...

---

### Post by adrian15 on 2011-06-19
> **Neoxhadowespio said:**
> You got everything correctly. My mail is full of spam and your here anyway so here are the gpart results:
```

Checking partitions...
Partition(Primary 'big' DOS (> 32MB)): primary 
Ok.

Guessed primary partition table:
Primary partition(1)
   type: 006(0x06)(Primary 'big' DOS (> 32MB))
   size: 39mb #s(80259) s(63-80321)
   chs:  (0/1/1)-(4/254/60)d (0/1/1)-(4/254/60)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

```


It seems that gpart is not able to find your Gnu/Linux partitions.

Does the output vary if you try an:
```

gpart -e -f /dev/sda

```
?

Just to remember from Rescatux just before running gpart you will need these commands:
```

sudo -i
apt-get update
apt-get install gpart

```

> **Neoxhadowespio said:**
> 
It is unusual for the application to detect my HDD as 360 MB. It should be around 250 GB if I remember correctly.

Well, that's what you probably managed to do with testdisk. Although it might be another posterior tool which mangled everything, you only know ;).

> **Neoxhadowespio said:**
> 
Also it was truely silly of me not to preform a backup. I was new to Testdisk and I was following a YouTube video. 
gpart is scaring me right now...

Well, everything is not lost. If the extended gpart attempt that I ask you to run above does not work we can try to use testdisk to repair things (I will have to learn a bit how it works. I have already used it but I prefer gpart for this kind of task).

And finally if no partition can be found some kind of files like pictures, videos or other file types can be recovered thanks to photorec.

adrian15

---

### Post by Neoxhadowespio on 2011-06-19
Thank you for clearing the foggg window a bit. 
I will now preform: 
sudo -i
apt-get update
apt-get install gpartThats what I should do, right?
NVM, done!

---

### Post by adrian15 on 2011-06-19
> **Neoxhadowespio said:**
> Thank you for clearing the foggg window a bit. 
I will now preform:
```

sudo -i
apt-get update
apt-get install gpart

```
Thats what I should do, right?
NVM, done!

Yes. And in the same terminal just after these commands you should type:
```

gpart -e -f /dev/sda

```
and press enter afterwards.

And put here the output around [ code ] tags, although I think we will get the same output as in the first place.

adrian15

---

### Post by Neoxhadowespio on 2011-06-19
Guessed primary partition table:
Primary partition(1)
   type: 006(0x06)(Primary 'big' DOS (> 32MB))
   size: 39mb #s(80259) s(63-80321)
   chs:  (0/1/1)-(4/254/60)d (0/1/1)-(4/254/60)r

Primary partition(2)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(3)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

Primary partition(4)
   type: 000(0x00)(unused)
   size: 0mb #s(0) s(0-0)
   chs:  (0/0/0)-(0/0/0)d (0/0/0)-(0/0/0)r

---

### Post by adrian15 on 2011-06-19
> **Neoxhadowespio said:**
> Guessed primary partition table:
Primary partition(1)


We need to use testdisk.

In order to be able to use testdisk from Rescatux:

```

sudo -i
apt-get update
apt-get install testdisk

```

After that in the same terminal you should run:
```

testdisk

```

Using testdisk to recover old partition structure should be something similar to this:

[LIST]
[*]Create (Create a new log file)
[*]Select sda and press enter to select Proceed
[*]Intel (Intel/PC partition)
[*]Analyse (Analyse current partition...)
[*]Right arrow to select -> Backup
[*]Should Testdisk... under Vista? N  (You won't be able to recover Linux and we want Linux back)
[*]Click OK to continue if partitions are not found
[*]Choose Deeper search
[*]The list will appear again. Probably the right one. Press Enter.
[*]If you are convinced that this was the former partition structure that fits into Linux. You can press right arrow and press enter to select Write.
[*]Confirm if you are asked to.
[/LIST]

If you are unsure you can always not select Write and come here with the partition structure that testdisk offers you.

With the offered partition structure we can advise you to remove a partition, to change a partition type or maybe not to do anything at all.

So... waiting for testdisk results.

adrian15

---

### Post by Neoxhadowespio on 2011-06-19
It is doing its job right now. 
When the partition is recovered how far back will everything be?
Will it be exactly the way it was before it messed up?

---

### Post by adrian15 on 2011-06-19
> **Neoxhadowespio said:**
> It is doing its job right now. 
When the partition is recovered how far back will everything be?
Will it be exactly the way it was before it messed up?

There are basically three possible scenarios:

1) A Linux system that can be restored by just reinstalling grub (There is an option on Rescatux for doing that ;) ).
2) A Linux system where you can restore files but somewhat you cannot restore its boot or it is more difficult than usual.
3) No Linux partitions have been found. So it is needed to use photorec.

In neither case you are going to reboot and your system is going to boot.

I think it would be great to have the boot info script output after running testdisk, writing to disk and rebooting once again to Rescatux.

Let's see how to do that in Rescatux.

```

sudo -i
wget -O boot_info_script.sh 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=boot_info_script.sh;hb=HEAD'
chmod +x boot_info_script.sh
./boot_info_script.sh > /tmp/bootinfo.txt
gedit /tmp/bootinfo.txt

```

Please use [ code ] tags to put here the boot info script result as you never have done.

But... I cannot assure that bootinfo script will work ok because I have not prepared specifically Rescatux to have all the packages needed by bootinfo script.


adrian15

---

### Post by Neoxhadowespio on 2011-06-19
Ahhh! Thanks to everyone for their very kind support! I am so happy. Me and adrian15 have been able to get me back up and running. Thanks to him once again. Our solution was mostly made up of Testdisk where we recovered some lost data. Appearently much more was lost than a Grub file. Thank you everyone! Long Live Linux! Yeah!

---

### Post by verymadpip on 2011-06-20
Good job adrian15!!!
I for one am very pleased that has been sorted out.  Yay \o/
Enjoy.

---

### Post by adrian15 on 2011-06-20
> **Neoxhadowespio said:**
> Ahhh! Thanks to everyone for their very kind support! I am so happy. Me and adrian15 have been able to get me back up and running. Thanks to him once again. Our solution was mostly made up of Testdisk where we recovered some lost data. Appearently much more was lost than a Grub file. Thank you everyone! Long Live Linux! Yeah!

Testdisk was able to detect two partitions: Dell Utility and Linux.
I set up the Linux partition from Deleted to primary partition and saved.

When we rebooted (and not before) we were able to mount the partition as ext4. Once it was mounted I unmounted and left [Rescatux]("http://www.supergrubdisk.org/rescatux/") to do its job.

I used **Restore Grub to the MBR** and **Update Grub configuration** options.

He was able to boot after that I am still confused about him having only one Linux partition (no swap, no other linux partition).

Maybe Neoxhadowespio you should post Boot info script just be to sure that everything is ok.

I mean we will see at your
```

/etc/fstab

```
file if you had other partitions that you are not using right now because of testdisk not being able to detect all of your former partitions.

adrian15

---

