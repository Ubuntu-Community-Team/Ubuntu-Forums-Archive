---
title: "Hide folder"
date: 2011-09-06
forum: New to Ubuntu
---

### Post by cacs on 2011-09-06
Hi there!

There are any way to hide a folder?

TY in Advance, C.S.

---

### Post by cacs on 2011-09-06
Hi there!

There are any way to hide a folder?

TY in advance, C.S.

---

### Post by sanderd17 on 2011-09-06
In Linux, folders that start with a dot or end with a ~ are hidden by default.

You can press CTRL+H in Nautilus to show them.

---

### Post by Linux_junkie on 2011-09-06
Yes just rename the folder name with a . (period) at the beginning of the name.  Then if your file browser is set to not to show all files it will be hidden.

---

### Post by Beacon11 on 2011-09-06
Can you please delete your double post here: [http://ubuntuforums.org/showthread.php?t=1839951](http://ubuntuforums.org/showthread.php?t=1839951) ?

As for hiding the folder, are you wanting to hide the folder in Nautilus or the terminal? If it's Nautilus, simply placing a period at the beginning of the folder name (from the terminal) will do it (depending on its settings).

---

### Post by sanderd17 on 2011-09-06
> **Beacon11 said:**
> 

As for hiding the folder, are you wanting to hide the folder in Nautilus or the terminal? If it's Nautilus, simply placing a period at the beginning of the folder name will do it (depending on its settings).

In the terminal this works too.

---

### Post by drs305 on 2011-09-06
For Nautilus, another old trick is to create a file in the same directory as the folder you want to hide called *.hidden*

Open .hidden and add the names of any files or folders in the same directory you wish to hide. 

If the Nautilus is hiding other items, it will also hide any item listed in .hidden

**Moderator Note:** Threads merged. Please create only one thread per topic.

---

### Post by cacs on 2011-09-06
> **Beacon11 said:**
> Can you please delete your double post here: [http://ubuntuforums.org/showthread.php?t=1839951](http://ubuntuforums.org/showthread.php?t=1839951) ?


How can I delete the double post?
I cancelled it but it was posted anyway... sorry.

Thank you for all the answers!

---

### Post by Linux_junkie on 2011-09-06
> **cacs said:**
> How can I delete the double post?
I cancelled it but it was posted anyway... sorry.

Thank you for all the answers!

I think its been done for you.

---

### Post by lisati on 2011-09-06
> **Linux_junkie said:**
> I think its been done for you.

Confirmed.

---

### Post by bariamtak on 2012-01-05
i saw a video in youtube somthing lyk typing  "sudo gksu nautilus" in the terminal and one file browser pops up. then it involves right click and from properties changing the owner and group of the folder to root . The video was for ubuntu 8.10.But when  i tried the same procedure i could not change the owner of the folder or any other attributes from user to root. I am using ubuntu 11.10. is the proccess different for my version or is it becos i need some softwares or application? Or still is it not supported ? if it is possible lyk that, someone please help me out.
    I really like ubuntu (i'll be discarding my win7 ultimate soon). its great that users can help each other.though i dont know much I lyk d flexibility of linux ! and i learn a lot from u guys...thank u.

---

### Post by drs305 on 2012-01-06
bariamtak,

The command to open nautilus as root would be "gksu nautilus". In 11.10, I was able to change ownership as you described.

---

