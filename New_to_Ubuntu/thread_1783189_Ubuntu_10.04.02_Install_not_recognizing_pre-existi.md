---
title: "Ubuntu 10.04.02 Install not recognizing pre-existing partitions on primary drive"
date: 2011-06-15
forum: New to Ubuntu
---

### Post by venom104 on 2011-06-15
I'm trying to install Ubuntu 10.04.02 on my hard drive and replace an older version of ubuntu on it that I am having problems with. Whenever I try and install the new version at the partition screen none of my other partitions are viewable! The weird thing here is that if I do an sudo fdisk -l I can actually SEE all the partitions (including my windows and ubuntu partitions). 

What can I do? My old version of ubuntu is damaged and I can't repair it (I've tried).


Here is a picture of what I am talking about.

[http://s1125.photobucket.com/albums/l594/venom104/?action=view&current=problem.png](http://s1125.photobucket.com/albums/l594/venom104/?action=view&current=problem.png)

---

### Post by venom104 on 2011-06-15
> **venom104 said:**
> I'm trying to install Ubuntu 10.04.02 on my hard drive and replace an older version of ubuntu on it that I am having problems with. Whenever I try and install the new version at the partition screen none of my other partitions are viewable! The weird thing here is that if I do an sudo fdisk -l I can actually SEE all the partitions (including my windows and ubuntu partitions). 

What can I do? My old version of ubuntu is damaged and I can't repair it (I've tried).


Here is a picture of what I am talking about.

[http://s1125.photobucket.com/albums/l594/venom104/?action=view&current=problem.png](http://s1125.photobucket.com/albums/l594/venom104/?action=view&current=problem.png)


I looked on the Internet on what to do, and while most of the information is unhelpful...most of the posts there qoute output from parted, here is mine


ubuntu@ubuntu:~$ sudo parted /dev/sda print
Error: Can't have overlapping partitions.

---

### Post by ppv on 2011-06-15
If you have backed up all the data from the existing hard disk or do not want any data from it and just want a fresh install, you can boot from a live CD and delete all the partitions and then install Ubuntu.

---

### Post by themusicalduck on 2011-06-15
Open a terminal and run this command -

```
sudo apt-get remove dmraid
```

Then run the installer again and see if it can see the drives.

---

### Post by venom104 on 2011-06-15
> **themusicalduck said:**
> Open a terminal and run this command -

```
sudo apt-get remove dmraid
```Then run the installer again and see if it can see the drives.

No difference at all

---

### Post by venom104 on 2011-06-15
> **ppv said:**
> If you have backed up all the data from the existing hard disk or do not want any data from it and just want a fresh install, you can boot from a live CD and delete all the partitions and then install Ubuntu.


I can't delete all the partitions; I can't lose all the data I have and I don't have the means to back up all my data.

---

### Post by ppv on 2011-06-15
ok...so you already have a Ubuntu system running and you want to install a newer version since the older one is damaged. And how are you trying to install using a live CD?

---

### Post by venom104 on 2011-06-15
> **ppv said:**
> ok...so you already have a Ubuntu system running and you want to install a newer version since the older one is damaged. And how are you trying to install using a live CD?


I don't understand the question, yes I'm trying to install using a Live CD. I'm using the install program that comes on the cd, if that's what you mean.

---

### Post by venom104 on 2011-06-15
I solved this problem by downloading fixparts ([http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)) running the tool and simply saving the results. It was done almost automatically. 


Thank you to those who have helped

---

