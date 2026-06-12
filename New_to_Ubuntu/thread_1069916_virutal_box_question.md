---
title: "virutal box question"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by metzy85 on 2009-02-14
Hi i have a question about virtual box. I am wanting to make a virtual box for windows xp. My Linux partition is 34gb and i am using 4gb and i made a virtual hard drive that is 20gb and when i go to install xp it says it does not have enough space and the disk is full what am i doing wrong??

---

### Post by hyperyoda on 2009-02-14
> **metzy85 said:**
> Hi i have a question about virtual box. I am wanting to make a virtual box for windows xp. My Linux partition is 34gb and i am using 4gb and i made a virtual hard drive that is 20gb and when i go to install xp it says it does not have enough space and the disk is full what am i doing wrong??

Create a dynamic VDI of 30 GB and then allocate 256 MB or more (even 512 MB) to the VM. Next you can install XP. When XP's setup program asks how you want to partition the disk make sure you tell it to allocate the entire disk as one partition.

Here is an excellent step-by-step guide:
[http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/](http://www.blog.arun-prabha.com/2007/05/07/installing-virtualbox-and-windows-using-virtualbox-in-ubuntu/)

Zach

---

