---
title: "Partitioning Help"
date: 2011-08-19
forum: New to Ubuntu
---

### Post by mintpenguin20 on 2011-08-19
I need help partitioning Linux Mint 11 , I want to give the OS like 40GB and have the rest of my drive for my files like movies , pictures , music ect . I want to do this because when I update to the next version of Linux Mint I wont have to delete all my files . How do I do this please help I tried but didnt understand what mount points are and I dont know excactly how my setup should be , I have a 320 GB HD if you could help me step by step I would really appreciate it a lot , I know Mint isnt Ubuntu but it is based on it and is pretty much the same thing besides the UI . I am not using windows at all either just letting you know I am not dual booting anything at all just plain old Linux Mint 11 as my 1 OS .

---

### Post by Basher101 on 2011-08-19
first: do you already have data on your hdd or did just a fresh install of mint?

second:i will gladly provide you with some screenshots, although my partitions will look different since i wont actually partition them, just show you where to press what.

third: i am on windows right now and i will switch to ubuntu in a few minutes to make those screenshots. Please post your answer to my questions in that time

---

### Post by mintpenguin20 on 2011-08-19
> **Basher101 said:**
> first: do you already have data on your hdd or did just a fresh install of mint?

second:i will gladly provide you with some screenshots, although my partitions will look different since i wont actually partition them, just show you where to press what.

third: i am on windows right now and i will switch to ubuntu in a few minutes to make those screenshots. Please post your answer to my questions in that time

 I do not need anything on the hard drive right now . It will be a fresh install of Linux Mint 11 64 bit , basically I want 40GB for mint and all of the stuff it needs and I want the rest of my hard drive to be for all my files videos , music , pictures , ect .

---

### Post by Basher101 on 2011-08-19
okay so now im on linux. Okay this makes it quite easy. so you wanna wipe your hdd clean and just install only Mint on it? did i get the right idea? or do you want something else? keeping the OS partition small is a very wise choice. I dualboot with windows 7 and gave win 30 gb, ubuntu 15 gb, a massive 550gb shared storage partition (for movies, music ect.) and at the end 4gb for linux swap.

Please provide me with as much details as possible on how you want your hdd partitioned

---

### Post by mintpenguin20 on 2011-08-19
> **Basher101 said:**
> okay so now im on linux. Okay this makes it quite easy. so you wanna wipe your hdd clean and just install only Mint on it? did i get the right idea? or do you want something else? keeping the OS partition small is a very wise choice. I dualboot with windows 7 and gave win 30 gb, ubuntu 15 gb, a massive 550gb shared storage partition (for movies, music ect.) and at the end 4gb for linux swap.

Please provide me with as much details as possible on how you want your hdd partitioned

Yes I only want mint no other OS , I need help figuring out how to partition it , I want to give mint 40 GB and the rest just for files . I just dont understand how to make a swap and how big it should be and I dont understand the mount things what are you supposed to name them ?

I want MINT to be 40GB thats including the swap and what ever else it requires 
I want the rest to be a partition only for files 
I am using a 320 GB Hard Drive .

---

### Post by jerrrys on 2011-08-19
ok, sounds like to me that you want nothing more that personal files to be on a  separate partition.  

what i did was just to create and ext4 (non-bootable) partition or HDD.  never ran mint, but this is done in ubuntu by using the live cd and gparted.

---

### Post by Basher101 on 2011-08-19
For my examples i will format my USB flash drive and make a few partitions and screenshot it how i make them. simply follow these steps (just adjust the size of the partitions, as my usb only has 8 gigs) i will make the screens now..it should take a few minutes. also i will add big red arrows with gimp to point you on what you must exactly do.

---

### Post by mintpenguin20 on 2011-08-19
> **Basher101 said:**
> For my examples i will format my USB flash drive and make a few partitions and screenshot it how i make them. simply follow these steps (just adjust the size of the partitions, as my usb only has 8 gigs) i will make the screens now..it should take a few minutes. also i will add big red arrows with gimp to point you on what you must exactly do.

K I will wait for you thanks .

---

### Post by Basher101 on 2011-08-19
okay i made all the screenshots. they are 14 screens, with step by step instructions, tho i will have to add the red arrows and write the instructions. Thank you for your patience

---

### Post by mintpenguin20 on 2011-08-19
> **Basher101 said:**
> okay i made all the screenshots. they are 14 screens, with step by step instructions, tho i will have to add the red arrows and write the instructions. Thank you for your patience

K just tell me where to get them , and I really appreciate all of your effort you are being very helpful .

---

### Post by ajgreeny on 2011-08-19
The simplest way to do what you want is to follow the instructions at [Separate home at install.]("http://www.psychocats.net/ubuntu/installseparatehome") which will give you a partition for all your data files and the configuration files and folders which  by default, are placed in /home.

