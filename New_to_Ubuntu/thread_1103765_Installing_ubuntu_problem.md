---
title: "Installing ubuntu problem"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by zxy on 2009-03-23
So I've installed Ubuntu and got a error, so i tried to remove it but there's one problem.

The laptop I bought from circuit city is a 2008 model but it came with no vista c.d., so how do I do the repair thing.

---

### Post by iaculallad on 2009-03-23
And what problem would that be? Try to be more specific.

---

### Post by lisati on 2009-03-23
If you installed Ubuntu over the top of XP and have no recovery disk, that's probably it, you might have to put it down to experience and have a go at getting Ubuntu working.

Do you know if your computer has a recovery partition?

Some more information about the error you had might also prove useful.

---

### Post by zxy on 2009-03-23
I think so but I cant find it

---

### Post by lisati on 2009-03-23
If you are able to boot from an Ubuntu "Live CD" (installation disk) and choose the "Try Ubuntu without changing your system") the forum members might be able to guide you through the troubleshooting process.
*One thing which would be helpful for us is if you give us more information about the error you experienced*

---

### Post by zxy on 2009-03-23
Ok so when I press f12 to load up boot manager i press tab and i get to system repair, I do it and in a couple of seconds its done but when I restart my laptop the ubuntu and the microsoft vista choice still pop's up.

---

### Post by lisati on 2009-03-23
> **zxy said:**
> Ok so when I press f12 to load up boot manager i press tab and i get to system repair, I do it and in a couple of seconds its done but when I restart my laptop the ubuntu and the microsoft vista choice still pop's up.

<sighs>
It sounds like the recovery partition is unavailable.

How did you get on booting the Live CD (installation disk)? If you were successful, you will be able to go to the command line (it's listed on the Applications->Accessories menu as "Terminal). Please post the output from
```
sudo fdisk -l
```
This will help us figure out what's on your computer's hard disk (including finding a recovery partition, if there is one still there)

---

### Post by blandman3 on 2009-03-23
Can you run windows at all?  

Usually, a recovery partition will be on the drive letter D:\

If you don't have one, that means you will need to create a recovery CD from windows.  Usually, when you buy a new computer, the sales people tell you to create your recovery disks before you do anything to your computer.

:popcorn:

---

### Post by lisati on 2009-03-23
I think zxy has left the building.....

---

### Post by zxy on 2009-03-23
yeah sorry, i had school in the morning so i had to go to sleep

---

### Post by zxy on 2009-03-23
> **lisati said:**
> <sighs>
It sounds like the recovery partition is unavailable.

How did you get on booting the Live CD (installation disk)? If you were successful, you will be able to go to the command line (it's listed on the Applications->Accessories menu as "Terminal). Please post the output from
```
sudo fdisk -l
```
This will help us figure out what's on your computer's hard disk (including finding a recovery partition, if there is one still there)

well i cant boot ubuntu anymore since it comes up as a error and I dont really understand what you mean about Terminal, I go to my accesories folder from start and dont see anything like that.

> **blandman3 said:**
> Can you run windows at all?  

Usually, a recovery partition will be on the drive letter D:\

If you don't have one, that means you will need to create a recovery CD from windows.  Usually, when you buy a new computer, the sales people tell you to create your recovery disks before you do anything to your computer.

:popcorn:

Windows works fine, and i have a c drive but the d drive is my dvd drive. And the sales people didnt tell me anything about recovery disk

---

