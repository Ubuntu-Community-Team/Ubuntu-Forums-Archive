---
title: "Help with installing/ downloading Ubuntu 10.10"
date: 2011-03-23
forum: New to Ubuntu
---

### Post by Bombcat on 2011-03-23
I can't seem to get Ubuntu 10.10 on my laptop. It is an inspiron 1525, intel(r) core 2 duo T8300 @2.40GHz [I don't know what this means, but that's what my computer tells me so it must be true].A couple of months ago I ordered the Ubuntu 10.10 desktop disk, but while waiting for it I download ubuntu to try. Now I can't to the ubuntu part of my computer and I also can't reinstall it using wubi.
Can anyone help me?

PS I'm pretty dumb with computers, also I haven't seen this problem on any forum yet.

---

### Post by samcot on 2011-03-23
How do you intend to install Ubuntu? For example, do you want to have only Ubuntu on this laptop, or are you thinking of a multiboot system with Windows and Ubuntu?

---

### Post by jfb112697 on 2011-03-23
Well you could try deleting your ubuntu partition via the windows part of ur drive, and what is the point of downloading a iso to try if you can do a web live or just nit order the official disk and burn it yourself

---

### Post by Bombcat on 2011-03-24
I'm trying for a dual boot. How do I delete the ubuntu partition?

---

### Post by RubenAlonzo on 2011-03-24
Can you see the Ubuntu partition in Windows? Try this...

Start Windows, then right click My Computer and click on Manage. 

Then click on Storage which will pop up on the left tree. It should show you all the partitions of your hard drive in a bar graph on the right.

I think, that you will have the option to reclaim that space if in fact the ubuntu partition shows up.

Afterwards if this fixes your problem, you can try a fresh install. Best of luck.

---

### Post by Elfy on 2011-03-24
If you've previously installed and want to reinstall you don't need to remove the existing install.

Boot the livecd, start the install - when you get to the partition section - choose manual or advanced - I can never remember which version has which wording anymore - then it will show you a list of your partitions.

Assuming that you;ve only installed once there will be one ext4 partition - you can overwrite it - select the partition - edit partition - format as ext4 and choose / as a mountpoint - save that and continue

---

### Post by samcot on 2011-03-24
I agree with forestpiskie, that you don't necessarily have to delete the existing Ubuntu partition(s). But first things first, because I don't want to make any assumptions: Are you still able to boot up the Windows OS? And, do you have an installation CD for Ubuntu 10.10? (The 32-bit version for your laptop)
 
Maybe someone here knows of a way to read all the partitions from Windows, but in my experience Windows can't read non-Windows partitions, although, like Ruben said, you can at least see the partitions in Disk Management, but it won't tell you it's Linux. Also, there are some good, free partition applications (such as GParted) that not only can see all the partitions but change them, too. But at this point I don't think we need that. The Ubuntu install CD should suffice for now.
 
You haven't yet said how you attempted to install Ubuntu. You mentioned that you tried Wubi as a way to reinstall, but what did you try before that? A Wubi install may be a better option for you, because you said that you're not a techie. Not that you need to be a techie to install a multiboot system, but that way is more complicated and has a greater risk of mistakes. With a Wubi install, you install while Windows is up and running. The other method of installing involves booting from the Ubuntu CD. If you boot with the CD, after about ten minutes of staring at a purple Ubuntu screen you will be asked to choose between "Try Ubuntu" and "Install Ubuntu." Choose install. The next screen will give you a summary of preparation requirements, but don't worry about this yet, just go "Forward." The next screen is partitioning. You may (or may not) have 3 choices: Install alongside other operating systems; Erase and use the entire disk; Specify partitions manually (advanced). Click on the third option. On that screen, you're going to see all of your partitions, including those used for Windows. The Windows partitions are the ones with ntfs formatting. If you have any Linux partitions, you will see ext2, ext3, ext4, or swap partitioning. This is the information you need to post, so we can help you figure out where you are and where you need to go. 
 
For example, a multiboot disk with Windows and Ubuntu may look like this:
 
/dev/sda
  /dev/sda1 ntfs    208 MB (size) unknown (used)
  /dev/sda2 ntfs    199950 MB (size) 47997 MB (used)
  /dev/sda3 ext4   7956 MB (size) 3703 MB (used)
  /dev/sda5 swap   5240 MB (size) 0 MB (used)
  /dev/sda6 ext4    36699 MB (size) 868 MB (used)
 
After you view that information and write it down, post it in here. You can quit the installation at this point.

---

### Post by Bombcat on 2011-03-25
to samcot: I do have the livecd and I can still boot with windows
You aksed what I tried before Wubi, I first installed ubuntu with wubi and I was just using the 'try me' mode, but then I got a live cd. The live cd got rid of the option to get to the 'try me', and after that I tried using wubi again.

I'm about to try booting from the livecd again so I'll report back with any news

---

### Post by Bombcat on 2011-03-25
Ok I just tried booting from the livecd and here is what happened:
It got to the purple screen and stayed there for about 5 minutes and then it went to a black screen for 10 minutes until it showed this message:

BusyBox v1.15.3 (ubuntu1:1.15.3-ubuntu 5) built in shell (ash)
(initramfs) mount: mounting /dev/loop0 on//filesystem. sqaushfs failed: input output error
Can not mount /dev/loop0 (/cdrom/casper/filesystem.squashfs)on file system .squashfs
udevd[911]: worker [218] returned with status 0x0100
udevd[911]: worker [218] failed handling '/devices/virtual/block/loop0

and that's it

---

### Post by samcot on 2011-03-26
Sorry it took so long to get back to you, I got busy at work. Keep in mind I'm a noobie like yourself, so when something isn't working right like this, you're better off if someone with more experience can help out. But until the calvary arrives, perhaps we can try some things.
 
