---
title: "Need help on New partition"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by mobiusrex on 2010-10-16
Hi there , I am a new Linux user and have now installed Maverick Meerkat  2 days back on my new PC(brand new , no other O.S) . I love the system  and am still getting used to downloading package instead of exes . I  have hit up on one newbie problem here and I have spent some time  looking for the solution on the web but I dont seem to have got the  answers for it. 

I have a 1 TB HDD which I have partitioned into 5 partitions

Primary partition sda1 mounted on root "\" which is about 200 GBs
Swap partition sda5 which is about 10 GB
logical partition sda6 mounted at /home and about 200 GB
logical partition sda7 about 100 GB mounted at /usr
logical partition sda8 at /usr/local with rest of the memory

Having been a windows user all along i am having difficulty not seeing  these partitions as separate drives. I have check via the "Storage  Device Manager" that the partitions are mounted automatically. I have  gone into the file system via the file system icon and I can see that  there is only 173 GB available.  I checked the home and usr folders and i  cant figure where the rest of the space has gone.

So what I would like from the forum is

1. Where do i now find the other partitions ? (Please excuse if this is  very basic as every partition related query I have fired has taken me  only to how to sections )
2. I did see when starting the OS from a flash drive directly that I was  getting different icons for each partitions viz. 200 GB file system ,  500 GB file system etc, how do I make it appear in normal mode

Kindly provie the answer or provide a link to relevant documenation

Cheers
Mojo

---

### Post by Hippytaff on 2010-10-16
1- Typing df in the terminal will give you a list of partitions

CTRL+ALT+T to open terminal

not sure what question 2 means :-)

---

### Post by Elfy on 2010-10-16
I assume you had a reason for partitioning your drive like that. 

Not too sure how they will look in nautilus as /usr and /usr/local are generally in / .

To be honest I would say that having 

/ @200Gb
/usr @100Gb
/usr/local @ ~490Gb

is a waste of drive space - of course I don't know what you intend to do with the system so that is a general comment.

I too am not sure what you mean by the icons.

---

### Post by srs5694 on 2010-10-16
There's seldom much need for you to have direct access as a user to anything in the /usr directory tree. That is, you don't usually need to copy files to or from those directories, edit those files, etc. You do obviously need to be able to read these files, since they're program executables, libraries, fonts, and so on; but you launch them from icons or menu entries on your desktop or by typing their names in a shell, not by browsing to their locations in a file browser. The way Linux lays out its directories, the vast majority of your file accesses (in terms of things you'll want to use a file manager to get to) should be in /home or in /media if you make much use of removable disks.

Generally speaking, 20 GB is plenty of space for a Linux installation, including everything in root (/), /usr, and /usr/local, but often *not* for /home. Thus, I agree with forestpiskie that you're probably wasting vast amounts of your disk space with your current partitioning scheme. My general advice to new Linux users is to partition as follows:


[LIST]
[*]**root (/):** One partition of 5-20 GB, depending on how much software you plan to install and how much space you have available
[*]**swap:** One partition of 1-2x your system's RAM
[*]**/home:** One partition for the rest of your available disk space
[/LIST]


There are reasons to split off other directories from root (/), but these reasons are strongest for big professional installations (servers, systems with dozens of users, etc.). The difficulty of getting the sizes right makes it inadvisable for new users.

Overall, I'd recommend you re-install before you put too many files in your home directory that you'll have to back up. Unless you're using software that's fallen through a time warp from 2020, chances are you won't use much of the space you've allocated to root (/), /usr, and /usr/local; but you might want that space in /home if you do video editing, have large music collections, have lots of digital photos, etc.

Regarding your question #2, if I understand correctly you're saying that  when you boot from your hard disk, you don't see desktop icons for /usr  and /usr/local, but that when you boot from a USB flash drive, you do.  This is because /usr and /usr/local are defined in /etc/fstab for your  hard disk boot, but not for your USB flash drive boot. If you really  want to see such icons, you could probably create symbolic links in the  ~/Desktop directory. There's probably a way to do this within the GUI,  but I don't use GNOME much, so I'm not sure what it is. From a shell,  you could do it by typing "ln -s /usr ~/Desktop/usr", and similarly for  /usr/local.

---

