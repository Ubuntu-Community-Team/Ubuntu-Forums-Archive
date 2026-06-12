---
title: "A partitioning nightmare"
date: 2009-08-18
forum: New to Ubuntu
---

### Post by cosmocrazy on 2009-08-18
Here's the story: I have Windows 7, XP and Ubuntu 8.10 on one hard drive. I used XP for gaming, but it was taking a lot of time, so I decided to delete it. 

Did I use Gparted? Unfortunately, no. I wanted to test out some new software. (Paragon Partition Manager, free from Give Away of the Day) Unfortunately instead of deleting the XP partition, it converted all the partitons on my hard drive to logical partitions inside an extended partition, breaking the boot into any form of Windows. 

However, I could still boot into Ubuntu live and from there, install grub and boot into 8.10 on my HDD. Eventually I removed the extended partition the only way I knew how: by copying the logical partitions to another drive, deleting everything including the extended partition, then copying back the 7, XP, 8.10, and swap partitons as primaries. However, Windows ***still doesn't boot.***

I've troubleshooted this for 2 full days and I'm ready to give up. I have tried using the Windows 7 restore disk several ways, including "Startup Repair", bootrec /fixmbr, bootrec /fixboot, bootrec /rebuildbcd. All of those just produce a blinking cursor on boot.

Currently I have grub as my bootloader with all the working Ubuntu entries, plus these Windows entries that don't work. They hang on a blinking cursor too after the "Starting up..." line. I have tried root and rootnoverify.

```
title		Windows 7
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


Here are my partitions. The first is Windows 7, then XP, the Ubuntu.

```
ubuntu-desktop:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf6f4091d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       26757   214925571    7  HPFS/NTFS
/dev/sda2           31645       33587    15607147+   7  HPFS/NTFS
/dev/sda3           33588       36248    21374482+  83  Linux
/dev/sda4           36249       36532     2281230   82  Linux swap / Solaris

```



What do I do to get Windows to boot?

---

### Post by timcredible on 2009-08-18
it probably erased the boot sector for windows (gparted just moves it).  you'll probably need to reinstall windows.  it will want to take the first partition, and it won't like an extended partition, so....... backup your data first, because windows may erase your entire hard drive.  your other option is to create a SGD (Super Grub Disk) livecd and see if you can repair the install, but from the sounds of things SGD isn't going to work in this case.

---

### Post by presence1960 on 2009-08-18
Boot into Ubuntu and click on the link in my signature line. Download the boot info script 0.32 to desktop. Once on desktop open a terminal and run this command ```
sudo bash ~/Desktop/boot_info_script*.sh
```
This will create a RESULTS.txt file on desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. This info will give a clear picture of your set up and boot process.

---

### Post by stinger30au on 2009-08-18
_[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)_[]("https://launchpad.net/remote-help-assistant")

---

### Post by cosmocrazy on 2009-08-20
I can't believe this. I thought no one replied because I didn't get any email notifications, but now I realize that was because I didn't setup a subscription. *sets subscription* Does anyone know how to set up a default subscription for all threads/replies? 

I don't have any results of scripts to show you since I gave up, but I did have some Windows problems I can share:

I got tired of troubleshooting, so what I tried to do was reinstall windows on the first primary partition, then replace the "Windows", "PerfLogs", and "Users" etc. folders, in theory keeping my drivers, home folders, and programs, while replacing the boot files. [by not overwriting them on the new install] That didn't work. When I restarted to Windows, it immediately launched Startup Repair (I didn't have the disk inserted), which then deleted the entire first primary partition. At that point I just gave up and did a clean install, and reinstalled all my programs and copied the contents of my home folder back. (I was using the "Administrator" profile to install programs and move all my data back, with TeraCopy 2)

[More Windows troubles ahead]

However, even after I moved all the contents of my home folder back, things still weren't perfect. I logged into my profile and found that all my programs were installed, and the settings too, since I copied the AppData folder! Except whenever I tried to open anything on my desktop, or any links on the Start Menu, I would always get the message: 

"Windows cannot access the specified device, path, or file. You may not have the appropriate permissions to access the item."

It would always be in a window titled "Explorer.exe". Which made sense, because all my other programs could read files and open folders. Apparently this error message is also associated with "Internet Explorer 8 Enhanced Security", but that only blocks executables, whereas with me, I got that message with everything, and there was no "Unblock" button. 

So I used my head. "Ok," I thought, "It must be a permissions problem." So I looked in the Security tab and took ownership and added "Full Control" permissions for myself, and it STILL didn't help. I still couldn't open files on the desktop or links on the start menu, or even open any explorer windows at all. Win+E, Win+R, nothing worked. 

But what I did notice was that the problem was isolated to that account only. So what I did was create a new profile and moved the contents of my home directory to that profile. I could then open folders and operate normally, even after logout/login, so nothing was wrong with my home folder AppData folder etc. I then deleted the original, defected profile, then created a new profile with the same name, then once again moved all my home folder contents to the new profile. I then deleted the test profile. One day later I can now say that I am back up and running, with only a few programs left to reinstall.

So the problem could have been one of many things. It could have been that I was copying my files from another user account. It could have been that I initially used TeraCopy to copy all the data from my backup drive. It could have been that I just had a corrupted profile.

---

### Post by presence1960 on 2009-08-20
to subscribe, log in to the forum, under Quick Links choose Edit options. Scroll down a little and you will see it, Default Thread Subscription Mode. Choose your option and save by clicking Save Changes at the very bottom of the page..

---

