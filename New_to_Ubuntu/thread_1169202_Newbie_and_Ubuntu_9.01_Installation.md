---
title: "Newbie and Ubuntu 9.01 Installation"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by g767300 on 2009-05-24
First I am brand new to Linux and Ubuntu. Second I hope this is the right way to ask question on beginners thread?

I have Dell laptop with Windows Vista Premium (all current), McAfee Security and Dell 305 wireless printer, scanner with Dell provided Linksys router. Internet is ATT Wireless Broadband (Read Slow). Long time Windows user (since DOS) not OS geek but am application designer who finally decided on learning about OS and Linux was the choice.

My first attempt to check out Ubuntu 9.01 was with LiveCD. I got it running and second time it started I discovered it was installing Ubuntu.  Foolishly I let it go ahead but I am not at all sure I have good installation. It is dual boot with windows on its own partition(I think). Windows has two partitions one for OS (regular win installation) the other Windows factory install image 

How do I check to see if I do have good installation?

If so need lots of guidence on how to connect to my printer. Lets try direct connect first. If that works then we can deal with wireless.

If I need to reinstall as dual boot how do I get rid of existing Ubuntu partition without disturbing windows?

All help appreciated

g76700

---

### Post by lisati on 2009-05-24
1) When you restart your computer, do you get an option to choose between Ubuntu and Vista? If so, does choosing Ubuntu let you use Ubuntu? (That's the best way of seeing if your installation worked)

2) 9.01? Do you mean 9.04?

---

### Post by powel212 on 2009-05-24
To check if Ubuntu is installed just reboot. 

On reboot you should see a screen with some boot options;

jaunty
mem test
windows boot loader


If you don't see this on reboot then Ubuntu was not installed successfully.

If you do see this just use the arrow keys to choose your boot OS

Powel

---

### Post by powel212 on 2009-05-24
Setting up a Win Ubuntu Dual boot the clean way.

You are familiar with windows so I suggest using the win partitioner to set up your partitions before installing.


You have 2 existing partition and you need to create a 3rd empty partition. Use the "Windows Computer Manager - Disk management tool" to configure your partitions.

Create the partition for Ubuntu.

Leave the new partition unformatted as a blank partition, This is most important, do not format the new partition just leave it blank.. We will deal with it later. Apply changes.

Insert the Live CD and Reboot

Insert your Ubuntu "Live" CD and boot from it "try Ubuntu without changes to my computer"

Once booted and running from the Live cd, chose install.

enter the appropriate information, country, language etc but when you arrive at the partition screen you will have a choice where to install Ubuntu.

This is the important part and this is why we left that unformatted space before. You can now chose to install Ubuntu to "the largest continuous free space" In doing so Ubuntu will now install to the empty space we left unformatted. Do not adjust the slider. Ubuntu will only install to the empty space we made before and will leave your windows alone.

Allow the rest of the install to run and reboot.

Upon reboot you will be greeted with Ubuntu's Grub screen where you will be given a short list of options to boot from. there will be Ubuntu at the top and Windows at the bottom. Just use the arrow keys to select the system you want to boot.

Now you are almost done. But once you have booted into Ubuntu for the first time from the hard drive you won't see the Win partition on your desktop so we need to install a little applet so all your partitions will be mounted automatically.

Go to "Applications-Add/Remove...

Change the box at top that says "show" from "Conical-maintained-applications" to "All available applications"

Than type into the search box "NTFS"

in a second or 2 you will see a program called NTFS configuration tool.

Put a check in the box beside it and then apply changes.

Close Add/remove

Then go to "Applications-System_Tools-NTFS Configuration tool"

if it is not there try

"System-Administration-NTFS Configuration tool"

After launching the tool just check the boxes next to; enable read and write to internal and external drives.

the next time you boot all your drives will appear on the desktop.

I hope that helps.

Powel

---

### Post by g767300 on 2009-05-25
Powel:

First thanks for your reply and to all the others who replied.

The install instructions look good. How do I safely delete the existing Ubuntu partition w/o endangering windows 2 partitions?

Thanks,

Gary

---

### Post by powel212 on 2009-05-25
As you are most familiar with windows I would recommend using the windows disk management tool to delete the Ubuntu partition and as I mentioned before leave the space empty and unformatted.

To open the disk management tool. In win click start then right click "My Computer" and select Manage then choose Disk Management under Storage

6Gigs is enough space for Ubuntu, (as a trial)
10Gigs is better
20Gigs is what I recommend if you can afford the space.


See attachments for more details on the win disk manager.

