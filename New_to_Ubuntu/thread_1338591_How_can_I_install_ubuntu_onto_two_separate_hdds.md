---
title: "How can I install ubuntu onto two separate hdds?"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by davidstri on 2009-11-26
I have a windows partition (sda1, 20GBs) and an empty partition (sda5 40GBs) on the first hdd. I have a second hdd (sdb 20GBs) that is empty. I want to install ubuntu onto sda5 and sdb thus having an ubuntu 9.10 OS with 60GBs of free space. Is there a way to do this? Thanks for your help.

---

### Post by louieb on 2009-11-26
Just a thought. 20GB is plenty of space for Ubuntu. Install it there. Then you can use the 40GB partition on the other drive for data (music, photos, documents ... (simple and keeps your data in a different partition from the OS).

Another option is to use manual partitioning and mount the 20GB partition as / (root)  and mount the 40GB partition as /home.

---

### Post by celticbhoy on 2009-11-26
> **davidstri said:**
> I have a windows partition (sda1, 20GBs) and an empty partition (sda5 40GBs) on the first hdd. I have a second hdd (sdb 20GBs) that is empty. I want to install ubuntu onto sda5 and sdb thus having an ubuntu 9.10 OS with 60GBs of free space. Is there a way to do this? Thanks for your help.

I would install Ubutnu onto sdb & use sda5 as the home partition. If you search google you will find many how-to's for this.

Basically when you install set the mount point for sdb to '/'
abd for sda5 to '/home'.

---

### Post by davidstri on 2009-11-26
Thank you louieb and celticbhoy! That is just the answer I was looking for! Louieb, are either of your options better?

---

### Post by davidstri on 2009-11-26
Is there a difference about logical and primary, and should I set the partitions on ext4?

---

### Post by celticbhoy on 2009-11-26
By setting separate root and home partitions then it all works seamlessly. If you set one as a data partition then you have to remember to store on it or create symbolic links.

You can have a look here :-

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Basically you get to the bit in installation and select manual configuration. and select each partition and select its use. And yes Ext4 for both.

---

### Post by louieb on 2009-11-26
> **davidstri said:**
> ... Louieb, are either of your options better?

Both are good - a separate /home allows you keep your program settings in case you mess your system up and have to reinstall.  Having the other partition data only is a little safer for your data.   

> Is there a difference about logical and primary, and should I set the partitions on ext4?

There is a difference between logical and primary partitions, but Linux does not care - not a problem installing or using either.  

Not all Linux distributions support ext4 yet.  Other than that you can't go wrong with ext3 or ext4.

:D Full of turkey and the Dallas Cowboys are winning - life is good - happy holidays - think I'm going to take a nap.

---

### Post by kansasnoob on 2009-11-26
I'd personally dread having / and /home on different drives!

Two drives spinning at the same time? Why?

Then again I'm a tree hugger.

---

### Post by davidstri on 2009-12-08
Okay, here is my log of almost everything I did and what went wrong.
1. Installed Ubuntu onto sda then I tried installing windows onto sdb but windows wanted to install something onto sda.

2. I had to erase Ubuntu, and add like a 3gb partition to sda with the ubuntu installation disc partitioner so Windows could have it's space that it wanted. I installed windows first and it installed to sdb nicely and added the files it wanted to add to the 3gb partition of sda, and then I installed Ubuntu and it installed next to Windows perfectly. I logged into Ubuntu and installed the updates and changed the display( resolution?) to what I wanted and restarted the computer. When I got to the log-in screen and entered my password, the ubuntu loading screen would flicker and then send me back to the log-in screen.

3. I erased both OS's and just installed Ubuntu, and after many trial and errors, I found out the problem in Ubuntu was the display, NOT windows, as I thought was the problem. After every fresh installation of Ubuntu I would go to System > Preference > Display and change it to what would fit my monitor nicely. After I would restart the computer I would get the same flickering screen which I wouldn't get if I didn't change the display and ubuntu would go back to the log-in screen thus a never ending circle. So now I don't touch the Display settings and endure the tiny resolution. PROBLEM SOLVED!!! :)

4. Oh yeah, and the best way to install Ubuntu onto two HDD's as celticbhoy and loui said is to install Ubuntu onto the smaller HDD (sdb, 20 GB) and make the mount point of sdb /(slash)(format everything ext4). Don't forget to add the swap partition to sdb. Format the larger HDD, sda, as ext4 and make the mount point of sda /home. /home does not need a swap partition. All of this is done at the advanced partitioner of the installation disc. I hope this log helps someone and didn't waste too much of their time. :)


P.S
At the log-in screen, I could log-in to an xterm session, but not a GNOME session.

---

