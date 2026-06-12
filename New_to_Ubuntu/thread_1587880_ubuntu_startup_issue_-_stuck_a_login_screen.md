---
title: "ubuntu startup issue - stuck a login screen"
date: 2010-10-04
forum: New to Ubuntu
---

### Post by doctor_adnan2003 on 2010-10-04
Hi
I am totally new to ubuntu, i have installed it previously but haven't used it much. 
A few days back i installed ubuntu on my laptop, using the CD. It installed fine and was working fine but by win 7 stopped working (the bluescreen issue).
So i formatted my hard disk
installed win 7 (working fine)
installed ubuntu using the windows installer available at [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

the installation went well, but when i start ubuntu, my laptop gets stuck on the login screen (i gave a username and password during the installation) but the system is completely stuck, the mouse and keyboard are totally jammed and the only way out is to keep the power button pressed few seconds to turn the laptop off.

i am totally new to ubuntu and i really want to learn it. Is there anyway to get ubuntu working without another install?
Thanks
Adnan

---

### Post by viralmeme on 2010-10-04
> **doctor_adnan2003 said:**
> A few days back i installed ubuntu on my laptop, using the CD. It installed fine and was working fine but by win 7 stopped working (the bluescreen issue).
You know something, that happens a lot around here, installing Linux breaks the Windows installation. What exactly was the `bluescreen issue' you encountered?

---

### Post by robsoles on 2010-10-04
> **viralmeme said:**
> You know something, that happens a lot around here, installing Linux breaks the Windows installation. What exactly was the `bluescreen issue' you encountered?

Installing Linux on a separate partition, where windows is on another partition, is not guaranteed to break your windows installation.

--------------------------------------------------------------------------------------------------------

Can you try booting into Ubuntu again, take note of the time, and then boot from the LiveCD, choose 'try Ubuntu' and try to find us some /var/log/messages, /var/log/boot.log and /var/log/dmesg log entries from at and after the time that you tried to boot.

When booted from the LiveCD you need to choose your Ubuntu install file-system from 'places' and then navigate within that to the /var/log directory.

---

### Post by doctor_adnan2003 on 2010-10-04
the 'blue screen' issue was bcoz i did something wrong in the partitioning and the bootloader of win 7 got corrupt.

now both the operating systems are installed fine, its just that ubuntu on start-up gets stuck.

i will get the /var/log/messages, /var/log/boot.log and /var/log/dmesg log in a few hours and upload it
thanks

---

### Post by doctor_adnan2003 on 2010-10-04
i dont have to cd right now, but i can login into the recovery mode
how can i navigate from there?

---

### Post by doctor_adnan2003 on 2010-10-04
no one?

---

### Post by robsoles on 2010-10-04
Good morning, it's 7.33am in AU and that's where I am, I must leave for work in 6 minutes.

Funnily enough I haven't spent much time in recovery mode so I don't know what it offers you.

While booted from the problem OS itself;
In GUI: 'Places'->'Computer'->'File System'->'/var/log'

in Terminal: ```
cd /var/log
```


For use of a browser in which to paste a copy of relevant lines from the logs I think you'll end up booting from a LiveCD.

---

### Post by amjjawad on 2010-10-04
> **doctor_adnan2003 said:**
> Hi
I am totally new to ubuntu, i have installed it previously but haven't used it much. 
A few days back i installed ubuntu on my laptop, using the CD. It installed fine and was working fine but by win 7 stopped working (the bluescreen issue).
So i formatted my hard disk
installed win 7 (working fine)
installed ubuntu using the windows installer available at [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

the installation went well, but when i start ubuntu, my laptop gets stuck on the login screen (i gave a username and password during the installation) but the system is completely stuck, the mouse and keyboard are totally jammed and the only way out is to keep the power button pressed few seconds to turn the laptop off.

i am totally new to ubuntu and i really want to learn it. Is there anyway to get ubuntu working without another install?
Thanks
Adnan

Hello Adnan,

Check my signature, there's a helpful guide that might help you.

I second what robsoles said. I always install Ubuntu either on a separate partition or on a separate Hard Disk Drive (internal/external). That would keep you in the safe side especially when you're dual booting with Windows.

Another advice. Always make sure to install Ubuntu's Boot loader in a separate partition rather than the partition where Windows is Installed. By time, you'll understand how important is that.


P.S.
Does your Windows 7 work without any problem?

---

### Post by doctor_adnan2003 on 2010-10-05
yes win 7 is working without any problem and definitely i installed ubuntu in a completely separate partition.

i tried to install it with wubi.exe 2 more times but i get the same problem.

is there any guide on how can i install ubuntu along with my win 7, without anything happening to the windows bcoz at this point im really not comfortable with ubuntu so i dont want to end up not being able to use my laptop for another few days.

---

### Post by amjjawad on 2010-10-05
> **doctor_adnan2003 said:**
> yes win 7 is working without any problem and definitely i installed ubuntu in a completely separate partition.

i tried to install it with wubi.exe 2 more times but i get the same problem.

is there any guide on how can i install ubuntu along with my win 7, without anything happening to the windows bcoz at this point im really not comfortable with ubuntu so i dont want to end up not being able to use my laptop for another few days.

1) Insert the LiveCD (the CD that contains Ubuntu's installation) ***OR*** the LiveUSB (the USB Drive that contains Ubuntu's installation).
2) Reboot your PC.
3) Double check your BIOS settings to make sure that your first booting device is either your CD-ROM or USB Drive.
4) When your PC will boot from your CD (or USB), select "TRY" Ubuntu or "Run Ubuntu from ..." and make sure NOT to select "Install Ubuntu".

