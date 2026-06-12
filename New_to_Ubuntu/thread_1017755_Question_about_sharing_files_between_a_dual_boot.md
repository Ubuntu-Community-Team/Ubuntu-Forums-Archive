---
title: "Question about sharing files between a dual boot"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by dai_vernon on 2008-12-21
So, I am installing Intrepid onto a machine with Windows currently on it, and I have a question about the partition setup.  Would the optimal idea be to, out of the space not being used by Windows, create two partitions for linux, one moderately sized one for / and a larger one for /home that will be shared by both systems?

---

### Post by mikeyphi on 2008-12-21
> **dai_vernon said:**
> So, I am installing Intrepid onto a machine with Windows currently on it, and I have a question about the partition setup.  Would the optimal idea be to, out of the space not being used by Windows, create two partitions for linux, one moderately sized one for / and a larger one for /home that will be shared by both systems?

Here's an excellent guide:   [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by gTinker on 2008-12-21
You probably want to also consider a swap partition.

---

### Post by zvacet on 2008-12-21
@ **dai_vernon**

It is O.K. to have separate home and that is what I suggest you to do.But if you want to share files between OS I think it is good idea to make one NTFS partition,because it look like in Itrepid [fs-driver]("http://www.fs-driver.org/") doesn´t work anymore.

---

### Post by dai_vernon on 2008-12-21
Well yeah, I just didn't mention the swap partition; that's a given.

---

### Post by dai_vernon on 2008-12-21
> **zvacet said:**
> @ **dai_vernon**

It is O.K. to have separate home and that is what I suggest you to do.But if you want to share files between OS I think it is good idea to make one NTFS partition,because it look like in Itrepid [fs-driver]("http://www.fs-driver.org/") doesn´t work anymore.
I have heard that it is good to separate /home and / because you can then reinstall the OS without wiping home.  Is this not true?

---

### Post by arckeda on 2008-12-21
I usually just move files around via partitions.

---

### Post by dai_vernon on 2008-12-21
> **zvacet said:**
> @ **dai_vernon**

It is O.K. to have separate home and that is what I suggest you to do.But if you want to share files between OS I think it is good idea to make one NTFS partition,because it look like in Itrepid [fs-driver]("http://www.fs-driver.org/") doesn´t work anymore.
I was planning on having the entire Ubuntu section (with the exception of the swap of course) in NTFS format.  This is what you are suggesting, right?

---

### Post by gTinker on 2008-12-21
> **dai_vernon said:**
> I was planning on having the entire Ubuntu section (with the exception of the swap of course) in NTFS format.  This is what you are suggesting, right?

That's not how I read what was written.

I suggest you use a native Linux filesystem for the Linux partitions.

---

### Post by Captain_tux on 2008-12-21
Hardy and Intrepid can read NTFS partitions just fine. However, using NTFS on which to load Ubuntu is a **very** bad idea.

---

### Post by handydan918 on 2008-12-21
> **Captain_tux said:**
> Hardy and Intrepid can read NTFS partitions just fine. However, using NTFS on which to load Ubuntu is a **very** bad idea.

+1

NTFS == NeanderThal File System

---

### Post by zvacet on 2008-12-21
@ **dai_vernon**

> I was planning on having the entire Ubuntu section (with the exception of the swap of course) in NTFS format. This is what you are suggesting, right?

Not it is not.I suggest you to format shared partition as NTFS,because Ubutu can read it (and Windows of course ;) ).Native Ubuntu format is ext3,and yes you need swap.

---

