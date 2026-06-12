---
title: "dual booting"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Jack Shankle on 2009-01-12
I tried loading Ubuntu once before and had to remove it because
I can't be days without my email and online stuff  while I'm trying to figure this out. I want to use Firefox and Thunderbird in Ubuntu as I am using them in Windows Vista. The last time I couldn't boot into windows. What I mean by that is access to the Windows desktop as I see it without Ubuntu installed. I know I can see the files from Windows in Ubuntu but that's not what I want. The selection menu in Ubuntu presented the option but I could never get there.
My setup is drive 1 sata with Windows Vista.
I want to put Ubuntu on drive 2 sata with Ubuntu. Really want to be able to boot from windows to Ubuntu or vice versa. Would like to have the two OSes totally isolated from each other. I have a CD of Ubuntu and probably will have no trouble installing Ubuntu. That's probably as far as I will get.
That's why a program like System Commander by Avanquest would
give me the option of having two isolated OS on the same Puter
and be able to boot to either one at will.
Also I have done a lot of reading and can't seem to find answers to these questions.
1% Ubuntu working on 2% Ubuntu.
Thanks for any guidance.

---

### Post by skern03 on 2009-01-12
> **Jack Shankle said:**
> I tried loading Ubuntu once before and had to remove it because
I can't be days without my email and online stuff  while I'm trying to figure this out. I want to use Firefox and Thunderbird in Ubuntu as I am using them in Windows Vista. The last time I couldn't boot into windows. What I mean by that is access to the Windows desktop as I see it without Ubuntu installed. I know I can see the files from Windows in Ubuntu but that's not what I want. The selection menu in Ubuntu presented the option but I could never get there.
My setup is drive 1 sata with Windows Vista.
I want to put Ubuntu on drive 2 sata with Ubuntu. Really want to be able to boot from windows to Ubuntu or vice versa. Would like to have the two OSes totally isolated from each other. I have a CD of Ubuntu and probably will have no trouble installing Ubuntu. That's probably as far as I will get.
That's why a program like System Commander by Avanquest would
give me the option of having two isolated OS on the same Puter
and be able to boot to either one at will.
Also I have done a lot of reading and can't seem to find answers to these questions.
1% Ubuntu working on 2% Ubuntu.
Thanks for any guidance.

Dual booting Ubuntu and Windows is pretty easy. I haven't done it with Vista, but have it running on two machines with XP. Here's what I did:

Download and burn the latest version of Ubuntu (sounds like you already have).
Put the CD in your drive, and restart your system. Make sure that the BIOS is set to boot first from the CD.
When the CD starts up, you'll get a language selection. Pick your language. You'll then get a menu. One of the choices is Install. Note that you can also hit F6 to enter other options. Sometimes install fails; if it does, hit F6 and type "noacpi" (without quotes).

Select install, and follow the prompts to select keyboard, etc. Eventually, you'll get to a screen that sets up partitions. Make sure you select MANUAL. Do NOT use guided install (this is just my opinion, no doubt others will disagree).