5) Now, you're using the LiveCD/LiveUSB. The main point of this is to TRY Ubuntu before INSTALLING it :) Why? sometimes there are incompatibility issues so it's better to try Ubuntu on your machine (PC/Laptop) to make sure everything will go soothly.

6) I'd suggest to take a look on GParted.
System > Administration > GParted.
You can do whatever you like to your HDD(s) like formatting, creating, extra.

7) If everything is ok so far, try to install Ubuntu now. There's an icon on the desktop so that you can click it and the Installation process will start.

8) As I said, on my signature, there's a nice guide on how to partitioning your HDD and how to Install Ubuntu (check the photos Album and the Discussion Board).
I assume you have only one HDD but more than a partition.

A- In case you have two HDDs even if one of them is external, I suggest to install Ubuntu on the 2nd HDD. In that case, you just need to use "Erase and use the entire disk" and select your 2nd HDD from the drop down list.

B- In case you have only one HDD, then you have two choices:
Either 
- to Install using "Install them side by side, choosing between them each start up" 
OR
- to install using "Specify partitions manually"

If you'll choose "Specify partitions manually - Advanced", then you need to have the following partitions

1- Root Partition (/) - ext4
2- Swap - Usually the size of this partition should be double the size of your RAM (if your RAM is 2GB then your SWAP should be 4GB)
3- Home (/home) - ext4

9) Make sure to NOT install the boot loader on the same partition where Windows is installed.

10) I think you're good to go and hope I didn't forget anything.

Here is all what you need (hopefully).

Good luck!

---

### Post by doctor_adnan2003 on 2010-10-05
> **amjjawad said:**
> 

A- In case you have two HDDs even if one of them is external, I suggest to install Ubuntu on the 2nd HDD. In that case, you just need to use "Erase and use the entire disk" and select your 2nd HDD from the drop down list.

B- In case you have only one HDD, then you have two choices:
Either 
- to Install using "Install them side by side, choosing between them each start up" 
OR
- to install using "Specify partitions manually"

If you'll choose "Specify partitions manually - Advanced", then you need to have the following partitions

1- Root Partition (/) - ext4
2- Swap - Usually the size of this partition should be double the size of your RAM (if your RAM is 2GB then your SWAP should be 4GB)
3- Home (/home) - ext4

