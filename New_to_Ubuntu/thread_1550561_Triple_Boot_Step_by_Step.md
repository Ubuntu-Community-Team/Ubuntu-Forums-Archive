---
title: "Triple Boot Step by Step"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by babribeiro on 2010-08-11
As of personal interest and also for general people , im here to ask if it is possible to make and simple and step by step tutorial of how to install a triple boot.

I personally would like the following:

On a 500 gb hardisk ( laptop )
100 for OS
400 for data

On the OS partition:

Windows 7   ( default boot )
Ubuntu  ( latest version )
Qimo ( for my kids )

I wonder if anyone could tell me how to make this , step by step. 
I also Suggest but is make a tutorial for triple boot with maybe so screens for everyoine that might be interested.

Thanks all.

PS: I searched the forum , but couldn't find much related to this, so if i opened this topic when there someone other , i apologize.

</div>

---

### Post by QLee on 2010-08-11
[QUOTE=babribeiro]As of personal interest and also for general people , im here to ask if it is possible to make and simple and step by step tutorial of how to install a triple boot.[/QUOTE]

Sorry to be the bearer of bad news but, no, it isn't possible to make that simple step-by-step you want. That's because what has to be done depends a great deal on which versions of which operating systems and which bootloader one chooses to do the booting. This is a classic case of one size does not fit all. 

However, there is lots of documentation, help threads, wiki articles, website articles on dual and multi booting so you should be able to find things that apply in your specific case.

[QUOTE=babribeiro]I personally would like the following:

On a 500 gb hardisk ( laptop )
100 for OS
400 for data

On the OS partition:

Windows 7   ( default boot )
Ubuntu  ( latest version )
Qimo ( for my kids )

...[/QUOTE]

Well, that doesn't make sense. There is no "OS partition", probably you mean a separate partition for each OS (but then the numbers don't work out). I suggest you not try this multi-boot you want until you research a bit more because in this help forum people will tell you how to do something if you ask because they will assume you know what you are doing, so it is critical that you ask the correct question to avoid confusion.

[QUOTE=babribeiro]PS: I searched the forum , but couldn't find much related to this, so if i opened this topic when there someone other , i apologize.[/QUOTE]

That's odd, as there is a wealth of information available on this topic, similar questions get asked a lot. After you have researched and determined what you want, you could post back with what you propose (the step-by-step) and people will be able to spot any errors or steps where you need to be careful and thus help you customise a procedure that will work for your specific situation.

---

### Post by Mark Phelps on 2010-08-11
Don't know where you searched, but you would do better searching the Installations subforum, rather than here.

---

### Post by jakupl on 2010-08-11
however, it's not hard. This is what I would do in your case:

300 Gb for Windows (NTFS)
20 Gb for Ubuntu (EXT4)
10 Gb for Qimo (EXT4)(this is probably way too much)

170 Gb logical partition containing:
2 Gb linux swap
50 Gb /home partition for Qimo (EXT4)
118 Gb /home partition for Ubuntu (EXT4)


Create the partitions first by popping in an Ubuntu live cd and going to Gparted (alt + F2 and type gparted)

Install windows before the other ones, make sure you install it to the 300 Gb NTFS partition.

Then install Qimo and then Ubuntu. When you install qimo and ubuntu, you need to use the "custom partitoning" option, and specify the correct root and /home partition for each.

When you have installed Ubuntu, it should have detected windows and Qimo. But it will boot Ubuntu after 10 seconds if you don't select windows. This is easy to change.

---

### Post by jakupl on 2010-08-11
The only semi hard thing to do, is choosing the correct partitions while installing the linux stuff. But you are welcome to ask if you have some questions.

---

### Post by jakupl on 2010-08-11
altso, if you have windows already, be sure to defrag it several times first. Then you can pop in the ubuntu live cd. and simply resize the windows partition, so it matches the partition scheme that I made.

EDIT: i feel obliged to tell you, that partitioning is never 100% safe. backup your stuff so you don't loose precious files

---

### Post by babribeiro on 2010-08-11
Thanks for the reply.

I meant os partition as in:

50 for win7
40 for ubuntu
8 for qimo
2 for swap
i wonder if this is possible.

And the remaining 400 to be shared as a only data partition and not programs.

I did find some useful info after sometime more search , but was mostly about dual boot.

I basically a noob on linux, although i had installed and uninstalled several times but that pretty much it..

As for know i think i got much inform which i can move on and try
Thanks a lot for the help.

---

### Post by jakupl on 2010-08-11
> **babribeiro said:**
> Thanks for the reply.

I meant os partition as in:

50 for win7
40 for ubuntu
8 for qimo
2 for swap
i wonder if this is possible.

And the remaining 400 to be shared as a only data partition and not programs.

I did find some useful info after sometime more search , but was mostly about dual boot.

I basically a noob on linux, although i had installed and uninstalled several times but that pretty much it..

As for know i think i got much inform which i can move on and try
Thanks a lot for the help.

Yeah that's altso fine, but then you don't have seperate /home partitions. But that's fine.

---

### Post by jakupl on 2010-08-11
Remember that a harddisk can't have more than 4 primary partitions, so you will need to make an extended partition.

---

### Post by babribeiro on 2010-08-11
> **jakupl said:**
> Remember that a harddisk can't have more than 4 primary partitions, so you will need to make an extended partition.


Ic , OK thanks a lot , i will try it out soon and for anything i will try search better around the forum.


all the best

---

