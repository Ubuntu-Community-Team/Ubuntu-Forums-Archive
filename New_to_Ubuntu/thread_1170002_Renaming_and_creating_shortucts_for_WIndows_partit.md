---
title: "Renaming and creating shortucts for WIndows partitions"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by kickwin on 2009-05-25
I have three Windows partitions (C, D, E) and Ubuntu named them as /media/disk, /media/disk-1 and /media/disk-2 respectively. I created a link for my Windows desktop and placed it on my Ubuntu desktop. It all worked fine until I restarted the system. When I restarted my computer, what  happened was the partitions had interchanged their names. For instance C became disk-2 and D became disk. So the link I created did not work. 

What I would ideally like to have is have fixed names for my Windows partitions which would enable me to create links from Ubuntu. 

I have another question ATSL. Currently, most of my files are in my Windwows drive and I am accessing these files from Ubuntu as it mounts these drives by default. Is it better to have my files on /home/username rather? Any negatives on having my files on Windows partitions?

---

### Post by Ceiber Boy on 2009-05-25
All disk partitions weather mounted or not are listed on the 'places' menu at the top of the screen, so i can't see a need for creating links on your desktop, also when the partition is mounted ubuntu automatically places a shortcut on the desktop for you anyway!

if your using a windows partition to store all your data, then i'm assuming the file system is an NTFS, which suffers from 'windows' problems. so you are still tied to using windows for the utility tools. also a good chunk of research will allow you to discover the pro's and con's of NTFS and ext3, but you must find these things out for yourself and make your own decisions!

Good Luck

---

### Post by kickwin on 2009-05-25
> **Ceiber Boy said:**
> All disk partitions weather mounted or not are listed on the 'places' menu at the top of the screen, so i can't see a need for creating links on your desktop, also when the partition is mounted ubuntu automatically places a shortcut on the desktop for you anyway!
  

The shortcuts I want to create are not just for the the Windows drives C or D. I want to create shortcuts for other folders inside these partitions such as my Windows Desktop which is on C:/documents and settings/user/Desktop. It would easier to navigate instead of going down folder by folder. Any help would be appreciated.

---

### Post by Ceiber Boy on 2009-05-25
ok, sorry i did not fully understand your question because i miss read it! i have never tried to make a link on my ubuntu desktop to a specific place on my windows partition, so i am unable to offer any helpful advice other than playing around and seeing if it is possiable, but you can do that your self!

to overcome a simular problem to this i have three partitions on my hardisk, first is windows, second is just for data (has to be NTFS so that it can be read by windows), third is my ubuntu. i then access my data partition from both linux and windows,

hope this idea helps

---

### Post by Viva on 2009-05-25
Install "link to" nautilus script and create a short cut using it.

---

### Post by asmoore82 on 2009-05-25
It sounds to me like the OP wants to edit his fstab and set static mount points for windoze ...

"/etc/fstab" is plain text file that governs which partitions get mounted at boot and where.

Google it or search the forums and you'll find a nice "howto" guide that include making
sure your NTFS filesystems get the proper UNIX permissions faked at mount time.

the starting point is ```
gksudo gedit /etc/fstab
``` but I can't quote the NTFS specifics from memory

---

### Post by theozzlives on 2009-05-25
Use [this]("http://ubuntuforums.org/showthread.php?t=1015834"), then drag your folders to the left side of Nautilus, or your dektop.

---