9) Make sure to NOT install the boot loader on the same partition where Windows is installed.

Good luck!

thanks a lot i'll try that today and let you know.
just a note that i have used the 'try ubuntu' option and it works perfectly fine.

i have a question (i have only on hdd)

where do i see the "Install them side by side, choosing between them each start up" option.
when i run the setup i get only 2 options
1_Erase and use the entire disk
2_Specify partitions manually
(i have downloaded the iso from ubuntu's website)

and where u say "Make sure to NOT install the boot loader on the same partition where Windows is installed." u mean not to install both in the same partition?

Thanks

---

### Post by amjjawad on 2010-10-05
> **doctor_adnan2003 said:**
> thanks a lot i'll try that today and let you know.
just a note that i have used the 'try ubuntu' option and it works perfectly fine.

i have a question (i have only on hdd)

where do i see the "Install them side by side, choosing between them each start up" option.
when i run the setup i get only 2 options
1_Erase and use the entire disk
2_Specify partitions manually
(i have downloaded the iso from ubuntu's website)

and where u say "Make sure to NOT install the boot loader on the same partition where Windows is installed." u mean not to install both in the same partition?

Thanks


You most welcome :)

To answer you questions:

1) [https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step4b.png](https://help.ubuntu.com/community/GraphicalInstall?action=AttachFile&do=get&target=install-step4b.png)

2) Yes, Ubuntu's boot loader is better to be installed on a separate partition which is NOT the same partition of Windows.

Let me know if you need more info :)

---

### Post by amjjawad on 2010-10-05
I forgot to mention that even if you have one HDD, you can also try the manual partition (advanced) as explained in my previous post.
It's all up to you. Either you let Ubuntu do the job for you or you could do it. Your call :)

---

### Post by doctor_adnan2003 on 2010-10-07
my friend  have solved the problem

first i was installing ubuntu when all my drives were extended drives in windows. i repeatedly got the same issue after every reinstall.

