---
title: "Op System Selection - What does all this mean ?"
date: 2010-01-25
forum: New to Ubuntu
---

### Post by ericstrom on 2010-01-25
I have a few questions about what I'm seeing when I boot up and get to the operating system selection page. First a little background:

Dual booting Ubuntu with Windows XP
Very small hard drive ...so I want to keep anything that's not needed off
Recently switched back to 9.04 from 9.10 b/c I didn't like how 9.10 ran.

Here's what I see when I get to my Operating Sys selection:

Operating System Selection

Ubuntu 9.04 Kernel 2.6.28-17 – generic
Ubuntu 9.04 Kernel 2.6.28-17 – generic (recovery mode)
Ubuntu 9.04 Kernel 2.6.28-11 – generic
Ubuntu 9.04 Kernel 2.6.28-11 – generic (recovery mode)
Ubuntu 9.04 memtest 86+

Other Operating Systems

Microsoft Windows XP Home Addition

Ubuntu 9.10 Kernel 2.6.31-18 – generic (on/dev/sda 5)
Ubuntu 9.10 Kernel 2.6.31-18 – generic (recovery mode) (on/dev/sda 5)
Ubuntu 9.10 Kernel 2.6.31-17 – generic (on/dev/sda 5)
Ubuntu 9.10 Kernel 2.6.31-17 – generic (recovery mode) (on/dev/sda 5)
Ubuntu 9.10 Kernel 2.6.31-16 – generic (on/dev/sda 5)

So here are my questions:

Why do I see 4 instances of 9.04, is that normal, & are they all needed ?

What is 9.04 memtest 86+ and is that needed ?

Why do I see 5 instances of 9.10, is that normal, & are they all needed ?

What is sda 5 ? I also see that I have an sdb.

Would getting rid of 9.10 stuff free up some hard drive space ?

What's the best way to get rid of the 9.10 stuff assuming it will free up space ? I have the 9.04 disc.

---

### Post by amaroKer on 2010-01-25
1 and 3: All the different iterations of the same operating system are just kernel versions that were acquired through updates.  The update makes an entry in /boot/grub/menu.lst to reflect the new kernel version, but keeps the old one there in case you run into problems.  You can edit that file to make it show what you want to see.

2: Memtest is a memory test that you can run, I don't know much about it.

4: /dev/sda5 is the partition numbered 5 that 9.10 is installed on.  Your XP is probably on sda1, and you may have an extended partition sda2 that holds the rest (3-5 or 6) depending on how you set it up.  sdb is going to be another device, probably an external drive or usb thumb stick and will contain sdb1.  Your sda5 will be on your sda device.

5: Yes

6: Install gparted or GNOME partition editor.  Find /dev/sda5 and delete it.  Then resize your partition adjacent (your linux / partition or /home if you have one) to take up that space (back up important data first).  Some partition setups get pretty creative and if you need help, show us the output of **sudo fdisk -l**

---

### Post by Thomas Garman on 2010-01-25
I had the same problem, which is really simple to solve: go into synaptic and put 2.6.31 -15 or -16 or -14 or whatever in the search box and you will see all of the different versions listed there.  You can tick/select/mark all of the versions you want to completely remove and they will be completely removed and then stop showing up.

In the GRUB2 tutorial you will also find an easy explanation of how to get those memtest lines to stop showing up on GRUB screen.

---

### Post by ericstrom on 2010-01-25
Would I free up some hard drive space if I got rid of all the 9.10 instances ? And if so, how would I go about doing that ?

---

### Post by Diametric on 2010-01-25
> **Thomas Garman said:**
> I had the same problem, which is really simple to solve: go into synaptic and put 2.6.31 -15 or -16 or -14 or whatever in the search box and you will see all of the different versions listed there. You can tick/select/mark all of the versions you want to completely remove and they will be completely removed and then stop showing up.
 
In the GRUB2 tutorial you will also find an easy explanation of how to get those memtest lines to stop showing up on GRUB screen.
 
Should he be carefull of dependencies issues here?  Not sure if that is true for kernals, but wanted to post before he deletes an older one and some app has a dependencie on it...

---

### Post by king EZi on 2010-01-25
I would recommend you download ubuntu tweak from [here]("http://ubuntu-tweak.com/"), this will clean up your system "safely than you manually deleting stuff, unless you are sure of what you are doing.

---

### Post by kansasnoob on 2010-01-26
> Why do I see 4 instances of 9.04, is that normal, & are they all needed ?

What is 9.04 memtest 86+ and is that needed ?

Install Startup Manager:

```
sudo apt-get install startupmanager
```

You'll then find it in System > Administration and if you click on the Advanced tab you can untick the option for displaying the Memtest, and also limit the number of kernels shown (I recommend 2). I'd also leave the Recovery Mode option ticked because it can be very useful.

> Why do I see 5 instances of 9.10, is that normal, & are they all needed ?

What is sda 5 ? I also see that I have an sdb.

Would getting rid of 9.10 stuff free up some hard drive space ?

What's the best way to get rid of the 9.10 stuff assuming it will free up space ?

Have you already removed 9.10?

Post the output of:

```
sudo parted /dev/sda print
```

Or better yet a screenshot of Gparted.

---