For the partition, select your second SATA drive. This is exactly how i have mine set up - my IDE drive (hd0) has XP, my SATA has Ubuntu. Set the partition table up like this AND in this order:
[LIST=1]
[*]15-20 GB for the root (this is displayed as "/"). Mark it to be formatted, and set the file type to ext3 Journaling Filesystem.
[*]2 GB for Linux swap file (there's no formatting option)
[*]The rest (or however much you want) should use /home as the mountpoint. This too should be ext3, and set to format.
[/LIST]
The end result of this will be a boot menu upon startup that will give you choices of Ubuntu and Windows.

That's the basics... post back and ask away if this doesn't make sense.

---

### Post by cozmicharlie on 2009-01-12
I'm a little lost in what you are trying to do.  Just so I am sure what you want could you answer these questions.

Do you now have windows installed on drive 1?
Do you have Ubuntu installed on either drive 1 or 2?
Do you want to dual boot with Windows on drive 1 and ubuntu on drive 2?
You state ultimately you want to be able to access windows from ubuntu and vice versa - does this mean you want to be working in Windows and be able to open and use Ubuntu from Windows or do you want to just be able to access Ubuntu files from Windows?

Once you answer these questions I can offer better help.  But, in the meantime I think this might help:

Yes, you can dual boot with Windows and Ubuntu on different drives.  It is best to install Windows first then Ubuntu since Ubuntu will set up Grub.  Alternately you could use a program like True Image (acronis.com)or as you suggest, System Commander to act as the boot manager.  Though Grub is perfectly capable of doing this.  
No you can't dual boot and be able to access Windows from Ubuntu.  To do that you would need to set up something like virtual box with either a windows host and ubuntu guest or a ubuntu guest and windows host then enable the virtual box add-ons so you have seamless integration.

---

### Post by Jack Shankle on 2009-01-12
Thanks guys for helping. 
To skern03.
I already have Vista set up on HD 1 which is HD0.

To cozmicharlie.
I will try to answer your questions:
1. I have Vista installed on drive 1.
2. I will install Ubuntu on Drive 2.
3. yes I want to be able to dual boot Vista on Drive 1 and      
   Ubuntu on drive 2.
4. No. I want to boot into Vista and work on Vista. Or boot into
   Ubuntu and work in Ubuntu. Don't want them together.
   This a crutch for me until I get used to Ubuntu then byebye
   Microsoft and all its goodies. 
5. Will have a learning curve with Grub but am halfway   
   skilled with system commander.
If you need any more info I will be most happy to reply.

1% Ubuntu working on 2% Ubuntu

---

### Post by skern03 on 2009-01-13
> **Jack Shankle said:**
> Thanks guys for helping. 

5. Will have a learning curve with Grub but am halfway   
   skilled with system commander.


When you get Ubuntu going, either open a terminal (Applications, Accessories, Terminal) and enter:
sudo apt-get install startupmanager

Or load the program from Synaptic (System, Administration, Synaptic Package Manager).

This gives you a GUI front-end to GRUB (Grand Unified Boot loader). It is NOT necessary, but you can make it prettier and control the number of entries that appear, etc. Truthfully, there's really nothing you need to learn about GRUB.

---

### Post by handydan918 on 2009-01-13
+ 1!!
DO NOT shy away from grub in favor of some proprietary, third-party software! It will not be supported on the forums! If you stick with grub, there are many experts here who can walk you through any problems you may encounter. 

Although, I gotta say, for me, grub has just worked at least 99% of the time...

---

### Post by kansasnoob on 2009-01-13
> **Jack Shankle said:**
> I tried loading Ubuntu once before and had to remove it because
I can't be days without my email and online stuff  while I'm trying to figure this out. I want to use Firefox and Thunderbird in Ubuntu as I am using them in Windows Vista. The last time I couldn't boot into windows. What I mean by that is access to the Windows desktop as I see it without Ubuntu installed. I know I can see the files from Windows in Ubuntu but that's not what I want. The selection menu in Ubuntu presented the option but I could never get there.
My setup is drive 1 sata with Windows Vista.
I want to put Ubuntu on drive 2 sata with Ubuntu. Really want to be able to boot from windows to Ubuntu or vice versa. Would like to have the two OSes totally isolated from each other. I have a CD of Ubuntu and probably will have no trouble installing Ubuntu. That's probably as far as I will get.
That's why a program like System Commander by Avanquest would
give me the option of having two isolated OS on the same Puter
and be able to boot to either one at will.
Also I have done a lot of reading and can't seem to find answers to these questions.
1% Ubuntu working on 2% Ubuntu.
Thanks for any guidance.

Well GRUB can be a bit tricky, especially when you have operating systems on more than one hard drive, you can read some about it here:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)

I know nothing about System Commander, but I've actually used EasyBCD by Neosmart Technologies as described as the latter option here:

[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=4)

It worked fine for me.

---

### Post by skern03 on 2009-01-13
> **kansasnoob said:**
> Well GRUB can be a bit tricky, especially when you have operating systems on more than one hard drive...

I mean no disrespect... and you're right in that there are a lot of posts about problems with grub. But as handydan918 points out, there are a LOT of folks who will help here.

I'm a big fan of keeping OS's on separate drives, as the OP plans. The only hassle I've ever had with grub was from a hard crash on my XP installation. But that would have caused problems even if both OS's were on the same drive.

---

### Post by Jack Shankle on 2009-01-13
Thanks guys for replying.
This is coming to you via Ubuntu.
Firefox and my Bookmarks are intact. However Thunderbird is another story and my emails from the Windows OS are still there. At the present time I cannot access my email. I sure hate to take Ubuntu back off just to read my Email. I also can not boot into Windows Vista. Which means I am an idiot and have done something or some things wrong. I did download all the updates thinking that would make a difference.
To Skern03 : I will do the startupmanager thing and see what happens.

Also this forum has been down and I have had to sign in half a dozens times. It keeps logging me off.
Just for infos sake.

1% ubuntu working on 2% ubuntu

---

### Post by skern03 on 2009-01-13
> **Jack Shankle said:**
> Thanks guys for replying.
This is coming to you via Ubuntu.
Firefox and my Bookmarks are intact. However Thunderbird is another story and my emails from the Windows OS are still there. At the present time I cannot access my email. I sure hate to take Ubuntu back off just to read my Email. I also can not boot into Windows Vista. Which means I am an idiot and have done something or some things wrong. I did download all the updates thinking that would make a difference.
To Skern03 : I will do the startupmanager thing and see what happens.

