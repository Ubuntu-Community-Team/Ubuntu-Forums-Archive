---
title: "Problems Dual Booting"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by wickid_ninja on 2011-05-11
Hello All!

I am hoping somebody help me out here, I have been a windows user for quite some time, and would like to dual boot 7 with ubuntu 11.04.  
I created a live dvd of ubuntu 11.04 64 bit from the website, and it seemed to work.  I loaded it to give it a whirl and it booted up fine, runs good. After booting from the dvd, I went back to windows and I created a 60 gig partition of unallocated space from windows 7 disk management as i thought i needed to.  I then reboot and load the dvd of ubuntu and select install.  When the "allocate drive space" screen comes up, I am supposed to have a few options to work with, but instead I have a blank window and cannot select anything except install, but it tells me that i have "no root file system is defined".  I can right click the blank white screen above and "revert", but I do not want to risk loosing my windows 7 if this is what it will do.  

I am at a loss of what to do, I have searched google to try to find solutions with no luck.
Sorry if this is lacking in information, I am writing this quickly as I must leave for work.  Please let me know what other details are relevant and needed to help me solve this problem.

---

### Post by seawolf167 on 2011-05-11
Welcome to the forums!

I know it's a little late now, but I always suggest backing up with [Clonezilla ]("http://www.clonezilla.org")before you try anything that might break your computer.

The official how-to for dual booting Windows and Ubuntu is [here ]("https://help.ubuntu.com/community/WindowsDualBoot")as well.

On to your issue, it sounds like you didn't properly set the mount point when going through the install prompts. Since you have just finished installing, IMO the easiest thing to do would be to reinstall with your Ubuntu LiveCD.

Put it in, then when you come to the screen that asks how to install Ubuntu, you can select "Manual Partition".

Once here:

[LIST]
[*]allocate 2GB (4GB max) to swap, formatted and mounted as swap.
[*]allocate 10GB to / (root), formatted as ext4 and mounted at /
[*]allocate the remainder to /home, formatted as ext4 and mounted at /home
[/LIST]
Reboot and you should be good to go.

This is of course only one simple partition table, let us know how it goes.

---

### Post by wickid_ninja on 2011-05-11
I did backup everything before attempting, thanks :).
Like I said, booting from the disc went fine, but I cannot seem to actually install Ubuntu.
When I select "install", and navigate through the screens, I do not see the option to "manually partition"... So its not that I need to reinstall, I cannot install in the first place.  
You mentioned "mount point"... I am not sure where I had that option (I cannot check atm as I'm currently at work, and my PC is at home) but I think that is the screen I got stuck on... It had some options at the top of the window, but they were unclickable.  
How do I change the mount point?  
Thanks for replying, and excuse the (probably) simple question...

---

### Post by wildmanne39 on 2011-05-11
> **wickid_ninja said:**
> I did backup everything before attempting, thanks :).
Like I said, booting from the disc went fine, but I cannot seem to actually install Ubuntu.
When I select "install", and navigate through the screens, I do not see the option to "manually partition"... So its not that I need to reinstall, I cannot install in the first place.  
You mentioned "mount point"... I am not sure where I had that option (I cannot check atm as I'm currently at work, and my PC is at home) but I think that is the screen I got stuck on... It had some options at the top of the window, but they were unclickable.  
How do I change the mount point?  
Thanks for replying, and excuse the (probably) simple question...

Hi, it sounds like you might have a problem with the installation cd. You might should download and make another live cd. I hope this helps.:)

---

### Post by thinkren on 2011-05-11
Ninja, 

My still on-going cautionary tale of woe, may help you avoid a potential headache, especially as it may pertain to clonezilla.

