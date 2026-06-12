---
title: "Help! Removed Ubuntu to return computer to store, now it won't boot"
date: 2009-05-08
forum: New to Ubuntu
---

### Post by swarup on 2009-05-08
I purchased a computer which I ended up not liking and so need to return it to the store tomorrow. It came with Vista on a 500 GB HDD. I shrunk vista to 50 GB and installed Jaunty on the space thus freed up. Now that I decided to return the computer, I booted to a Parted Magic livecd, deleted the extended partition containing Jaunty and linux swap, and re-expanded the Vista partition to its former size. So now there is nothing left of Ubuntu on the HDD. But when I try to boot up the computer it is still looking for GRUB. Here is what comes on the screen:

```
GRUB Loading stage 1.5
GRUB loading, pleast wait...
Error 22
```

How can I remove whatever is remaining of GRUB from the computer, so it will boot normally into Vista as a one-boot system, the way I got it from the store. Thanks!

---

### Post by Cypher on 2009-05-08
Did the computer come with a Vista or restore disk? If so, you'll want to put that in and have Windows repair itself, this will cause it to remove GRUB and put the Windows boot-loader back in.

Hopefully Windows Vista can properly handle being shrunk and then grown back in size..

---

### Post by hansdown on 2009-05-08
Hi swarup.

Please see this.