First, I don't think it's normal to go from the purple screen to a black screen. At least, that never happened to me, and I've run the install several times now. After the purple business is over (5 to 10 minutes), you should start getting some menus. And while I'm not really sure what to make of the information output you posted, I can't help but notice the reference to mounting the CDROM, so I wonder if that means there is some issue with it, or perhaps with the CD itself? 
 
When you booted from the CD, can you tell me how you did that? For example, is the BIOS of your laptop set to look for a boot from the CD drive before it boots from the hard disk, or do you boot from the CD manuallly, by pressing F12 on your laptop, (I think), and then choosing the CD as the boot device? Also, is the Ubuntu CD you have the one you ordered, or did you make it yourself from a download?
 
The next step we try will depend on your answers to these questions. And if worse comes to worse, we might try to use the partition application I mentioned earlier, GParted. But not quite yet. 
 
And someone who is more knowledgeable might join in and give you better suggestions! But I think we can make progress either way. :-)
 
Oh, one more thing that I should ask: You said that you had done a Wubi install from within Windows. Did you delete that, or is it still there? If it's still there, I wonder if it can interfere with other kinds of installs. I suppose it's possible to have a Wubi install and also have Ubuntu installed on its own partition, but I don't know.

---

### Post by Dutch70 on 2011-03-26
If you want to install Ubuntu into a separate partition. First make sure you have gotten rid of anything to do with Wubi.

Check the md5sum of your downloaded .iso
[[COLOR="RoyalBlue"]HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM")
Check the integrity of your disc.
[[COLOR="RoyalBlue"]CDIntegrityCheck[/COLOR]]("https://help.ubuntu.com/community/Installation/CDIntegrityCheck?action=show&redirect=CDIntegrityCheck")
If either of these show errors, fix that first. It is recommended to burn the .iso at the slowest speed possible.

When you boot the live cd, select "Try Ubuntu" before installing to make sure you will be satisfied with how it runs on your machine before installing.

If you get a black screen when trying to run the live cd. You may need to choose nomodeset to get around this.
[[COLOR="RoyalBlue"]http://ubuntuforums.org/showthread.php?t=1613132[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")
[[COLOR="RoyalBlue"]http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html[/COLOR]]("http://ubuntu4beginners.blogspot.com/2011/01/ubuntumaverick-blank-screen-problem.html")

It's best not to choose the side by side install if your installing version 10.10, choose "manual"

I recommend you prepare your hdd before installing. You'll need a Swap partition equal to the size of your physical RAM. 
and the rest of your free hdd for "/" aka "root". 
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/HowtoPartition[/COLOR]]("https://help.ubuntu.com/community/HowtoPartition")

I don't know what all you've done with your computer, but it may be a good idea to run check disk after completely removing Wubi & before installing Ubuntu. 

It's all a lot simpler than it may appear in this post, I just wanted to give you some good info for back up.

---

### Post by Bombcat on 2011-03-26
The cd boots automatically and wubi is still installed. Do you think that by uninstalling wubi the cd might work?

---

### Post by Dutch70 on 2011-03-26
Wubi would be on your hdd. When you boot from the cd, it shouldn't be reading anything from your hdd. So it shouldn't make any difference.

It's not a good idea to install Grub if you have Wubi installed.

---

### Post by samcot on 2011-03-26
It looks like you've got a pro helping you now! If your laptop automatically boots from the CD, that must mean that your BIOS is set to do that. But are you using the CD that you ordered, or are you using a CD that you burned yourself? Dutch mentioned how burn speed can affect quality. I like to use the free ISO burning utility called BurnCDCC. You can download it and start using it right away on your laptop, in Windows. Also, at this point it may be a good idea for you to download the GParted partition utility I told you about (which is also an ISO that will have to be burned to a CD).
 
If Dutch says that it's not a good idea to install GRUB if Wubi is installed, I'm tempted to suggest that you should uninstall Wubi. GRUB will give you a nice boot menu once you've got a multiboot system.
 
Hang in there!

---

### Post by Dutch70 on 2011-03-26
Sorry samcot, I'm far from a pro. Having a lot of post doesn't make you a pro ;). My best experience is that I've gotten pretty good with Google.

Bombcat, did you want a Wubi install? That is basically installed directly into windows programs, like any other program you install in windows, It can also be uninstalled the same way. 
That about sums up my knowledge of Wubi.

Once you have Grub installed, it's not quite as easy to get rid of if you change your  mind. Just make sure Ubuntu runs to your satisfaction, on  your hardware, by choosing "Try Ubuntu" from the live cd/usb.

---

### Post by Bombcat on 2011-03-28
the livecd is one that I ordered from ubuntu (or whereever it comes from) so that shouldn't be a  problem.
I just uninstalled wubi but I haven't had a chance to try booting from the cd but I'll post what happens

---

### Post by Bombcat on 2011-03-30
Ok i tried booting from the livecd after I uninstalled wubi.
I still went to a black screen and it didn't work, but instead of saying udevd[911]: worker [218] failed, it said that some other worker failed.
I don't know if that makes a difference; it's just something I noticed

---

### Post by Dutch70 on 2011-03-31
Not sure about the error you're getting, but did you try nomodeset or other settings from the link I provided?

---

### Post by Bombcat on 2011-03-31
Dutch, I read your links, but as far as I could tell I need the somewhere to but in the nomodeset. Should I put in in when then screen goes black and shows the driver errors?

---

### Post by Dutch70 on 2011-03-31
If you've checked the md5sum & the cd integrity check, then I really don't know what to tell you on that one. 
Hopefully someone else will have an idea on what to do with that.

Are you not getting to the screen with the little man at the purple screen?

---

