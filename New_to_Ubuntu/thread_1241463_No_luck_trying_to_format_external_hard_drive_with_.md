---
title: "No luck trying to format external hard drive with gparted"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by jalehtor on 2009-08-16
I was given an external hard drive which a friend used for a short time with a mac laptop. He saved some info on it, but he said that he had never formatted it.

I have a 40GB internal hard drive, and, ultimately, I'll be partitioning it between Ubuntu and xp, xp for games, Ubuntu for everything else. I wanted to format the external hard drive for ntfs and save my files on it to create more space on the hard drive. 

So I got gparted, sudo apt-get install gparted ntfsprogs unmounted the hard drive, and tried to get gparted to work, and gparted would not work. I booted from the live Ubuntu cd, and the same thing happened. 

Btw, when the hard drive is mounted, then the gparted screen will show up, but the partition-format is grey and can't be used. 

What am I doing wrong? 

Also, if I ever get this bit working, which would be simpler (not faster) for a technically challenged person: to install xp over ubuntu, and then try the partition for ubuntu after that, or to try the dual boot with xp starting with Ubuntu?

---

### Post by mrbiggbrain on 2009-08-16
> **jalehtor said:**
> I was given an external hard drive which a friend used for a short time with a mac laptop. He saved some info on it, but he said that he had never formatted it.

I have a 40GB internal hard drive, and, ultimately, I'll be partitioning it between Ubuntu and xp, xp for games, Ubuntu for everything else. I wanted to format the external hard drive for ntfs and save my files on it to create more space on the hard drive. 

So I got gparted, sudo apt-get install gparted ntfsprogs unmounted the hard drive, and tried to get gparted to work, and gparted would not work. I booted from the live Ubuntu cd, and the same thing happened. 

Btw, when the hard drive is mounted, then the gparted screen will show up, but the partition-format is grey and can't be used. 

What am I doing wrong? 

Also, if I ever get this bit working, which would be simpler (not faster) for a technically challenged person: to install xp over ubuntu, and then try the partition for ubuntu after that, or to try the dual boot with xp starting with Ubuntu?

Use the Gparted live cd, not ubuntu. that way nothing is mounted automaticly. also, mount the device, open gparted, then unmount useing gparted...

---

### Post by jalehtor on 2009-08-16
> **mrbiggbrain said:**
> Use the Gparted live cd, not ubuntu. that way nothing is mounted automaticly. also, mount the device, open gparted, then unmount useing gparted...

Thank you, will try tomorrow :)

---

### Post by mrbiggbrain on 2009-08-16
> **jalehtor said:**
> Thank you, will try tomorrow :)

Iv had nothing but issues useing gparted from non-live cd's, but gparted's live cd always works, i use it OFTEN

---

### Post by jalehtor on 2009-08-16
> **mrbiggbrain said:**
> Iv had nothing but issues useing gparted from non-live cd's, but gparted's live cd always works, i use it OFTEN

I downloaded the iso file, burned it onto a cd, opened with cd/dvd creator, and when it finished with the cd, I can't find the program.

Did I copy the wrong thing onto the cd?

---

### Post by mrbiggbrain on 2009-08-16
> **jalehtor said:**
> I downloaded the iso file, burned it onto a cd, opened with cd/dvd creator, and when it finished with the cd, I can't find the program.

Did I copy the wrong thing onto the cd?

DId you copy the file itself, or have the program do a ISO image burn (as iso files are copys of disks themselves)

---

### Post by jalehtor on 2009-08-16
> **mrbiggbrain said:**
> DId you copy the file itself, or have the program do a ISO image burn (as iso files are copys of disks themselves)

I don't know. I downloaded the iso, then opened with the cd/dvd creator. I must have copied the file itself. How do I do an ISO image burn?

---

### Post by mrbiggbrain on 2009-08-16
if you have access to a windows pc currently (as you sed you would be setting one up) i commonly use iso-burner

[http://www.ntfs.com/iso-burning.htm](http://www.ntfs.com/iso-burning.htm)

IF you have access to ubuntu

# Insert a blank CD into your burner. A "CD/DVD Creator" or "Choose Disc Type" window might pop up. Close this, as we will not be using it.
# Browse to the downloaded ISO image in the file browser.
# Right click on the ISO image file and choose Write to Disc.
# Where it says "Write disc to" you may have options such as "File image" as well as your CD drive. Choose your CD drive. Your CD drive may show as something like "BD-MLT UJ-210S"
# Select the write speed. If you are burning a Ubuntu Live CD (one that you may want to boot from), it is recommended that you write at the lowest possible speed.
# Start the burning process.
# After burning completed, verify that your CD contains multiple files and folders and not just the ISO file. This way you will know the process was performed correctly.

thats from [https://help.ubuntu.com/community/BurningIsoHowto#Ubuntu](https://help.ubuntu.com/community/BurningIsoHowto#Ubuntu)

---

### Post by kiridude on 2009-08-16
Right click your ISO image and select "write to disk."

It is a 2 click procedure :)

---

### Post by jalehtor on 2009-08-16
> **mrbiggbrain said:**
> if you have access to a windows pc currently (as you sed you would be setting one up) i commonly use iso-burner

[http://www.ntfs.com/iso-burning.htm](http://www.ntfs.com/iso-burning.htm)

IF you have access to ubuntu

# Insert a blank CD into your burner. A "CD/DVD Creator" or "Choose Disc Type" window might pop up. Close this, as we will not be using it.
# Browse to the downloaded ISO image in the file browser.
# Right click on the ISO image file and choose Write to Disc.
# Where it says "Write disc to" you may have options such as "File image" as well as your CD drive. Choose your CD drive. Your CD drive may show as something like "BD-MLT UJ-210S"
# Select the write speed. If you are burning a Ubuntu Live CD (one that you may want to boot from), it is recommended that you write at the lowest possible speed.
# Start the burning process.
# After burning completed, verify that your CD contains multiple files and folders and not just the ISO file. This way you will know the process was performed correctly.

thats from [https://help.ubuntu.com/community/BurningIsoHowto#Ubuntu](https://help.ubuntu.com/community/BurningIsoHowto#Ubuntu)

Thank you! Of course I wasted my last cd on the previous of many errors, so will really have to wait till tomorrow to do this. THANK YOU!

---

### Post by jalehtor on 2009-08-16
> **kiridude said:**
> Right click your ISO image and select "write to disk."

It is a 2 click procedure :)

A 2 click procedure is, for me, a two week hassle. Ubuntu is not easy for me, but I've been sticking with it because of awful memories of what happened with xp. Don't ask. 

Thank you.

---