### Post by chideock on 2010-10-16
Open a terminal window and type in "gedit /etc/fstab" after the prompt. Does that show you what you want? 
I take it your OS is Ubuntu with the Gnome GUI - if that is the case try System-Administration-System Monitor and look at all the tabs - Does that get you the info you want?

Tom

---

### Post by Cycledoc on 2010-10-16
For new users please clarify the differences in terminology between:  

Forrestpiskie's

       / @200Gb
       /usr @100Gb
       /usr/local @ ~490Gb

And SRS 5694's


[LIST]
[*]**root (/):** One partition of 5-20 GB, depending on how much software you plan to install and how much space you have available
[*]**swap:** One partition of 1-2x your system's RAM
[*]**/home:** One partition for the rest of your available disk space
[/LIST]
Are they the same or different.  

Many thanks.  

Ubuntu is some ways is like learning a new language.

---

### Post by chideock on 2010-10-16
The root partition is shown as "/" in the linux system
swap is a partition
/home is the home partition
/usr is another partition
/usr/local I guess is another partition but in the stuff I have read never seen mention of it


I was going to ask about a general way to partition but I think srs5694 answered that question. When I loaded I let Ubuntu assign the entire disk - 500gig. My system shows "/dev/sda1"  "/"  "ext4"  439.4GiB total;  436.8GiB free;  414.4GiB available; 3.1GiB used. I load a few apps after install.

Tom

---

### Post by srs5694 on 2010-10-16
In Linux, most partitions are mounted at mount points, which means that they appear as directories in the Linux directory tree. In principle, you can split off most Linux directories as separate partitions -- /home, /usr, /usr/local, /tmp, /var, /boot, /opt, and so on. (There are a few exceptions, like /etc, /bin, /sbin, and /lib.) The base, or "root", of the directory tree, is written as "/". I generally refer to it as "root (/)" to avoid confusion because of a single-character value that could be interpreted as punctuation or confusion with the /root directory, which is *not* the same as the root (/) partition or directory.

Swap space is unusual in that it doesn't get mounted, so it's not "/swap"; it's just "swap". Non-Linux partitions also might or might not be mounted, depending on your needs and preferences. (The GNOME file manager has a tendency to auto-mount everything in sight, though, so you may have non-Linux filesystems mounted in subdirectories of /media whether or not you want them there.)

For more information on how Linux organizes its directories, and therefore what different partitions are for if you split them off that way, consult the [Filesystem Hierarchy Standard](http://www.pathname.com/fhs/) documentation.

---

### Post by Elfy on 2010-10-16
> **Cycledoc said:**
> For new users please clarify the differences in terminology between:  

Forrestpiskie's

       / @200Gb
       /usr @100Gb
       /usr/local @ ~490Gb

And SRS 5694's


[LIST]
[*]**root (/):** One partition of 5-20 GB, depending on how much software you plan to install and how much space you have available
[*]**swap:** One partition of 1-2x your system's RAM
[*]**/home:** One partition for the rest of your available disk space
[/LIST]
Are they the same or different.  

Many thanks.  

Ubuntu is some ways is like learning a new language.

Mine was not a suggestion - it was a question as to why it was like it.

Personally I used to go with the /, swap and /home route. I no longer use a seperate /home - data all goes to other partitions and when I need to do a clean install I do not format and existing /home is left alone.

---

### Post by mobiusrex on 2010-10-16
First everyone thanks everyone for providing your valuable expertise.I had checked sometime back and didnt see any reply so thought Ubuntu forums were just like other forums where a query could be snowed under. Happy to be proven wrong.

@Hippytaff - Thnx. I could view the same using sudo fdisk -l command.

@forestpiskie -Actually I had no specific reason to do that except that I used to do a similar partitioning approach whilst I used to install windows on my older machine.

@srs5694 - As mentioned above, I didnt have an inkling of it would turn out when I did the partitioning. Now I understand better. I think I will probably do the reinstall now with below partition

    * root (/):  ~100
    * swap: ~ 4 GB
    * /home: The rest.

I hope this will provide me  the right file system

Thanks every one

P.S - Actually what'd got me worried was that I could just see around 180 Gigs of free space in the file system and that made me wonder where the others had gone making me do this post in the first place

---

### Post by mobiusrex on 2010-10-16
I've now done the install and all the free space is now available at home and the space allocated for the root is at the file system. Perfect. Thanks

---

### Post by heyandy889 on 2010-10-19
> **srs5694 said:**
> There's seldom much need for you to have direct access as a user to anything in the /usr directory tree. That is, you don't usually need to copy files to or from those directories, edit those files, etc. You do obviously need to be able to read these files, since they're program executables, libraries, fonts, and so on; but you launch them from icons or menu entries on your desktop or by typing their names in a shell, not by browsing to their locations in a file browser. The way Linux lays out its directories, the vast majority of your file accesses (in terms of things you'll want to use a file manager to get to) should be in /home or in /media if you make much use of removable disks.