This page is for ubuntu, but the basic operations are exactly the same for Mint.

---

### Post by Basher101 on 2011-08-19
Okay now. Just follow these steps:

Step 1: Open GParted and delete all the current partitions on your drive.

Step 2: Rightclick on the "unallocated space" and click new. Then create your OS partition. For 40 GB you must enter 40960 MB in the new size box. Also make sure that you select ext4 as your filesystem.

Step 3: Create an extended partition that will hold all the other ones you will create. For this use ALL the remaining unallocated space.

Step 4: Create an partition for your /home directory. In your home directory all your settings, music, documents and downloads will be saved there, so make it big as it will function as your storage.

Step 5: Create a Swap partition. The swap must only be twice as big as your RAM if you have a desktop, and exactly as big as your RAM if you use a laptop.

Step 6: Apply all your partitioning. This will partition your disk with your custom made partition table. All changes will be permanent (unless you repartition again)

Step 7: now start the installer for mint. Make sure you select your partitions of your hdd. It should be /dev/sd***_a_*** instead of /dev/sdb if its your internal hdd. Also make sure to select where your bootloader will be installed to. Make sure that the bootloader is installed to the HDD itself, ***_/dev/sda_*** not a partition like /dev/sda1

Step 8: Select the first partition /dev/sda***_1_***. Then the window on the screen will pop up. Here you will tell the mount points (whats should be installed where).

Step 9: For your OS set it to "/" as the mount point like on the screen. Also select ext4 as filesystem and check the format box.

Step 10: Select the second partition (the big one for storage) and select ext4 as the filesystem and make the mount point to "/home".

Step 11: Select your swap partition and select linux swap as the filesystem. Now your all done and can click the install button.


Hope this is clear enough. If you have any questions ask them, i will gladly answer them.

---

### Post by Basher101 on 2011-08-19
i just noticed i can only upload 5 screens at a time. Here come the other steps

---

### Post by Basher101 on 2011-08-19
and the last one

ps. i will make a quick reboot as i just made a kernel update. brb

---

### Post by mintpenguin20 on 2011-08-19
So when I make a /home partiton that will be where I keep my files ?  So / will be where MINT is installed ? Will this allow me to keep all my files when i eventually do a clean install of latest version of mint when it is released in October ?

---

### Post by mintpenguin20 on 2011-08-19
> **Basher101 said:**
> and the last one

ps. i will make a quick reboot as i just made a kernel update. brb

So the /home will be saved when I eventually do a clean install of the latest mint in October ?

When it comes out in October  do I just reformat the other  2 partitions and leave /home alone ?

---

### Post by Basher101 on 2011-08-19
/home contains all your personal data and configurations. If you also want to keep your programs you will have to make another partition for /usr. But i dont think this will be necassary, sicne doing fresh installs of programs is also better.

---

### Post by mintpenguin20 on 2011-08-19
> **Basher101 said:**
> /home contains all your personal data and configurations. If you also want to keep your programs you will have to make another partition for /usr. But i dont think this will be necassary, sicne doing fresh installs of programs is also better.

So when the next version comes out in October and when I do a clean install do I just format the operating system partition and the swap or do I have to delete them and recreate those 2 partitions ? Thanks again for your help I really would be lost with out you lol .

---

### Post by Basher101 on 2011-08-19
I was lost too, formatted my HDD 16 times total (after i backed up windows on an external hdd huzzah) and well i got some serious experience with that^^
you just need to format the OS partition and place "/" as the mount point. The thing i dunno is if it will "recognize" your /home partition and note "make" a new one inside the "/" partition. I hope someone else could answer that but i simply dont know. Glad i could help ya pal, i literally rape the "New Posts" button to help out noobs as i know too good how not nice it is to have partitioning problems^^

---

### Post by mintpenguin20 on 2011-08-19
> **Basher101 said:**
> I was lost too, formatted my HDD 16 times total (after i backed up windows on an external hdd huzzah) and well i got some serious experience with that^^
you just need to format the OS partition and place "/" as the mount point. The thing i dunno is if it will "recognize" your /home partition and note "make" a new one inside the "/" partition. I hope someone else could answer that but i simply dont know. Glad i could help ya pal, i literally rape the "New Posts" button to help out noobs as i know too good how not nice it is to have partitioning problems^^

Yeah I appreciate it I know it probably took a lot of effort and time to do what you did and it really did help . Partitioning is not fun lol .

---

### Post by Basher101 on 2011-08-19
Its not something you should do on a daily basis...still knowing how to do it will often safe you alot of time, stress and money

---

