---
title: "how do i change the partition?"
date: 2011-06-13
forum: New to Ubuntu
---

### Post by subalster on 2011-06-13
sorry im completly new to this, i've figured out that i need to change the partition so that i have more room to do stuff with ubuntu and i have found the disk utility device but im not quite sure where to go from here.....
please help

---

### Post by Quackers on 2011-06-13
Welcome to UF.
If you open synaptic package manager and in the search box enter gparted it will appear in the main screen. Right-click on gparted and select mark for installation then click on the green tick in the toolbar to apply the change and then OK the box.
After installation go to System > Admin > gparted and open the program.
Please post a screenshot of that program screen in your next post (using attachments). This will give a better idea of your partition layout.

---

### Post by mike555 on 2011-06-13
If you installed Ubuntu using "Wubi" then it's inside Windows and I don't think you can change it ........... I suggest you use a live cd Ubuntu and gparted to make a separate partition .......... but you should read more about how to first ...

---

### Post by JohnBonne on 2011-06-13
> **subalster said:**
> sorry im completly new to this, i've figured out that i need to change the partition so that i have more room to do stuff with ubuntu and i have found the disk utility device but im not quite sure where to go from here.....
please help

To use Ubuntu you need a few Gigabytes of HDD and a swap file the size of your physical Memory. I use a 40 Gig Partition for Linux Mint and a 3 Gig Swap partition. To do this I prefomatted both of them using Windows and Grub2. My take on this, as I am new to Ubuntu and Linux, is to lay out what you want your drives to look like when you are completely finished. maybe two operating systems each with their own swap files and aware of each other?

I want three operating systems. I am having problems because didn't map the drives accordingly. I  didn't know I needed one whole drive for beta testing new operating systems or even that such an idea existed.

Maybe some day you can prevent others from making the same mistakes you have made.

---

### Post by subalster on 2011-06-13
ok i got the g parted partion editor and i took a picture and it should be attached to this

---

### Post by subalster on 2011-06-13
how about i just delete windows is that easier?

---

### Post by psusi on 2011-06-13
Since you did a WUBI install, Ubuntu exists as a file inside Windows.  To get rid of Windows, you will need to reinstall Ubuntu.

---

### Post by subalster on 2011-06-13
hmmmmmm the plot thickens

---

### Post by wildmanne39 on 2011-06-14
> **subalster said:**
> hmmmmmm the plot thickens

Hi, you can use this guide to expand your partition in a wubi installation, but I would go for the real install, it is totally up to you.
[http://ubuntuforums.org/showthread.php?t=1625371](http://ubuntuforums.org/showthread.php?t=1625371) The second guide tells you how to turn your wubi install into a normal install if you want too.
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

---

### Post by JohnBonne on 2011-06-14
I think anything short of erasing everything will cause problems later. That you need to plan out the lay-out beforehand to save the problems that will occur, or a manual install. This Linux whole reminds me of overhauling a D 8 caterpillar, I jest you not.

:popcorn:

---

### Post by AlbaKirkee on 2011-06-14
I would like a recommendation for an ISO program to re-partition a Linux drive.  I was thinking of using Partition Logic version point seven, but I don't know how good it works with Linux [Ubuntu] partitions..... Thanks....

---

### Post by oldfred on 2011-06-14
@AlbaKirkee
We mostly use gparted. Still suggest using the windows MMC only to shrink a Vista/7 windows partition.

Gparted in on the Ubuntu liveCD or you can download liveCDs with gparted.

[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)
[http://partedmagic.com/](http://partedmagic.com/)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