Generally speaking, 20 GB is plenty of space for a Linux installation, including everything in root (/), /usr, and /usr/local, but often *not* for /home. Thus, I agree with forestpiskie that you're probably wasting vast amounts of your disk space with your current partitioning scheme. My general advice to new Linux users is to partition as follows:


[LIST]
[*]**root (/):** One partition of 5-20 GB, depending on how much software you plan to install and how much space you have available
[*]**swap:** One partition of 1-2x your system's RAM
[*]**/home:** One partition for the rest of your available disk space
[/LIST]


There are reasons to split off other directories from root (/), but these reasons are strongest for big professional installations (servers, systems with dozens of users, etc.). The difficulty of getting the sizes right makes it inadvisable for new users.

Overall, I'd recommend you re-install before you put too many files in your home directory that you'll have to back up. Unless you're using software that's fallen through a time warp from 2020, chances are you won't use much of the space you've allocated to root (/), /usr, and /usr/local; but you might want that space in /home if you do video editing, have large music collections, have lots of digital photos, etc.

Regarding your question #2, if I understand correctly you're saying that  when you boot from your hard disk, you don't see desktop icons for /usr  and /usr/local, but that when you boot from a USB flash drive, you do.  This is because /usr and /usr/local are defined in /etc/fstab for your  hard disk boot, but not for your USB flash drive boot. If you really  want to see such icons, you could probably create symbolic links in the  ~/Desktop directory. There's probably a way to do this within the GUI,  but I don't use GNOME much, so I'm not sure what it is. From a shell,  you could do it by typing "ln -s /usr ~/Desktop/usr", and similarly for  /usr/local.
This post was particularly helpful to me, thank you very much. :D

I didn't realize that I wanted / in a partition all by itself. I was planning to allocate 4 GB to the swap partition, and then the other 100GB to the root partition. But, now I will take the advice of srs5694.


EDIT: Also, thought of a question. Should the /home partition be a logical partition, or a primary partition? I am using the partition editor on the Ubuntu 10.04 Live install disk. Thank you!

---

### Post by srs5694 on 2010-10-19
> **heyandy889 said:**
> I didn't realize that I wanted / in a partition all by itself. I was planning to allocate 4 GB to the swap partition, and then the other 100GB to the root partition. But, now I will take the advice of srs5694.

The root (/) partition is the only one that's really required by Linux; *every* directory is defined relative to the root (/) directory, and it needs storage space -- normally a partition, although it can be a logical volume in an LVM scheme or other unusual types of storage.

> EDIT: Also, thought of a question. Should the /home partition be a logical partition, or a primary partition? I am using the partition editor on the Ubuntu 10.04 Live install disk. Thank you!
 
Linux doesn't care if /home (or any other partition) is primary or logical. My own recommendation is to make as many partitions as possible logical (with a few exceptions); that way, if you need another primary partition or two in the future (say, to install Windows or FreeBSD or some other OS that requires a primary), you'll have the entries available, even if you've got to move and/or resize partitions to free up the disk space. There are some exceptions to this rule, though. Obviously, if a non-Linux OS needs a primary partition, it should have one. Also, putting the Linux root (/) partition or the /boot partition, if it's separate, on a primary gives you more flexibility for boot loader configuration, since you can then install GRUB in the boot sector of the partition and use a standard DOS/Windows MBR boot loader to initiate the boot process. (These simple boot loaders can typically only boot to a primary partition.) This approach has some advantages, particularly in a dual-boot configuration; if you install Windows and this causes the system to boot straight to Windows, you can restore GRUB simply by changing the boot/active flag in the partition table, which you can do from Windows without using a Linux emergency disc to re-install GRUB.

---