It should be easy to spot the Ubuntu partition because it won't have a drive letter and it will just say "Healthy Partition"

Note:
Ubuntu also has a great disk partitioner on the live CD but I remember my first time using I found it a bit confusing. You might want to give it look next time your running the live CD, look under - System-Administration-Partition Editor

---

### Post by powel212 on 2009-05-25
Here is what the partitioner looks like in Ubuntu. It is a great and powerful tool but takes some getting used to.

Once you get comfortable with Ubuntu keep in mind that you can run Windows in a Virtualbox inside Linux so you don't have to reboot. But that comes later. For now just get familiar with Ubuntu and enjoy it.

Powel

---

### Post by g767300 on 2009-07-03
powel212: I fat fingered something!

Followed your instructions for dual boot install work well. Used same user name and pw as windows easy for me. Even copied it. But now UBUNTU won't let me log in. How do I remove Ubuntu and start over??

Information that might impact your answer:
1) Windows partition manager by the time I got to install last night showed  partition/s:
      a)Healthy (EISA Confirguration) Layout:Simple, Type: Basic, file system Blank, Capacity 39mg    free space 100% (This was not there when we exchanged messages in May Right click only shows help which is no help. Quick Google - apparently remement of XP.  Only thing I have added is Google toolbox to Windows)
      b) C: simple, basic, NTFS Healthy,(windows, boot etc) 172GB, free 67%
      c) D: Recovery same  9.8 GB free 45%
      d)  No name1 39MB 100% free (this is the one I created for Ubuntu)
      e) No name2 2.14 GB 100% free. This existed at the time of our last message exchange.

I followed ur "script" everything went well no errors. Only goof I made other than fat fingering user name or pw was I forget to install applet that shows all files.

I created the no name1 39GB above by using windows partitioner and shrinking the windows partition by by ~ 50GB less than the allowable per windows.

Where is Ubuntu? Can I just delete the two free partitions and start over? When laptop starts I get the screen with the usual Ubuntu options and windows "booter" which takes me to the screen Ubuntu created when it "installed itself" the first time.

I am using a disc (I think I found source or Link fro Ubuntu.org) from OSDisc.com Ubuntu 9.01 Disc 1(there was only 1) Install/Live CD Platform PC.


All Help appreciated.

g767300

---

### Post by annie227 on 2009-07-08
So g,I'm a newbie too and am finding this post very helpful.
How'd you go?
Got any hints?-I have a pc with 2 HD's 160G ide with XP and wubi installed 9.04(32) and a secondary 500G sata,wanting to install ubuntu on the 500,maybe..........

---

### Post by g767300 on 2009-07-10
> **annie227 said:**
> So g,I'm a newbie too and am finding this post very helpful.
How'd you go?
Got any hints?-I have a pc with 2 HD's 160G ide with XP and wubi installed 9.04(32) and a secondary 500G sata,wanting to install ubuntu on the 500,maybe..........

annie: I am afraid I won't be much help.  I had trouble getting clean install and messed up MBR.  SOOO had to reinstall Windows(running dual boot). Trying to decide next move

g767300
:lolflag:

---

### Post by Zogh on 2009-07-10
Hi!

I too have been in the situation wheere I needed to uninstall ubuntu completely to get a fresh start.

The program i used to help me is called bootitng. Basically you can burn it to a cd and use it to remove the partitions you like and restore the MBR afterwards to kill off Grub so that Windows can boot up again without trouble.

More information about how you use it and where to download it can be found in this thread
[http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630)

The information in that thread really saved me when i experimented a lot with ubuntu during the first few days, more or less destroying my installations during the process. the program allowed me to reinstall ubuntu again and again without any hazzle.

You run the program, you have it make you a bootable CD. When you've loaded up the program from the cd you use it to format the partitions (exept those containing any user data that you want to keep and windows)
When done formatting you select the old windows partition -> select the button "view mbr"  -> select the button "Std MBR".

This will restore your old (windows) boot option.

I hope this tip will help you with experimenting with ubuntu without hazzle.

---

### Post by g767300 on 2009-07-12
Zogh:

Thanks, I will read the reference [http://ubuntuforums.org/showthread.php?t=113630](http://ubuntuforums.org/showthread.php?t=113630) and proceed from there.  Do you know if this will work with 8.xx and 9.. at least the stable versions?

Also any advice on finding Linix device drivers for Dell Wireless Printers, ATT Sierria USB devices and Linksys wireless routers. I have/will check vendor sites but ATT told me yesterday that they don't support Linix but there are "drivers" out there that work.

Thanks,

g767399:razz:

---

