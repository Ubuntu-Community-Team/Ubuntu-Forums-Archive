---
title: "Sorry, another dual boot thread/partition sizes"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by miss_fugg on 2009-03-27
Hi guys,

I currently have an old laptop and wish to dual boot Windows XP Pro and Ubuntu.

Here are a few details:

* I have a 120GB hard disk, which is new and has nothing on it
* I have 512MB of RAM installed
* I will be mainly using Windows as my main OS, Ubuntu to test, but I will be leaving it on the hard disk as I have enough space to play with

I'm looking for a recommendation on Ubuntu partition sizes as I am clueless in this department, though I have tried to read up on this.

Thanks in advance,
Jen

---

### Post by WhiskyChris on 2009-03-27
Easiest way to go about this is to install windows first, then install ubuntu specifying how much space to use in total (anything you want really depending how many/what size of programs/data you want to do). It will sort out its own partitions and leave windows with the rest of the disk.

There are of course, many other more detailed and manual methods. I'll leave those for others to explain if you'd like to learn, however I'd point you to this reference for now - [http://www.psychocats.net/ubuntu/partitioning]("http://www.psychocats.net/ubuntu/partitioning")

---

### Post by Paqman on 2009-03-27
> **miss_fugg said:**
> 
I'm looking for a recommendation on Ubuntu partition sizes

Swap size needs to equal your RAM if you want to hibernate. So 512MB will do fine.

As for the rest, if you're planning on putting Ubuntu onto a single partition i'd give it 20GB. It only needs about 6-8GB, but sometimes you want room for big temp files, etc. You can use the Windows partition for data.

---

### Post by Crowd Control on 2009-03-27
I am definitely no expert on this, but I have been reformatting my Ubuntu HDD (physical) for a couple of times now. I do use it as my main OS though.

My File System hasn't exceeded 5 GB yet and my Home Folder has about 250 MB of settings. So that would total roughly 5.5 GB total (clean without music, movies, etc). I don't know if it's representative and I don't know what you plan on running on it, but with a total of 8 GB you should be safe with running the OS for testing.

---

### Post by miss_fugg on 2009-03-27
Thank you very much for the advice guys. Much appreciated.

Jen

---

