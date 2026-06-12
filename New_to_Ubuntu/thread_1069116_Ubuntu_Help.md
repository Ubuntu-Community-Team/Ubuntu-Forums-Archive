---
title: "Ubuntu Help"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by sk7499 on 2009-02-13
I am trying to setup a dual boot XP and ubuntu.  I have XP currently installed on the CPU i can load ubuntu fine i try to resize the partition  i have a 160gb hardrive giving ubuntu 60gb but i get an error when i resize the partition an error has occured.  Should be able to resize the partition im trying to install ubuntu 8 the new version from a cd.

---

### Post by overdrank on 2009-02-13
Hi and welcome, moved to Absolute Beginner Talk

---

### Post by ugm6hr on 2009-02-13
1. Backup important files first (resizing partitions can cause datat corruption).
2. Boot from Ubuntu LiveCD - select "Try without making any changes" option
3. In Ubuntu Menu: System -> Aministration -> Partition Editor
4. Select correct HD (if you have more than one)
5. Resize XP partition to 100GB (right-click on HD coloured box gives options)
6. Apply changes (make sure files are backed up!)
7. Double-click Install on desktop
8. Select "Guided - Install using largest free space" option.

Hopefully the rest should be pretty obvious.

---

### Post by Captain_tux on 2009-02-13
Also, be sure to defrag and run **chkdsk** the drive at least once (perhaps twice!) before you begin the partitioning.

Good luck and welcome to Linux/Ubuntu!

---

### Post by sk7499 on 2009-02-19
It says an error occured while applying operations i cannot get to the install screen as it will not apply it does xp have a restriction that it does not allow a resize of the partition.

---

### Post by Kareeser on 2009-02-19
No, but due to the fragmented nature of the NTFS file structure, bits and pieces of files are strewn all over your hard drive, including places you want to resize for your Ubuntu partition.

Did you run defrag on Windows before trying to install Ubuntu?

---

### Post by sk7499 on 2009-02-19
i defrag the drive and ran scan dish all is compacted this was a new xp install any way fresh xp new laptop no new programs not sure what the issue is there a restriction somewhere

---

### Post by sk7499 on 2009-02-19
ill keep you posted i think i might have it.

---

### Post by Peter09 on 2009-02-19
Make sure you shutdown XP completely, do not hibernate the O/S as it can leave the file system in an indeterminate mode.

---

### Post by sk7499 on 2009-02-19
ojk got it to work i neeed some more assistance i need to install wireshark on ubuntu how do i do this thanks for everyones help after running chkdsk 5 times and defraging the drive it took.

---

### Post by Ocxic on 2009-02-19
in terminal "sudo apt-get install wireshark" or select in from synaptic System->admin->Synaptic package manager.

I also use etherape which is pretty cool, and may be of use aswell.

---

### Post by sk7499 on 2009-02-26
I tried the Sudo which should be a download howver i cannot get it to download.  i get the following error cant find package wireshark.

MY IE connection is good.

---

### Post by ugm6hr on 2009-02-26
The package is definitely in the standard "repository":
[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=wireshark](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=wireshark)

If you are using Ubuntu 8.x with a working internet connection, it should work.

Copy and paste the exact output from the command here.

Also, the contents of :
```
cat /etc/apt/sources.list
```

---

### Post by Sidewinder1 on 2009-02-26
This site was invaluable to me when learning how to dual boot with XP and ubuntu:
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
As stated above, defrag is a must, even with a new install.
HTH
Side

---

### Post by Sidewinder1 on 2009-02-26
Sorry, I missed post #10. Disregard the above. A thousand pardons. :-)

---

### Post by sk7499 on 2009-03-02
When I download thies what do i do next i have ubuntu 8  new version how do i install it can you provide a step by step still trying to figure out linux.  The package is definitely in the standard "repository":
[http://packages.ubuntu.com/search?su...ords=wireshark](http://packages.ubuntu.com/search?su...ords=wireshark)

---

### Post by ugm6hr on 2009-03-02
> **sk7499 said:**
> what do i do next 

Respond with the details requested.

Try clicking here: [wireshark]("apt:wireshark")

---

### Post by sk7499 on 2009-03-12
The link provided wont work also when i do sude ect it states package not found is there a step by step tutorial on how to do this

---