[http://www.google.ca/search?q=reinstalling+mbr&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a](http://www.google.ca/search?q=reinstalling+mbr&ie=utf-8&oe=utf-8&aq=t&rls=com.ubuntu:en-US:unofficial&client=firefox-a)

---

### Post by abn91c on 2009-05-08
if you did not create or have a vista recovery disk you are out of luck. Normally you will boot from the cdrom with the vista cd and re-run the setup. Does the HDD have a vista recovery partition? if it does then run the recovery process from there, otherwise you voided the warranty and they may not take it back

---

### Post by fatbotgw on 2009-05-08
Sounds like Grub is still installed in the master boot record (MBR).  You'll need to replace it with the Windows boot loader.  I don't know the stops off hand, but if you google "fix windows MBR" I'm sure you'll get a set of instructions.

---

### Post by swarup on 2009-05-08
The computer did not come with a Vista reinstallation or recovery disk. It has a Vista recovery partition on the HDD. 

I do have a Vista reinstallation DVD for another computer. The computer I'm returning is an HP, which has consumer Vista on it, and the reinstallation disk is a Vista Business edition, for a Dell.

So I don't know that I should use that disk to do a fresh install, as it would probably install the Dell logo on the post etc. But perhaps it could be used to recover/repair the MBR?

This is my main question, I guess: Can I use Dell's Business Vista Reinstallation DVD to fix the MBR on this HP machine?

---

### Post by Sef on 2009-05-08
> if you did not create or have a vista recovery disk you are out of luck. 

Not correct.  Here is a [Windows Vista Recovery Disk]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").

---

### Post by rustutzman on 2009-05-08
Wipe the drive and explain you didn't want any personal info left on it. I'm sure the vendor can take care of it.

Russ

---

### Post by swarup on 2009-05-08
> **Sef said:**
> Not correct.  Here is a [Windows Vista Recovery Disk]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/").

Wow! Thanks for the great tip. After reading the explanation they give on the link you mention, it sounds as though my Dell Vista Reinstallation DVD may just have the very "recovery center" which your link refers to. I have pasted the link's description below:

> The Windows Vista DVD has a "recovery center" that provides you with the option of recovering your system via automated recovery (searches for problems and attempts to fix them automatically), rolling-back to a system restore point, recovering a full PC backup, or accessing a command-line recovery console for advanced recovery purposes.

Microsoft seems to have realized this problem, and have thankfully made a recovery disc for this purpose. It contains the contents of the Windows Vista DVD's "recovery center," as we've come to refer to it. NeoSmart Technologies is hosting a copy of the Windows Vista Recovery Disc for your convenience... 

So if my Vista Reinstallation DVD has the same "recovery center" on it, then perhaps I could just use that. What do you think?

Another possible option is to use an ubuntu livecd, as described here: [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/) Apparently it has a utility called "ms-sys", which is a program used to write Microsoft compatible boot records. So which of these three options sounds safest: 1. download the Vista recovery CD, 2. Use the Dell Vista Reinstallation DVD, 3. Use the Ubuntu livecd?

---

### Post by Sef on 2009-05-08
> So if my Vista Reinstallation DVD has the same "recovery center" on it, then perhaps I could just use that. What do you think?

That should restore it to factory defaults.

---

### Post by Blabberbox on 2009-05-08
[COLOR=Red]IF the recovery partition was NOT TOUCHED during the install or removal of Linux:
[/COLOR]
Proceed with caution!!!! Read + Print steps.  I also recommend investigating this further prior to attempting.

When the machine first powers up [COLOR=Red](ONLY if the recovery partition is VALID)[/COLOR]

[http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&#9001;=en&docname=c00814731#c00814731_vista]("http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&lang=en&docname=c00814731#c00814731_vista")

[FONT=Arial][B]Recovering the system without using Windows                  
                [/B][/FONT]                 
                1.  Disconnect all peripherals and internal non preinstalled devices from the                 PC, except the monitor, keyboard, and mouse.                 
                
                2.  Turn on the computer.                 
                
                3.  When the initial blue HP screen appears, press the F10 key repeatedly                 until a recovery menu appears. The progress indicator that first appears does not                 indicate that a recovery is taking place. The progress indicator represents the                 time before the recovery process is started.                  
                
                4.  When the Recovery screen appears, click **Next**, and then                 click **Yes** to perform                 a normal, non-destructive recovery.  **ATTEMPT to save user data**                 
                
                5.  To perform a destructive recovery, click **Advanced**, and                 then click **Yes**.
**ALL USER DATA WILL BE LOST** 
                
                6.  After the System Recovery is complete, and the computer starts successfully,                 update the computer software.

Good Luck!!!!!

-BB

---

### Post by swarup on 2009-05-08
Wow, so many incredibly incredibly helpful replies. And so many options. Well, in the mean time, I've gone ahead and downloaded the Vista Recovery iso suggested by Sef. So perhaps I'll try that first. --Although the strategy given by Blabberbox of doing F10 to access HP's own recovery partition, also sounds very safe and good. I'm sure one of these will work. Thanks so much for everyone's help! I'll let you know how it goes.

---

### Post by swarup on 2009-05-09
Well, I downloaded the Windows Vista Recovery Disc 64-Bit livecd iso, suggested by Sef. But when I booted to the livecd and ran the repair tool, it said it could not find anything wrong. I tried it several times, and it said the same thing every time.

I tried hitting F10 repeatedly as suggested just above by Blabberbox, to access HP's recovery partition. But it only seemed to enter HP's Setup utility, with power options etc, and nothing about recovery.

I then found an Ubuntu forum thread about repairing the Windows MBR with an Ubuntu Livecd ([http://ubuntuforums.org/showthread.php?t=622828](http://ubuntuforums.org/showthread.php?t=622828)), especially the post #10 on that thread.

So, I booted to a Jaunty livecd, and tried the two solutions given by caljohnsmith in post #10 of that thread (using the syslinux and mbr utilities). Both procedures went smoothly, but at the end of each when I tried a reboot, I got the same screen shown in my 1st posting here, about "GRUB loading, pleast wait...Error 22".

Vista was running perfectly until I removed the linux partition, so I do not think there is anything wrong except for the MBR. I did re-expand the Vista partition, which I now read some say was not good to do. But Vista was the first partition on the drive meaning that when I expanded it, I expanded it from its rear end, back to the end of the drive. So hopefully, that is an encouraging point.

What should I do at this point, to re-establish the Windows MBR?

---

### Post by Didius Falco on 2009-05-09
A few messages, and some eight hours ago, you said you had a Vista Recovery CD. Run that - it should wipe the whole drive and reset it to the factory default.

If you are in your Ubuntu Live CD right now, open a Terminal shell and type: ```
sudo fdisk -l
``` and post the output here before you do that - I'm just curious if you have a hidden Vista Restore partition. If it's a Vista Restore [COLOR=Red]DVD[/COLOR],  you probably don't, since that would be plenty large enough to hold everything needed to reset it to the factory settings.

---

### Post by swarup on 2009-05-09
I will boot up the Vista livecd now as you suggest, and give you the output of sudo fdisk -l.

I have a Dell Vista Business Reinstallation DVD, yes, but the computer I have my problem with is an HP with the usual consumer Vista on it. I did use Dell's DVD in so far as I tried its repair mode, but it did not find anything wrong. And I was afraid to have it wipe the entire partition and reinstall Vista entirely, since I won't have the HP drivers. UNLESS-- this HP computer does have a Vista recovery partition on it. If I use the DELL Vista DVD to reinstall Vista, then would the HP recovery partition then be able to supply the HP drivers I need?

There is one caveat to all the above-- if I use the DELL reinstallation DVD, it will install Business Vista and not the consumer level Vista.

---

### Post by Didius Falco on 2009-05-09
No, I misunderstood your previous post - I though it came with the PC you are returning. Do NOT use that other DVD on it to restore - it'll likely cause a huge mess, as it will have the wrong drivers set up to install, etc.

And that's without even getting into the legal ramifications of doing that...

Yes, lets see that output - if there is a restore partition, you should be able to restore the PC to it's default state using that.

Did you get any kind of CD or DVD with that PC, or instructions on how to use the restore function?

Just as a side note, if I were going to buy a pre-built PC with a pre-installed O/S, I'd never accept one that didn't come with a regulation OEM install disk, or, at the very least, with a separate Restoration DVD.

Those hidden partition restores are just a way for the manufacturer to save a few cents per unit on their machines.

---

### Post by swarup on 2009-05-09
Here is the output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58928   473339128+   7  HPFS/NTFS
/dev/sda3           58929       60801    15044872+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```

> Did you get any kind of CD or DVD with that PC? 

No


> or instructions on how to use the restore function?

There is a printed manual that comes with the computer. I can look now to see if there are any instructions in it related with use of the restore partition.

And with regard to the DELL Vista DVD, I did use it once with my Dell computer. It appears to put a very generic version of Vista on the computer. And Dell gave me a totally separate DVD, containing all the Dell drivers. So for example, when I reinstalled Vista onto the Dell using the reinstallation DVD, initially there were no video or sound drivers, or wireless driver etc, and all those drivers had to be installed using the separate drivers DVD. So this is just by way of background info, just in case we end up perhaps needing to use this DELL DVD. But if we do use it, would it wipe out HP's restoration partition? Because I would need that restoration partition to re-setup all the HP drivers.

---

### Post by irv on 2009-05-09
I have a dell that came with vista and I installed Ubuntu on it. When I found that I had hardware issues I removed Ubuntu. I had the same problem but all I did was grab a XP disk I had and ran the MBR fix and it worked. The only problem I had was I still had my Linux partition which I just formated and am using it for Windows. I do have a hidden partition with the recovery so I could put it back to new.

Where else can you come for windows help but on a Linux forum.

---

### Post by presence1960 on 2009-05-09
> **swarup said:**
> Here is the output:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       58928   473339128+   7  HPFS/NTFS
/dev/sda3           58929       60801    15044872+   7  HPFS/NTFS
ubuntu@ubuntu:~$ 
```



No




There is a printed manual that comes with the computer. I can look now to see if there are any instructions in it related with use of the restore partition.

.

I hate to be the bearer of bad news, but from your fdisk -l output it appears you wiped your recovery partition. All you have are 2 NTFS partitions.

---

### Post by swarup on 2009-05-09
@ irv: When you say you ran the "MBR fix" from the XP disk, is that utility a specific, explicit "MBR fix" listed as such as an option on the XP disk? Because I did run the "startup fixit utility" from the Vist disk, and it couldn't find the problem. If the XP disk has a special MBR utility made just for fixing the MBR, then maybe it would work. (I do have an XP installation disk, although even then I don't know if it would have the same utility on it to which you refer.)

---

### Post by swarup on 2009-05-09
> **presence1960 said:**
> I hate to be the bearer of bad news, but from your fdisk -l output it appears you wiped your recovery partition. All you have are 2 NTFS partitions.

I believe sda3 *is* the recovery partition, isn't it? 

I don't recall there ever having been more than two partitions when the computer came.

---

### Post by Didius Falco on 2009-05-09
> **swarup said:**
> Here is the output:

There is a printed manual that comes with the computer. I can look now to see if there are any instructions in it related with use of the restore partition.

And with regard to the DELL Vista DVD, I did use it once with my Dell computer. It appears to put a very generic version of Vista on the computer. And Dell gave me a totally separate DVD, containing all the Dell drivers. So for example, when I reinstalled Vista onto the Dell using the reinstallation DVD, initially there were no video or sound drivers, or wireless driver etc, and all those drivers had to be installed using the separate drivers DVD. So this is just by way of background info, just in case we end up perhaps needing to use this DELL DVD. But if we do use it, would it wipe out HP's restoration partition? Because I would need that restoration partition to re-setup all the HP drivers.

Please do look for instructions in your manual.

It's hard to say if it would overwrite the restore partition. It's likely that it would, though it could be set up to restore a partition that would be the same size as the Hard Drive it had installed at the factory.

Personally, I wouldn't do it.

Looking at that readout, I do see two separate NTFS partitions. This is a good sign, because the second one is very likely the restore partition.

Please post the all the HP information - is it a laptop or a desktop and most importantly, the model number.

That way I can look up the exact instructions to restore it. I already have the HP website loaded, and I'm looking at the generic instructions, but I'd rather see the ones for your PC.

Once we have those, it shouldn't be too long before you have it restored.

Regards,

Didius

---

### Post by irv on 2009-05-09
> **swarup said:**
> @ irv: When you say you ran the "MBR fix" from the XP disk, is that utility a specific, explicit "MBR fix" listed as such as an option on the XP disk? Because I did run the "startup fixit utility" from the Vist disk, and it couldn't find the problem. If the XP disk has a special MBR utility made just for fixing the MBR, then maybe it would work. (I do have an XP installation disk, although even then I don't know if it would have the same utility on it to which you refer.)

The one for vista is Bootrec.exe and the one for XP is fixmbr as I remember either one will work.

---

### Post by presence1960 on 2009-05-09
> **swarup said:**
> I believe sda3 *is* the recovery partition, isn't it? 

I don't recall there ever having been more than two partitions when the computer came.

Hopefully I am wrong. Most recovery partitions I have seen are FAT not NTFS, So I hope I am incorrect so you can fix this. Check your documentation for which key to press when booting to use the recovery partition. If the partition is there and intact the process will begin.

---

### Post by neu2buntu on 2009-05-09
goto post num #19 [SIZE=4][COLOR=Red][here]("http://ubuntuforums.org/showthread.php?t=891118&page=2") [SIZE=1][COLOR=Black].i think this is the commands you need to run in the recovery console,using your recovery cd u downloaded[/COLOR][/SIZE][/COLOR][/SIZE]

---

### Post by swarup on 2009-05-09
@ Didius Falco: The computer is an all-in-one desktop computer i.e., the HDD, motherboard etc are all behind the screen in one body. The model is called, "HP TouchSmart PC IQ524"

---

### Post by presence1960 on 2009-05-09
I  found it on the HP site for your model- at boot press F11 to access the recovery process from the recovery partition.

System Recovery Options
You should attempt system recovery in the following order:
1  Through the hard disk drive, from the Windows Vista
Start menu.
2  Through the hard disk drive, by pressing the F11 key on
the keyboard during system startup.
3  Through recovery discs that you create.
4  Through recovery discs purchased from HP Support.
To purchase recovery discs, go to
[http://www.hp.com/support](http://www.hp.com/support) and visit the Software
& Driver downloads page for your computer model.
Starting system recovery from the
hard disk drive
Choose one of the following procedures to reinstall the
software from the recovery image on your hard disk drive:
&#8226;  Starting system recovery from the Windows Vista
Start menu
&#8226;  System recovery from system startup
System recovery from the
Windows Vista Start menu
If the computer is working, and Windows Vista is
responding, use these steps to perform a system recovery.
NOTE: System Recovery deletes any data or programs that
you created or installed after purchase. Therefore, ensure
you have backed up to a removable disc any data that you
want to keep.
1  Turn off the computer.
2  Disconnect all peripheral devices from the computer,
except the monitor, keyboard, and mouse.
3  Turn on the computer.
4  Click the Windows Vista start button, All
Programs, PC Help & Tools, and then click
Recovery Manager.
5  In the Recovery Manager Welcome window, click the
Advanced options button.
6  Click Recover your computer to its original
factory condition, and then click Next.

---

### Post by swarup on 2009-05-09
> **irv said:**
> The one for vista is Bootrec.exe and the one for XP is fixmbr as I remember either one will work.

When you put the Vista reinstallation or restoration disk in the computer, how would you access this Bootrec.exe? Remember, I cannot boot up anywhere in order to explore the DVD/CD. I can only use the options available on the menu when I put the DVD/CD in the computer and boot from it.

And same with the XP disk: is there a "fixmbr" option on the livecd menu?

---

### Post by Didius Falco on 2009-05-09
> **swarup said:**
> @ Didius Falco: The computer is an all-in-one desktop computer i.e., the HDD, motherboard etc are all behind the screen in one body. The model is called, "HP TouchSmart PC IQ524"

Okay, go to this web page. It tells you step-by-step how to restore from the hidden partition when you start up the PC.

If you've found the same instructions in your manual, you can just use that as a guide. Otherwise, print the linked web page out, or copy it by hand if you have to, and follow them exactly.

It doesn't look too complicated, but if you want to look them over first and ask any questions you have, I'll be around for a bit longer, and you have thousands of other users to help you out.

Here is hoping you soon have it restored!

[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00814731&cc=us&lc=en&dlc=en&product=3871946#c00814731_f11](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00814731&cc=us&lc=en&dlc=en&product=3871946#c00814731_f11)

Regards,

Didius

---

### Post by swarup on 2009-05-09
@ presence1960: I'm not sure, but I think I *may* have already tried F11 and nothing happened. I tried various buttons last night trying to access the recovery options-- not exactly sure if I tried the F11, but I might have.

Anyhow, I can exit from livecd (where I am now) and try F11. But I have a suspicion that for some reason it is not working now--although as I said earlier, I am 99.9% sure I did not wipe the restoration from the partition. All I removed was the extended partition containing Ubuntu and swap. 

That is why I am very interested in finalizing the info irv gave as to how to explicitly request the restoration DVD/CD to repair the MBR.

---

### Post by presence1960 on 2009-05-09
> **swarup said:**
> @ presence1960: I'm not sure, but I think I *may* have already tried F11 and nothing happened. I tried various buttons last night trying to access the recovery options-- not exactly sure if I tried the F11, but I might have.

Anyhow, I can exit from livecd (where I am now) and try F11. But I have a suspicion that for some reason it is not working now--although as I said earlier, I am 99.9% sure I did not wipe the restoration from the partition. All I removed was the extended partition containing Ubuntu and swap. 

That is why I am very interested in finalizing the info irv gave as to how to explicitly request the restoration DVD/CD to repair the MBR.

If F11 does not work then your recovery partition is not there or corrupted. I tend to think it is not there because they are usually FAT not NTFS.

---

### Post by swarup on 2009-05-09
> **neu2buntu said:**
> goto post num #19 [SIZE=4][COLOR=Red][here]("http://ubuntuforums.org/showthread.php?t=891118&page=2") [SIZE=1][COLOR=Black].i think this is the commands you need to run in the recovery console,using your recovery cd u downloaded[/COLOR][/SIZE][/COLOR][/SIZE]

Yes, after looking at this post #19 to which you refer, this looks like exactly what I need. I will try it.

For other readers, here is the nutshell of that post #19:

> Boot up your Vista Recovery CD that you downloaded and do following in the recovery console:

```
bootrec /fixmbr
bootrec /fixboot

```
That will replace the MBR with the Vista boot loader.

---

### Post by irv on 2009-05-09
Here are the instructions  Microsoft  Help and Support  
> To run the Bootrec.exe tool, you must start Windows RE. To do this, follow these steps:

   1. Put the Windows Vista installation disc in the disc drive, and then start the computer.
   2. Press a key when you are prompted.
   3. Select a language, a time, a currency, a keyboard or an input method, and then click Next.
   4. Click Repair your computer.
   5. Click the operating system that you want to repair, and then click Next.
   6. In the System Recovery Options dialog box, click Command Prompt.
   7. Type Bootrec.exe, and then press ENTER.

Note To start the computer from the Windows Vista DVD, the computer must be configured to start from the DVD drive. For more information about how to configure the computer to start from the DVD drive, see the documentation that is included with the computer or contact the computer manufacturer.
> Bootrec.exe options
The Bootrec.exe tool supports the following options. Use the option that is appropriate for your situation.

Note If rebuilding the BCD does not resolve the startup issue, you can export and delete the BCD, and then run this option again. By doing this, you make sure that the BCD is completely rebuilt. To do this, type the following commands at the Windows RE command prompt:

    * bcdedit /export C:\BCD_Backup
    * c:
    * cd boot
    * attrib bcd -s -h -r
    * ren c:\boot\bcd bcd.old
    * bootrec /RebuildBcd

/FixMbr
The /FixMbr option writes a Windows Vista-compatible MBR to the system partition. This option does not overwrite the existing partition table. Use this option when you must resolve MBR corruption issues, or when you have to remove non-standard code from the MBR.
/FixBoot
The /FixBoot option writes a new boot sector to the system partition by using a boot sector that is compatible with Windows Vista. Use this option if one of the following conditions is true:

    * The boot sector has been replaced with a non-standard Windows Vista boot sector.
    * The boot sector is damaged.
    * An earlier Windows operating system has been installed after Windows Vista was installed. In this scenario, the computer starts by using Windows NT Loader (NTLDR) instead of Windows Boot Manager (Bootmgr.exe).
> /ScanOs
The /ScanOs option scans all disks for installations that are compatible with Windows Vista. Additionally, this option displays the entries that are currently not in the BCD store. Use this option when there are Windows Vista installations that the Boot Manager menu does not list.
/RebuildBcd
The /RebuildBcd option scans all disks for installations that are compatible with Windows Vista. Additionally, this option lets you select the installations that you want to add to the BCD store. Use this option when you must completely rebuild the BCD.

---

### Post by swarup on 2009-05-09
> **Didius Falco said:**
> Okay, go to this web page. It tells you step-by-step how to restore from the hidden partition when you start up the PC....

Regards,

Didius

Just saw your post. Thanks very much for the helpful link. I will try it now. As presence1960 suggested, it does tell to start by pushing F11. So I will try that again. 

And if it does not work, then I will try to repair the MBR using the suggestions of neu2buntu and irv.

I will try these things now.

---

### Post by presence1960 on 2009-05-09
> **swarup said:**
> Just saw your post. Thanks very much for the helpful link. I will try it now. As presence1960 suggested, it does tell to start by pushing F11. So I will try that again. 

And if it does not work, then I will try to repair the MBR using the suggestions of neu2buntu and irv.

I will try these things now.

Hopefully one will work so you can return this thing to the store. Good luck, I'll keep my fingers crossed! :)

---

### Post by bennachie on 2009-05-09
You may already have resolved the problem - I can confirm that, in both my laptop (HP) and desktop (Lenovo), the recovery partitions are NTFS formatted, and respectively occupy 6GB and 4GB (the HP includes a lot more crapware in the "factory default" than the Lenovo). In both cases, I have messed around quite a bit with shrinking and later extending the Vista partition, without experiencing any serious problems.

However, I can only agree with those contributors who have characterised the recovery partition approach as being nothing more nor less than penny-pinching.

It seems obvious, particularly in comparison with all the sophisticated advice you have received, but have you tried using SuperGrubDisk to reset the MBR to standard Windows-only format?

---

### Post by swarup on 2009-05-09
It is fixed now-- boots perfectly into the original Vista that came with the computer. Many thanks to all of you who contributed your help and suggestions. I can only say that time and time again, this Ubuntu support forum and the people who participate in it are just so wonderful. This is not the first time nor the last, I am sure, that you people will come forward so cheerfully to save me. 

In the end, neu2buntu's suggestion worked perfectly. Here I am posting it again for any future readers:

> Boot up your Vista Recovery CD that you downloaded and do following in the recovery console:

```
bootrec /fixmbr
bootrec /fixboot
```

That will replace the MBR with the Vista boot loader. 

The above takes all of two seconds, and works perfectly. It is the same process as that detailed by Irv, for use with the Vista reinstallation disc. The info he posted from Microsoft in this regard, was also invaluable.

(I first tried the F11/recovery partition option, but it didn't work. I guess presence1960 and Didius Falco are right, that I must have inadvertently wiped something needed for recovery, from the drive.)

Again, many thanks to all!! :P

---

### Post by presence1960 on 2009-05-09
> **swarup said:**
> It is fixed now-- boots perfectly into the original Vista that came with the computer. Many thanks to all of you who contributed your help and suggestions. I can only say that time and time again, this Ubuntu support forum and the people who participate in it are just so wonderful. This is not the first time nor the last, I am sure, that you people will come forward so cheerfully to save me. 

In the end, neu2buntu's suggestion worked perfectly. Here I am posting it again for any future readers:

 

The above takes all of two seconds, and works perfectly. It is the same process as that detailed by Irv, for use with the Vista reinstallation disc. The info he posted from Microsoft in this regard, was also invaluable.

(I first tried the F11/recovery partition option, but it didn't work. I guess presence1960 and Didius Falco are right, that I must have inadvertently wiped something needed for recovery, from the drive.)

Again, many thanks to all!! :P

Glad you got it fixed, that way you can return it and get something you will enjoy using.

---

### Post by swarup on 2009-05-09
> **bennachie said:**
> It seems obvious, particularly in comparison with all the sophisticated advice you have received, but have you tried using SuperGrubDisk to reset the MBR to standard Windows-only format?

Thanks very much for the suggestion. caljohnsmith has written in his post on this link [http://ubuntuforums.org/showthread.php?t=891118&page=2](http://ubuntuforums.org/showthread.php?t=891118&page=2), in response to someone in the same situation as me, that "I don't think that is what computer_freak wants--if he uses the Super Grub Disk to repair his MBR back to Windows, it will put a Windows XP boot loader in the MBR, not Vista." So that SuperGrubDisk may not have worked for me. But anyhow everything is fine now, and thanks again for writing in.

---

