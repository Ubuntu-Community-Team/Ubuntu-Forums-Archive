---
title: "Partitioning for Jaunty"
date: 2009-05-20
forum: New to Ubuntu
---

### Post by Thurgood Stubbs on 2009-05-20
I am trying to install 9.04 to dual boot with Windows XP.  I have a relatively full HD as it is and was planning on leaving my files on the Windows partition, giving Ubuntu a 9 GB partition and I would have 5 GB of free space left (on the Windows partition).

In the "partition" step of the install I have the option to 1) Install side by side, 2) Use the entire disk (No), 3) Use the largest continuous free space, 4) Specify partitions manually.  Given what I just said (I want to create a 9 GB partition for Ubuntu and try to leave everything else alone) what is the easiest way to do this?  Thanks.

---

### Post by Thurgood Stubbs on 2009-05-20
Oops.  For some reason I couldn't select the slider before but I got it to work.

---

### Post by damis648 on 2009-05-20
Just choose side by side and you should be good to go. :popcorn:

---

### Post by sailthesea on 2009-05-20
You may be able to get a bigger space after you defrag XP a couple of times And don't forget to make a swap partition if you intend to keep your files in windows Install will let you do a dry run before you part the disc so make sure you are happy with the setup you have Happy days;)

---

### Post by powel212 on 2009-05-20
In windows:

1.) hit start - right click on the "my computer" select "manage".

2.) Choose Disk Mangement

3.) create a partition the size for the Ubuntu install
     (try shrinking the windows volume to make more space available.)

4.) Once you have created some free space for Ubuntu, DO NOT FORMAT IT!

5.) If everything is as it should be you now have a windows partition and a chunk of unallocated and unformatted space.

6.) Put in the Ubuntu live CD and Reboot.

7.) Run the Ubuntu install and when you arrive at the partitioning portion of the install select use largest continuous free space.

8.) Do NOT touch or move the slider.

9.) Ubuntu will now install into the space we created and left empty before when we were in windows. This will not make any changes to your windows partition.

....

10.) go to tigerdirect.com or newegg.com and checkout prices of internal harddrives. Drives are so cheap these days I would recommend eating mac and Cheese for a couple weeks and then going out and buying a Terabyte drive as they are only about a hundred bucks these days.

Powel

---

