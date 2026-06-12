---
title: "Uninstalling Ubuntu"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by lyrilmaki on 2011-01-05
Hi there, I wanna to uninstall my Ubuntu 10.10 from my laptop, can anyone guide me? 

I installed my Ubuntu at a new partition which only contain the installed Ubuntu.. Can I uninstall it by just formating the partition ? :confused:

---

### Post by mastablasta on 2011-01-05
> **lyrilmaki said:**
> I installed my Ubuntu at a new partition which only contain the installed Ubuntu.. Can I uninstall it by just formating the partition ? :confused:
 
yes or you can also go to disk manager and just delete partition format it or format&add the space to your other OS partition.

---

### Post by TNT1 on 2011-01-05
May not be strictly relevant, but why do you want to remove Ubuntu? Maybe it's something we can help you with so you can use it properly?

---

### Post by NightwishFan on 2011-01-05
You will need a recovery disk for your OS of choice.

---

### Post by lyrilmaki on 2011-01-05
I am changing laptop, so I need to format and left it with Window 7 to let my mommy use XD

---

### Post by presence1960 on 2011-01-05
before you remove ubuntu you should fix the MBR so GRUB is off and replaced with a windows or windows compatible bootloader. You can do this by booting to ubuntu. Open a terminal and run ```
sudo apt-get install lilo
```

Ignore warnings and proceed. next in terminal run ```
sudo lilo -M /dev/sda mbr
```This will fix the MBR to boot windows. 

Now boot to windows and open the disk management utility and delete the ubuntu partition(s).

Failure to change the MBR to boot windows prior to removing linux will result in a boot failure, specifically a GRUB command prompt.

---

### Post by mastablasta on 2011-01-06
> **presence1960 said:**
> Failure to change the MBR to boot windows prior to removing linux will result in a boot failure, specifically a GRUB command prompt.
 
and if this is the case you would need windows recovery cd to fix the main boot record.: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by presence1960 on 2011-01-06
> **mastablasta said:**
> and if this is the case you would need windows recovery cd to fix the main boot record.: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

Exactly, that's why I provided the lilo solution from ubuntu prior to removing ubuntu because everyone does not have a disc(s) due to recovery partitions.

---

### Post by lyrilmaki on 2011-01-06
Thank you so much for helping me ^^

---

### Post by Gregco on 2011-01-14
Hi,
Ive just registered on forum and Im new to this. My friend had  previously installed Ubuntu through Sun Virtualbox on my Samsung NC10  Network which I upgraded ram from 1 to 2gb. The problem is that my  system is almost full and sometime freezes. I wanted to uninstall Ubuntu  from Virtualbox or if I uninstall Virtualbox will that successfully  uninstall Ubuntu and its partition.
Thank you.

---