Also this forum has been down and I have had to sign in half a dozens times. It keeps logging me off.
Just for infos sake.

1% ubuntu working on 2% ubuntu

Yeah, sounds like they took a hard db crash. Been offine the better part of the past 24 hours.

Regarding thunderbird, I have it set up to share the same fileset, so that when I boot up in Windows or in Ubuntu, I get the same mail. I haven't figured out how to sync contacts, other than to do an LDIF export/import from the address book. Nor have I figured out how to import the account settings - unless that happens when you import an account when setting up Ubuntu (which I elected not to do).

All you need to do is from Windows, find out where your Thunderbird local folders are stored. It's usually in a path like this:
```
Documents and Settings/<*account name*>/Application Data/Thunderbird/Profiles/<*5xhwbl5c*>.default/Mail/Local Folders

```
In Ubuntu, set up your account, and point to the same folder on your legacy Vista drive. The path will have /media/<drive name> in front of it in the dialog box.

Let me know if you get stuck. You might have to click on the Vista drive icon before you launch thunderbird so that it's aware of the drive. I know there's a way to automount the legacy drive, but I've been too lazy to figure it out ;-).

---

### Post by 2hot6ft2 on 2009-01-13
I have used System Commander on a few pc's over the years and I found it to just be a pain. Don't expect it to work flawlessly. I've removed it and hope to never use it again. Used versions 7,8, and 9 they're all pretty much the same.

Back your stuff up before using it as I've had to recover partitions after using it, even deleting some and starting over without it. It's temperamental at times. Fair warning. Good luck.

SC9 is sitting in a folder right now and is not installed on any of my machines.

---

### Post by Jack Shankle on 2009-01-14
Thanks guys for all the help.
This epistle is coming to you by way of Ubuntu. So I am up and downloaded my updates and updated Firefox.
I can now boot into my Windows Vista on HD 0 sata and boot into Ubuntu
on HD 1 sata. It was a 10 hour struggle but I guess it's worth it. Couldn't
have done it without all the valuable tips from you guys, 
I have another Windows Vista partition on HD 0 that I can't access but
I think it has something to do with the way I coded the Multi-Entry menu.lst. The ex: from Neosmart didn't cover that and I had to guess.
Without easybcd and Neogrub it would have been impossible IMHO. Now the Thunderbird hassle and getting email from Windows Thunderbird into Ubuntu Thunderbird. 

1% Ubuntu working on 2% Ubuntu

---

### Post by Jack Shankle on 2009-01-16
Thanks for any help.
This is the code I used for booting into Windows Vista and Ununtu.
On HD 1(SATA) I have 2 partitions both of which are Vista Business.
On HD 2(sata) I have 1 partition with Ubuntu.
With the code below I can switch between Vista 1 and Ubuntu.
I cannot switch to Windows Vista 2.
This ex: came from NeoSmart and I have modified it for a 2nd Vista
boot. It does NOT work. I'm thinking it might have something to do
with the Windows Vista names. The loader lists both names the same.
I had to guess how to modify the code for the 2nd partition of Vista. 

# NeoSmart NeoGrub Bootloader Configuration File

#

# This is the NeoGrub configuration file, and should be located at C:\NST\menu.lst

# Please see the EasyBCD Documentation for information on how to create/modify entries:

# [http://neosmart.net/wiki/display/EBCD](http://neosmart.net/wiki/display/EBCD)

default 0     # pick the task to be run if the user doesn't pick one

              #  within the time limit

timeout 10    # give the user 10 seconds to choose a task



# we use the "title" keyword to indicate a new entry in the menu

title      Windows Vista    #this is our first entry - it's number 0

find --set--root /ntldr     #search for ntldr on all partitions. Once                                     

                            #found, use that partition as root

makeactive                  #make this the active partition

chainloader /ntldr          #run ntldr, the Windows Vista bootloader

# if we're using a menu, we don't need to use the "boot" command - it's

#  automatically implied.



#this is our SECOND entry    

title      Windows Vista Home basic    #this is our second entry - it's   

                                       # number 1

find --set--root /ntldr     #search for ntldr on all partitions. Once                                     

                            #found, use that partition as root

makeactive                  #make this the active partition

chainloader /ntldr          #run ntldr, the Windows Vista home      

                            #bootloader

# if we're using a menu, we don't need to use the "boot" command - it's

#  automatically implied.



#this is our THIRD entry    

title      Ubuntu           

root       (hd1,0)          #load Ubuntu from the 2nd HD partition

#next line: translate (hd1,0) to linex notation and set that as the #root partition

kernal     /boot/vmlinuz-2.6.22-14-generic root=/dev/sdbc

initrd     /boot/initrd.img-2.6.22-14-generic

#end Ubuntu entry


1% Ubuntu working on 2% Ubuntu

---

