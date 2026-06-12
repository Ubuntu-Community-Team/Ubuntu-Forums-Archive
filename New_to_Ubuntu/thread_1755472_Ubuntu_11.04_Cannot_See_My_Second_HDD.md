---
title: "Ubuntu 11.04 Cannot See My Second HDD"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by OwainGlyndwr on 2011-05-11
Hi all,

installed Linux last night for the very first time after using DOS 6.22  then Windows, since 1994.

Install went ok and updating drivers wasn't to bad.  :)

But i just cannot work out how i find, see or use my second hard drive.

I did read some information before coming here on "opening a portal" and "mounting the partition", using Alt+F2. But that did not seem to do anything.  :confused:

So you can see i don't have a clue what i am doing and any help would be gratefully received.

cheers,
Mike.

---

### Post by Ghost_Mazal on 2011-05-11
If you open your home folder , you will see devices listed on the left. Doesn't it show there ?

Also , is this drive NTFS or EXT or FAT 32 ?

---

### Post by TeoBigusGeekus on 2011-05-11
If you're using 10.04 or 10.10, go to the Places menu and select your 2nd hd - it will be automatically mounted.
If you're using 11.04, I think you should click on the Desktop and then go to the top panel, where a Places menu will appear.

---

### Post by grahammechanical on 2011-05-11
Hi

I remember DOS 6.22 and an earlier version. I wonder, are you as old as I am? You do not say which Linux distribution you are using. It does not have to be Ubuntu to get help on this forum. But Ubuntu is the only distribution of Linux that I have any familiarity with. Are you using 10.10 or 11.04? There is a different look to the screen between 10.10 and 11.04. There are changes to the directions needed to change things. So, I will keep advice to general comments.

Forget about DOS and Windows drive letters. They are not used in Linux. I am going to assume that you are using 11.04 and that you are seeing the Unity user interface. Do you see a panel to the left side of the screen? Do you see and icon of a folder? Click on it. A box will appear showing folders. Move the mouse pointer to the top panel and you will see File Edit View Places Help.

Click on Places and then click on Computer in the drop down menu. In the window you should now see a icons representing your hard discs. Click on one and two things will happen. 1) an icon of a hard disc will appear on the desktop (this means that you have mounted that hard drive). 2) an icon of a hard disc will appear in the side panel (called Launcher).

Click on this second icon and a window will open that will give you access to the folders and files on that hard disc. In the side panel of that window you will see the words File System. These would be called Drive C: or Drive D: in Microsoft Windows.

Once you have mounted the second drive programs will browse to the folders of the drive so that you can open documents in that folder.

In Ubuntu the intention is for the user to work with documents without the need to know about Drives. Folders, Drives, Partitions are just different places to put Files, which are just different documents. It is a different way of thinking to the one that we got used to from using Microsoft Windows. 

Regards.

---

### Post by OwainGlyndwr on 2011-05-11
Hi guys, my topic title is Ubuntu 11.04.............hehehehehehehehe.

I thought i was the mental one.  :lolflag:

In the "Places" side bar i see two hdd, but they both reference what was my C:\ drive.

Which it looks like Ubuntu partitioned when it was installing.

One it has named "314gb File System" and shows the various files and folders i would associate with Winblows.

The other it has just named "File System", which shows an identical selection of folders.

I really struggling here, to understand the concept of "no drives"  :)

I am using the Unity desktop and i have found the "Places" option, but it does not give me the option to mount my second hdd. I have 2x WD 320gb hdd, one has the Linux install on it, the other i use for storage and it uses the NTFS file system, these were my C & D drives in Win 7.

I am 58 next month Graham.  :(

regards,
Mike.

---

### Post by Ghost_Mazal on 2011-05-11
The "314gb drive" is your 2nd HDD.

The "filesystem" is Ubuntu's drive

---

### Post by OwainGlyndwr on 2011-05-11
Thanks Ghost, i re-installed Win 7 as i had a theory, which turned out correct.

Somehow last night when installing Ubuntu it installed to my D:\ drive thus wiping out over 4 yrs of stored files and information.  :(

Everything lost, something that never happened to me once using Windows.

So now i am back with Ubuntu on my main drive and i have formatted and re-partitioned what was my D:\ drive, so that there is nothing on it.

Looks like a lot of downloading to be done.  :D

Is there anyway to rename the main drive to something other than "filesystem" ?

Thank you for the help.

regards,
Mike.

---

### Post by Ghost_Mazal on 2011-05-11
When installing Ubuntu on a pc with more than one drive you must be very sure to which drive you point it to install.

In linux you must forget about drive letters and know the device names , for example /dev/sda and /dev/sdb
and different partitions and on a drive would be /dev/sda1 and /dev/sda2 for example. Knowing these things before install on a multi drive pc is vital. Otherwise your install goes where you didn't want it.


You must know exactly beforehand which drive is which and then do manual partitioning during install and point it to the correct drive.

---

### Post by OwainGlyndwr on 2011-05-11
Yup i have learnt my lesson on that one, lost the lot.  :o 

Can i allocate which drive to download to, as per windows.

I have just created a folder on the sdb drive, partition ( whatever it is called now )  :D

For anything i download in the future.

Thanks again for the very helpful information.  ;-)

regards,
Mike.

---

### Post by OwainGlyndwr on 2011-05-18
I returned  to Win 7 64, this is too much like jumping through hoops just for the sake of it.

Thank you to those who helped me, while i was here.  :)

Mike.

---

