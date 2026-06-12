---
title: "Beginner help/questions"
date: 2010-02-06
forum: New to Ubuntu
---

### Post by Marauder_IIc on 2010-02-06
Hello,
first off I am very new to Linux based OS's.  It was recommended to use Unbuntu to gain access to a workstation board, while I am waiting for RMA via a Boot from CD Unbuntu OS so I could recover my data form the HDD, so I can work while board is getting replaced.

Question 1)  Can someone provide me with a link for how to make the complete OS bootable from CD/DVD

Question 2)  The data is stored on a LSI SAS array, does Unbuntu have drivers for it, and if not, how would I go about getting them into the OS, when the OS is basically read only?

THanks

---

### Post by Ubu2010 on 2010-02-06
1)[http://www.ubuntu.com/GetUbuntu/download](http://www.ubuntu.com/GetUbuntu/download)

^^ this link leads you to the download, instructions on how to burn an .iso image (the Live CD you will need), and Ubuntu installation instructions if you were to decide to keep Linux.

As for using the CD to retrieve your files, the Live CD should be all you need, other than a place to send the files to once they are retrieved. You dont need drivers to go in there to get the files in other words. Linux (Ubuntu in this case) can retrieve Windows' and many other OS' files. You can do it from the LiveCD. You just will have to store them to another drive, or set of drives. You will probably want to learn about mounting drives but is worth the time invested in learning these things in my opinion. 

Oh, and its Ubuntu ;)

---

### Post by coldfusion1313 on 2010-02-06
> **Marauder_IIc said:**
> 
Question 1)  Can someone provide me with a link for how to make the complete OS bootable from CD/DVD 

Download the 'Desktop Version of Ubuntu" that is a live cd which will allow you to boot of it. Get it here ===> [Ubuntu Download]("http://www.ubuntu.com/getubuntu/download")

> **Marauder_IIc said:**
> Question 2)  The data is stored on a LSI SAS array, does Unbuntu have drivers for it, and if not, how would I go about getting them into the OS, when the OS is basically read only? 
 Can I have the model number of your LSI SAS array? It would help out a lot, in the meantime you should google your array model number and see if other people got it to work.

---

### Post by Marauder_IIc on 2010-02-08
> **coldfusion1313 said:**
> Download the 'Desktop Version of Ubuntu" that is a live cd which will allow you to boot of it. Get it here ===> [Ubuntu Download]("http://www.ubuntu.com/getubuntu/download")


 Can I have the model number of your LSI SAS array? It would help out a lot, in the meantime you should google your array model number and see if other people got it to work.


The SAS controller is embedded on my Supermicro H8DA3-2 motherboard, controller is LSI 1068E SAS Controlle.

Anything you can offer would be greatly appreciated.

---

### Post by coldfusion1313 on 2010-02-08
[http://www.linuxquestions.org/questions/linux-hardware-18/lsi-sas-raid-driver-for-debian-637604/](http://www.linuxquestions.org/questions/linux-hardware-18/lsi-sas-raid-driver-for-debian-637604/)
[http://www.supermicro.com/Aplus/support/resources/OS/OS_Comp_AMD_2.cfm](http://www.supermicro.com/Aplus/support/resources/OS/OS_Comp_AMD_2.cfm)

---