Then i turned all of the drives to primary from the windows disk manager and reinstalled and its worked fine, but when i restarted i got the same issue again
 :( :( :(
i think in giving up on ubuntu

---

### Post by amjjawad on 2010-10-07
> **doctor_adnan2003 said:**
> my friend  have solved the problem
first i was installing ubuntu when all my drives were extended drives in windows. i repeatedly got the same issue after every reinstall.

Then i turned all of the drives to primary from the windows disk manager and reinstalled and its worked fine, but when i restarted i got the same issue again
 :( :( :(
i think in giving up on ubuntu

I'm afraid I did not understand anything :(
Could you please explain more in details?

What do you mean by:
> 
first i was installing ubuntu when all my drives were extended drives in windows.

Do you mean all the partitions including Windows partition? or all the partitions EXCEPT Windows partition? Because Windows can not be installed on an extended partition at all, it must be primary partition.

Then, what do you mean by:
> 
Then i turned all of the drives to primary from the windows disk manager 

Why you're doing that? this is has nothing to do with Ubuntu's installation :)
You can install Ubuntu on a primary partition and/or a logical partition. Windows MUST be installed on a primary partition.

I hope you could provide me with more details so I could help you.

Giving up is not an option. Don't give up, that's nothing :)
We could walk you through until you fix your problem so don't lose hope, TEKA? ;)

---

### Post by amjjawad on 2010-10-07
Adnan,

Have a look on this screen shot:
[http://3.bp.blogspot.com/_T1ntsqbeRcI/TKyxgLi71mI/AAAAAAAAAAM/4B5uLnUh5A8/s1600/Disk+Manager.PNG](http://3.bp.blogspot.com/_T1ntsqbeRcI/TKyxgLi71mI/AAAAAAAAAAM/4B5uLnUh5A8/s1600/Disk+Manager.PNG)

Forget the names and numbers, just have a look on the partition map on that screen shot.
Where it says "Disk1", Windows is installed on Drive C which is a primary partition. The next 3 partitions (2 primary 1 logical in the extended partition) is for another OS.
The second disk (Disk2) has 2 primary and 2 logical partitions.

You need to know a little bit about partitioning so there you go:
[http://en.wikipedia.org/wiki/Disk_partitioning](http://en.wikipedia.org/wiki/Disk_partitioning)

Bottom line:
1- You can't have more than 4 primary partitions.
2- Windows must be installed on a primary partition
3- Ubuntu can be installed on primary or logical, doesn't matter.
4- When you create an extended partition, you can create many "logical" partition inside that extend partition. Check the screen shot again, you'll see the green area which is the extended and inside, there are some logical partitions.


I'm not sure what's the capacity of your HDD but that doesn't matter.

-----------------------------------------------------------------
Here's my suggestion for a partition scheme.

Partition1 (sda1)
File System: NTFS
Primary Partition
To be used by Windows


Partition 2 (sda2)
File System: ext4
Primary Partition
To be used by Ubuntu (mount point is /)

** Extended Partition **
Partition 3 (sda6)
File System: SWAP
Logical Partition
To be used as SWAP partition for Ubuntu

Partition 4 (sda7)
File System: ext4
Logical Partition
To be used by Ubuntu as Data Partition (mount point is /data)

Partition 5 (sda8 )
File System: NTFS
Logical Partition
To be used as Data partition for Windows

---------------------------------------------------------------
I chose Ubuntu's Partitioning numbers/scheme so that you could be more familiar with it. 

With Ubuntu, you need minimum 2 partitions (root and swap).
With Windows, it's up to you and one primary partition is enough.

I suggest to use GParted from the LiveCD (hope you have it now) because whatever changes you make on your HDD, it won't be applied until you click "Apply". Unlike Windows Disk Manager, any changes will take place immediately. 

Now, Try to format the whole HDD, start from scratch.
Create the partitions before you install anything using Ubuntu's LiveCD.
Once you're done, try to install Windows.
When it's done, DO NOT install Ubuntu, just reboot your PC and boot from the LiveCD of Ubuntu. See if you get the same issue of the login screen. If not, try to install Ubuntu as I previously explained.
You already have the partitions so all what you need to do is choose the last option: **Specify Partitions Manually (advanced)**. All what you have to do is to choose the mount point.

When the installation is done, reboot and see what will happen.

If you'll get exactly the same issue, then it might be something else is wrong. Before we say there's something wrong, I suggest to reboot your machine 2-3 times after the installations. First time I installed Ubuntu, I had to reboot 3-4 times until it worked perfectly after that.

Try and let me know :)

---

### Post by doctor_adnan2003 on 2010-10-08
> **amjjawad said:**
> I'm afraid I did not understand anything :(
Could you please explain more in details?

What do you mean by:

Do you mean all the partitions including Windows partition? or all the partitions EXCEPT Windows partition? Because Windows can not be installed on an extended partition at all, it must be primary partition.

Then, what do you mean by:

Why you're doing that? this is has nothing to do with Ubuntu's installation :)
You can install Ubuntu on a primary partition and/or a logical partition. Windows MUST be installed on a primary partition.

I hope you could provide me with more details so I could help you.

Giving up is not an option. Don't give up, that's nothing :)
We could walk you through until you fix your problem so don't lose hope, TEKA? ;)


it means

My first try:
only windows partition was primary, the rest were extended. Problem: Ubuntu did not startup at all.

My second try:
my friend did this.
all drives primary. ubnutu installed worked correctly for the first time, but after 1 reboot it jammed at the login screen again. the drum sound comes in 3 seperate pulses and it jams. (i had ubuntu working on my laptop just fine previously)


today i ll try this method and let you know.
Can i create an NTFS partition from ubuntu CD?

---

### Post by amjjawad on 2010-10-08
> **doctor_adnan2003 said:**
> Can i create an NTFS partition from ubuntu CD?

With GParted, you can create whatever file system you want. FAT, FAT32, NTFS, ext2, ext3, ext4, etc.

You need NTFS for Windows and ext4 for Ubuntu. So yes, you can :)

---

