---
title: "Trying my Ubuntu first installation"
date: 2009-04-08
forum: New to Ubuntu
---

### Post by mosaabJ on 2009-04-08
I'm a beginner in Ubuntu I read a lot about it and about the installation but I still don't understand something that when  partitioning the hard disk when installing Ubuntu 8.10 for Dual-Booting between Ubuntu and Windows XP .
Does this delete all the files in the  Hard Disk.

---

### Post by linux_lover69 on 2009-04-08
Only if you format the entire drive. If you resize the drive then it'll only make another partition for your ubuntu installation.

---

### Post by LowSky on 2009-04-08
creating a partition usually uses free space on a designated drive. So if you want to dual boot with XP I suggest doing a Disk Defragment from Windows before running the Ubuntu Partitioner. this way no files will be corrupted accidentally.
Now this isn't a completely ssfe thing to do on a drive that is fully formatted to Windows. It can break something if done wrong. Personally It never happened to me and many others, but a few have had this issue.

---

### Post by Jakey_TheSnake on 2009-04-08
When partitioning the hard disk it's like cutting it in half. You can boot-up of either half, both of which will remain intact. 

You can even see the Windows half an access it from inside Ubuntu: your files will be fine.

Don't let this stop you in installing Ubuntu! 

How much space does your Hard Drive (HDD) have? And how much are you using? Then I will recommend a size for the partition you will need to create.

---

### Post by LowSky on 2009-04-08
> **Gambitt said:**
> I suggest you to use Wubi. It will smoothly install Ubuntu on your exitsting Windows XP (even on same partition, if you want it so)

Wubi is way to install Ubuntu within Windows. Personally I think it is trash and not worth the hassle. Also Wubi takes up a lot of space and can really cause some odd behavior.

---

### Post by acimmarusti on 2009-04-08
I've read, it is often better to have the hard drive pre-partitioned before attempting a dual boot. You can get windows software (open-source free) that can do this for you without hurting windows: [http://partitionlogic.org.uk/](http://partitionlogic.org.uk/)

Then during the installation of ubuntu format that partition with the file system used by linux (ext3) and you are good to go.

---

### Post by Jakey_TheSnake on 2009-04-08
> **acimmarusti said:**
> I've read, it is often better to have the hard drive pre-partitioned before attempting a dual boot. You can get windows software (open-source free) that can do this for you without hurting windows: [http://partitionlogic.org.uk/](http://partitionlogic.org.uk/)

Then during the installation of ubuntu format that partition with the file system used by linux (ext3) and you are good to go.

You don't need separate software, this is the same as choosing the "Try Ubuntu Without any Change to my Computer" option, going to System > Administration > Partition Editor, creating, and then pressing the "Install" icon on the Desktop. 
The only way this is less risky is if the installer does not know which option would install Ubuntu to a new partition.

Shrinking a partition will always come with risks which are very small, but they can be made smaller with a windows defrag before you partition.

---

### Post by mosaabJ on 2009-04-08
> **Jakey_TheSnake said:**
> When partitioning the hard disk it's like cutting it in half. You can boot-up of either half, both of which will remain intact. 

You can even see the Windows half an access it from inside Ubuntu: your files will be fine.

Don't let this stop you in installing Ubuntu! 

How much space does your Hard Drive (HDD) have? And how much are you using? Then I will recommend a size for the partition you will need to create.
My Total hard disk space is 292 GB and the free space is 121 GB

---

### Post by Jakey_TheSnake on 2009-04-08
I'd give 30-50GB of space to Ubuntu, if I were you, depending on how much you plan to use it.

---

### Post by mosaabJ on 2009-04-09
OK thank you

---

### Post by hesjnet on 2009-04-09
> **LowSky said:**
> Wubi is way to install Ubuntu within Windows. Personally I think it is trash and not worth the hassle. Also Wubi takes up a lot of space and can really cause some odd behavior.

It also is slower than a real install.

---

### Post by Jakey_TheSnake on 2009-04-09
> **mosaabJ said:**
> OK thank you

Let us know if you have any more problems.

---

### Post by mosaabJ on 2009-04-09
Till now I have many problems in my current operating system (Windows XP) there is a virus in the computer and I couldn't even defragment the hard disk because of the virus.

---

### Post by Yvan300 on 2009-04-09
Yeah it really is simple, just use partition editor to resize the windows partition to leave about 50 gb of free space. A good practice would be to then create and extended partition using that free space and then within the extended partition, make 3 logical partitions, one for root(where ubuntu will be installed), one for the home folder(where your music,data etc will be saved,this is a great thing to do incase you decide to change distro's etc and will leave your data intact) and the last partition is for the swap space, which should be twice the amount of ram you got, if you got a lot of ram then it could be less, but make sure you have enough because if your ram runs out and swap space runs out as well then  your pc will crash.

eg. 2gb ram 1 gb swap space :)

---

### Post by Jakey_TheSnake on 2009-04-09
> **mosaabJ said:**
> Till now I have many problems in my current operating system (Windows XP) there is a virus in the computer and I couldn't even defragment the hard disk because of the virus.

Luckily for you, I'm handy with Windows XP. Check your pm's.

---

### Post by Mortus Pryde on 2009-04-09
> **mosaabJ said:**
> Till now I have many problems in my current operating system (Windows XP) there is a virus in the computer and I couldn't even defragment the hard disk because of the virus.
Personally I used WUSI till I got the general feel of Linux, and then did a full install on a new hard drive. The stock 40 was too small to begin with even for a grab and go essentials drive. Messed it up about 10 times trying to figure out video drivers and such. Starting with an IBM T42 so video drivers were "fun" though the out-of-the-box drivers work just fine for anything non-3D, now think I have that mostly sorted so I have a full install on it now, if only I can boost the 3D performance.

As for the Window, and I know this is off topic, but I am sure it will be your next task to tackle one way or another. Do you have an antivirus program installed on your Windows, and up to date, and still functional and it failed to remove the virus? If so your alternative if you can get on the internet and have Java installed go housecall.trendmicro.com, for now this is safest done in Windows so it can not remove any critical system files if they are infected. I am not sure if the Live CD is java enabled or I would suggest your last resort for removing the virus so you can defrag and repartition safely is to run housecall from the Live CD and see if it can remove the infection though this may also remove system files if they are infected, and this is why it would be your last resort.

Bare in mind I am new to Linux to and the above advice on your virus issue is entirely based on my Windows experiance. Perhaps the others have a more Linux related solution.

---

