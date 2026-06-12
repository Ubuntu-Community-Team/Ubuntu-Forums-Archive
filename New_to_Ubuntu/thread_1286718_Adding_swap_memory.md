---
title: "Adding swap memory?"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by scottishbloke on 2009-10-09
Hi im new to ubuntu so please go easy with me,as the title says really how do i go about adding more swap memory?

---

### Post by ninja_style on 2009-10-09
i have the same question! i have 3 partitions. i used to last one for ubuntu but i didn`t make and partition for swap! now i want to deduct few giga from the other partitions and dedicated for the swap file. how can i do that please?!

---

### Post by Bölvaður on 2009-10-09
For this you will need a proper program to (create) resize the partitions.

Either open synaptic package manager under System &#8594; Administration or click this link to install the [GParted]("apt:gparted") (gnome partition editor)


Now you will find it under System &#8594; Administration &#8594; Partition Editor
Or by pressing Alt+F2 and type ```
gksu gparted
```



There are 2 things to remember when you add more swap or make space for a new partition.

You will need to shrink another partition that touches it (sits next to it on the hard disk) and that you need to crop away that is next to the Swap partition.

The partition you shrink should contain as little data as possible, if it is full you will not be able to shrink it at all!

Take backup of the partition you are shrinking! IMPORTANT if you have some document that arent allowed to be deleted if something goes wrong.


The swap partition doesnt need to be bigger than few megabytes on desktop computers. Linux normally doesnt use swap space on modern computers. It is also **many** times slower than RAM, so sway away from thinking swap is a good thing to be using (like windows is known to do).

For laptops swap needs to be a little bit bigger than the average ram usage you have when you hibernate (or just equal size to your ram + ~10% if you want things simple).
For desktops swap can be anything from 200-500mb.

---

### Post by scottishbloke on 2009-10-09
Thankyou very much for your help,if its not really going to be of benefit to me then i will leave it,im finding it difficult to understand all this,but from your reply i dont think i need it.thanks:P

---

### Post by Bölvaður on 2009-10-09
You can open system monitor from System &#8594; Administration to see how much swap you are using. It should sit at 0% at all time, and max at 10mb, but may depend on what programs you are using.

---

### Post by phecht on 2009-10-09
Another method is:

I used the Sysrcd-1.3.0 a.k.a "System Restore CD" from this [http://www.sysresccd.org/download.en.php](http://www.sysresccd.org/download.en.php) site.  I decreased my Ubuntu 9.04 by about 200 MB and moved and re-sized my swap from 74 MB to 274 MB. After rebooting I can build the Hudson project, [http://wiki.hudson-ci.org/display/HUDSON/Building+Hudson](http://wiki.hudson-ci.org/display/HUDSON/Building+Hudson) , that made me happy.    

You will need to burn the ISO to a CD.  I have a Mac so it was pretty simple.  I know Windows has free tools as well.  Once the CD is created take it and boot from the CD on your Ubuntu machine.  

Once it boots, select the first option.  After that you will see a prompt, type 'wizard'.  Once the terminal starts, type 'gparted'.  This will start a partition manager that you can use to move and resize partitions.  It is somewhat nerve racking since it is messy with your live data.  Hopefully you have a backup just in case! 

I have a dual boot Toshiba with Windows XP and Ubuntu 9.04 in dual boot.  I have used the CD several times and haven't had any data loss.  A lot of defrag'ing and chkdsk'ing but no data loss.

---

