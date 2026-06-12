---
title: "encrypted drive with Preboot Authentication (possible on Linux?)"
date: 2011-03-04
forum: New to Ubuntu
---

### Post by nrundy on 2011-03-04
TrueCrypt offers this function for Windows installs. But I've read in several places that preboot authentication is not possible on Linux. Is this because there is no software that does what TrueCrypt can do on Windows? Have I read "bad" information?

---

### Post by davidmohammed on 2011-03-04
Not aware of the possibility - but why would you want to?

You can encrypt almost all of the hard-drive - there isn't really any point to encrypt /boot anyway - [grub]("http://stackoverflow.com/questions/4179365/linux-boot-loaders-supporting-full-disk-encryption") needs this to boot linux.

---

### Post by stoogiebuncho on 2011-03-04
Ubuntu offers full disk encryption if you install through the alternate CD.  Though /boot is not encrypted of course.

Most BIOS settings have the option to set a password - if you do the full disk encryption and then set a bios password I imagine you'd have your bases covered.

---

### Post by nrundy on 2011-03-04
I'm trying to gain a better understanding of this.

Does TrueCrypt encrypt the "/boot" on Windows? 

My understanding of "Preboot Authentication" is that before the OS is allowed to boot on the HDD a password must be entered.  For example, on Windows, I press power, then a BIOS prompt appears. If I do not respond to the BIOS prompt, then the TrueCrypt password prompt appears. Without the password, the comp won't boot to Windows. (This, as i understand it, is preboot authentication).

Does the whole disk encryption from the Alternate CD work like this for Ubuntu?

---

### Post by davidmohammed on 2011-03-04
grub boots using the kernel in /boot.  At that point you are prompted for the password.

In many ways true-crypt is similar - the master boot record (similar to grub) runs true-crypt (aka /boot).  This asks for your password and then runs the rest of windows.

If you really want a true encryption then you'll need a hardware encryption like "Eclypt" - this alters your bios to recognise a hard-drive that has inbuilt encryption.

---

### Post by nrundy on 2011-03-04
Thanks for this info.

When people talk about encrypting the whole disk and creating 3 partitions - one each for Root, Home, and Swap. What is the reason for this? Why not just create 1 partition and put all three on that single partition?

Do home users ever use things like Eclypt? Or is this mainly government, private security equipment? Do consumers buy computers with Eclypt from Dell and Lenovo :) ?

---

### Post by davidmohammed on 2011-03-04
partitioning is a unix concept that linux inherited.  You can quite happily run with one partition that has / /home and /boot etc in that one partition.

Some argue that having a separate /home make backup and recovery a lot easier.

You are correct - Eclypt is mainly for government and where you need to hold restricted and confidential information.  In the UK you are liable to prison and fines for losing laptops containing such data if you havent made adequate protection mechanisms - encryption, locking the laptop away etc.

Eclypts are special hard-drives you buy to replace existing hard-drives from Dell etc.

---

### Post by nrundy on 2011-03-04
Thx david :)

What do you do encryption wise? Do you do a whole disk or just containers or none?  I'm trying to decide whether I should encrypt everything--the thing I like about it is that I get a password prompt right at boot and then I'm done (no more passwords. I like this better than waiting for the typical login prompt).

PS: I read that encrypting the /Home directory is useless because someone can just boot into Recovery and see everything? Is this true? Why is encryption for the /Home folder even offered if this is true? Is there a way to prevent this?

---

### Post by stoogiebuncho on 2011-03-04
> **nrundy said:**
> Thanks for this info.

When people talk about encrypting the whole disk and creating 3 partitions - one each for Root, Home, and Swap. What is the reason for this? Why not just create 1 partition and put all three on that single partition?

Do home users ever use things like Eclypt? Or is this mainly government, private security equipment? Do consumers buy computers with Eclypt from Dell and Lenovo :) ?

David is correct in what he said, but I'd just add that Swap needs to be on it's own partition in order to work.  Everything else can be on one partition if you want it to be, though.

---

### Post by davidmohammed on 2011-03-05
> **nrundy said:**
> Thx david :)

What do you do encryption wise? Do you do a whole disk or just containers or none?  I'm trying to decide whether I should encrypt everything--the thing I like about it is that I get a password prompt right at boot and then I'm done (no more passwords. I like this better than waiting for the typical login prompt).

PS: I read that encrypting the /Home directory is useless because someone can just boot into Recovery and see everything? Is this true? Why is encryption for the /Home folder even offered if this is true? Is there a way to prevent this?

I dont have any laptops/netbooks etc with restricted/confidential data - only passwords I worry about - I use Keepass for that - access to that is password protected using its encryption stuff.  The stuff I use for work though is all encrypted - I use a combination of hardware encryption and software encryption like truecrypt.   I would be interested in the link where you say you can boot into recovery mode to see the encrypted /home - I dont believe thats true.  You certainly can boot into recovery to mount /home - the contents though would be garbage without the encryption key.

---

### Post by smssms on 2012-07-18
If anyone has installed Ubuntu on an eclypt internal HDD and want to tell me about it, drop me a line; I'm struggling...

> **ECLYPT_Encryption said:**
> 
 
We have several customers who protect their linux operating systems, both with government and personal data - we make two types.
 

---

### Post by NikTh on 2012-07-18
Hi , 
did you read this ? [http://ubuntuforums.org/showthread.php?t=1369019](http://ubuntuforums.org/showthread.php?t=1369019)
perhaps serve your needs .. i don't know.

---

### Post by kurt18947 on 2012-07-18
> **stoogiebuncho said:**
> David is correct in what he said, but I'd just add that Swap needs to be on it's own partition in order to work.  Everything else can be on one partition if you want it to be, though.

Swap needs its own partition only if one wants to enable suspend-to-disk aka hibernation.  If you just want to suspend-to-ram, you can create a swap *file*.  The advantage of a swap file is it doesn't require one of four allowed primary partitions.

---

### Post by Elfy on 2012-07-18
> **smssms said:**
> If anyone has installed Ubuntu on an eclypt internal HDD and want to tell me about it, drop me a line; I'm struggling...

Please start your own thread - this one is old and closed.

---