[http://ubuntuforums.org/showthread.php?t=1755070](http://ubuntuforums.org/showthread.php?t=1755070)

Very quickly if you don't have time to read the whole thread:

*If you are not careful using Disk Management to modify your partitions, Windows 7 will convert your HD from "basic disk" to "dynamic disk".  Windows itself will work just fine with dynamic disk, but it can't be used in a dual boot system.  

*"Dynamic Disk" is also not supported by clonezilla.  If you are not vigilant, you'll end up in the same unfortunate situation as I: You've created a set of images that has all you data, but can't be restored properly.
 
*If you do realize you're going down the same path as I, take stock of your options thoughtfully.  As far as I've been able to learn, converting a "dynamic disk" back to basic disk" is possible with retail disk management tools.  There are some free tools mentioned out there too, but I sincerely hope you won't have to bother by steering clear of dynamic disks altogether.

good luck!

---

### Post by Hedgehog1 on 2011-05-11
> **wickid_ninja said:**
>  After booting from the dvd, I went back to windows and I created a 60 gig partition of unallocated space from windows 7 disk management as i thought i needed to.

wickid_ninja,

You cannot create the Ubuntu partition from the Windows Disk Management.  You will need two or three partitions to run Ubuntu, and none of their formats are supported by the Windows Disk Management tool.

Here is an example of how to create the partitions manually using gparted on the LiveCD (liveDVD in your case).

Please boot from the LiveCD and select 'TRY', and menu to System >> Administration >> Gparted Partition Manager.

The following images show the deleting of the /dev/sda3 partiton to make and extended partition to allow the install of Ubuntu.  In your case, you will delete the partition you created in Windows Disk Management, which may or may not be /dev/sda3.

Here it goes:

[SIZE="3"]When all four primary partitions are taken (the HP install)[/SIZE]

[SIZE="4"][COLOR="DarkOrange"]First how it looks in Windows:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/9104/hp4partitions01.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]What it looks like in gparted off the LiveCD:[/COLOR][/SIZE]
[IMG]http://img859.imageshack.us/img859/8806/hp4partitions02.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right click on sda3 and select 'Delete': (YOURS MAY NOT BE SDA3!!)[/COLOR][/SIZE]
[IMG]http://img856.imageshack.us/img856/2164/hp4partitions03.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the 'check' mark button to really make the change:[/COLOR][/SIZE]
[IMG]http://img190.imageshack.us/img190/1732/hp4partitions04.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Right Click, on empty area, select new and create extended sda3 (Press that check mark button again...):[/COLOR][/SIZE]
[IMG]http://img69.imageshack.us/img69/5967/hp4partitions05.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create your sda5 Ubuntu partition, leave a little room for swap later (Format this ext4 - and press that check mark button again.):[/COLOR][/SIZE]
[IMG]http://img863.imageshack.us/img863/4839/hp4partitions06.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Create sda6 and make it swap space:[/COLOR][/SIZE]
[IMG]http://img855.imageshack.us/img855/3999/hp4partitions07.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]Press the check mark button again[/COLOR][/SIZE]

---

### Post by Hedgehog1 on 2011-05-11
[SIZE="4"][COLOR="DarkOrange"]You are ready to install Ubuntu:[/COLOR][/SIZE]
[IMG]http://img864.imageshack.us/img864/2449/hp4partitions08d.png[/IMG]

[SIZE="4"][COLOR="DarkOrange"]
Once your partitions are laid out, you will start the install and eventually get to the **Disk Space Allocation** screen.  

If you are installing Natty/11.04, select the '**Something Else**' option.

If you are installing 10.04 or 10.10, select the '**Specify Partitions Manually (Advanced)**' option.[/COLOR][/SIZE]

[SIZE="4"][COLOR="DarkOrange"]And you will get to here:[/COLOR][/SIZE]
[IMG]http://img849.imageshack.us/img849/9937/hp4partitions10.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]We will add some extra data to sda5 and sda6.  With sda5 highlighted, press the [CHANGE] button:[/COLOR][/SIZE]
[IMG]http://img861.imageshack.us/img861/5274/hp4partitions11.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]These settings prepare the partition to be exdt4, '/'.[/COLOR][/SIZE]
[SIZE="4"][COLOR="DarkOrange"]Repeat the steps for the swap area (This usually set itself up OK) :[/COLOR][/SIZE]
[IMG]http://img26.imageshack.us/img26/4934/hp4partitions12.png[/IMG]
[SIZE="4"][COLOR="DarkOrange"]You are ready to install.  Press [Install Now].[/COLOR][/SIZE]
[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG] 
[SIZE="4"][COLOR="DarkOrange"]This is what the drive looks like in the 'Disk Utility' in Ubuntu after the load is complete:[/COLOR][/SIZE]
[IMG]http://img852.imageshack.us/img852/3987/hp4partitions14.png[/IMG]  

***The Hedge***

:KS

---

