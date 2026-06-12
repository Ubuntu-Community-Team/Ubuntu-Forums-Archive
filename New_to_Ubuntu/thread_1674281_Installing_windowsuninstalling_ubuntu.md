---
title: "Installing windows/uninstalling ubuntu"
date: 2011-01-23
forum: New to Ubuntu
---

### Post by BrandenPosts on 2011-01-23
Heyy, so this is my second time installing linux ubuntu, but again i dont think im ready for it, this time though i completely uninstalled/formated my comp before, so i dont have windows. i have a windows cd, for windows 7, but it tells me i need a partition of like 600mb or more. how do i get past this and install windows 7/uninstall linux?

---

### Post by mikewhatever on 2011-01-23
If W7 wants, give it a partition, I rather doubt it has anything to do with Linux.
Searching online on how to install W7 might also help.

Edit: Welcome all to ubuntuforums.org, the number one resource for Windows7 help and support.:shock:

---

### Post by BrandenPosts on 2011-01-23
Yea i know,  but i have no idea how to install a partition on linux. and google didnt help me :/

---

### Post by Hippytaff on 2011-01-23
Do you want to dual boot or get rid of ubuntu completely?

If dual boot then your better off installing windows and reformatting the drive with it and then doing a ubutu partition...because Linux/ubuntu has the tools, windows tends not to facilitate dual booting!

---

### Post by Paqman on 2011-01-23
If you want to completely remove Linux and install Windows then just let the Windows installer format the whole drive. It'll create one big partition the size of the disk.

---

### Post by BrandenPosts on 2011-01-23
Yea i want to completely remove linux, then after when i get more ram/memory i will bring back linux. but for now im going to competely remove it. the problem is whenever i try installing windows it gives me an error. saying

Windows setup cannot find a location to store temporary installation files. to install windows, make sure that a partition on your boot disk has at least 685 megabytes of free space

error code: 0x80070490

---

### Post by mikewhatever on 2011-01-23
> **BrandenPosts said:**
> Yea i know,  but i have no idea how to install a partition on linux. and google didnt help me :/

You are installing Windows, so forget about Linux for now. If googling doesn't help you, check out some Windows help forums.

---

### Post by Hippytaff on 2011-01-23
you need to reformat your disc, but the windows install disc should offer to do that as part of the install process - guess you could try repartitioning the disc with gparted though I don't know that it offers to do it as ntfs?

strange

---

### Post by BrandenPosts on 2011-01-23
and how do you do that? :S

---

### Post by Hippytaff on 2011-01-23
You should be able to put the windows disc in...then reboot...then choose to do a fresh install of windows.

It should just reformat your disc and windows should take up the whole harddrive...if it doesn't work, then maybe the windows disc is corrupt and it might be worth checking with people who use windows ;-)

---

### Post by BrandenPosts on 2011-01-23
i just rebooted nothing happened, i went into setup with f11 and told it to boot from the cd but it still just brought me to linux again.

---

### Post by Hippytaff on 2011-01-23
[try this]("http://www.ehow.com/how_4929061_format-hard-drive-ubuntu.html")

---

### Post by BrandenPosts on 2011-01-23
How to i get gparted?

---

### Post by Hippytaff on 2011-01-23
There is a utulity on the Ubuntu liveCD similar to Gparted or you can download it [here]("http://gparted.sourceforge.net/livecd.php")

---

### Post by BrandenPosts on 2011-01-23
kk its downloading. but wouldnt it be easier to just make a partition for the cd to run ?

---

### Post by Hippytaff on 2011-01-23
Like I said if you want to get rid of Ubuntu and reinstall windows the windows disc should do that for you, but failing that the best way is to reformat you drive and then try your windows disc again...if you want to dual boot then thats a different matter all together..you have to beat your computer to death with your own shoes ;-)

If you want to dual boot then let me know becuase we'll havve had a misunderstanding :-)

---

### Post by BrandenPosts on 2011-01-23
hmm..what if i dool boot, then delete ubuntu? would that work?

---

### Post by uRock on 2011-01-23
That would just cause you more problems. 

If you still have an Ubuntu install disk, then you can use it to format the HDD to NTFS, then install Windows.

---

### Post by BrandenPosts on 2011-01-23
i didnt use a disk, i used daemon tools on my windows, so now that's gone too..

---

### Post by uRock on 2011-01-23
Here are a bunch of links that may explain how to reformat the HDD using the Windows installer. [http://www.google.com/search?client=ubuntu&channel=fs&q=windows+7+installer+partitioning&ie=utf-8&oe=utf-8](http://www.google.com/search?client=ubuntu&channel=fs&q=windows+7+installer+partitioning&ie=utf-8&oe=utf-8)

I have used the Windows & disk to wipe out EXT partitions, but I do not mind telling you how to delete the partition using the Ubuntu LiveCD, if you'd like.
> **BrandenPosts said:**
> i didnt use a disk, i used daemon tools on my windows, so now that's gone too..
If you can download and burn the ISO, then I'd gladly help.

---

### Post by BrandenPosts on 2011-01-23
yea sure, ima download it now.

and btw what's ntfw?

---

### Post by Hippytaff on 2011-01-23
:-D

Urock...you do actually rock :-)

---

### Post by uRock on 2011-01-23
> **BrandenPosts said:**
> yea sure, ima download it now.

and btw what's ntfw?
NTFS is the file system used by Windows.

Once you burn the ISO to CD/DVD, boot it,

When you see the first purple screen with the little keyboard icon, hit the **space bar**,

Select your language, then at the next screen, choose to **Try Ubuntu without installing**,

Then the system will take a minute or two to boot the image,

Once the desktop is loaded, open the menus and go to **System> Administration> GParted**,

once Gparted opens, it should list your HDD, **right-click** on the **EXT partition** then,

select to **delete** the partition then

once it reloads and says there is unallocated space you can **right-click** again and choose **New**,

Now a new window will open, click the dropdown for **filesystem** and select **NTFS**, which is at the bottom,

_and then_,

click the **Add** button,

Once the window closes you can now click the [COLOR=DarkGreen]**green check mark**[/COLOR] button which will delete the EXT partition and create and NTFS partition. 

You can not shutdown and boot the Windows 7 installer. This link will walk you through the steps on installing Windows 7. [http://www.techtalkz.com/windows-7/514412-windows-7-installation-guide-tutorial.html](http://www.techtalkz.com/windows-7/514412-windows-7-installation-guide-tutorial.html)

Cheers,
uRock

PS, You can access this page via Firefox once the LiveCD boots up to match the screenshots with the instructions. I took the screenshots while running the 10.10 LiveCD, so 10.04 may look a little different.

---

### Post by uRock on 2011-01-23
One thing I missed,

Delete the Swap partition as well, you may have to right-click it in the Gparted window and select to **Unmount** it.

---

### Post by nm_geo on 2011-01-23
+1 on uRock info.

Just in case the windows install goes South keep the Ubuntu CD or USB that you downloded.

---

### Post by Markn951 on 2011-01-23
I think a lesson can be learned here: Make sure you know what you're doing BEFORE you do it! :)

---

### Post by presence1960 on 2011-01-23
> **Markn951 said:**
> I think a lesson can be learned here: Make sure you know what you're doing BEFORE you do it! :)

Most people only learn that lesson **_AFTER_** they make the mistake. Hindsight is a dubious luxury. It helps not.

---

