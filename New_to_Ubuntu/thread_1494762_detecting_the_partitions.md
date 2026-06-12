---
title: "detecting the partitions"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by 1991sudarshan on 2010-05-27
i have installed the ubuntu nad the kubuntu in the partitions in sda7 and sda6 respectively! but my windows xp is not detecting the the linux partitions! pls help:confused:

---

### Post by Ozymandias_117 on 2010-05-27
Windows can't read ext partitions by default. You can try [http://www.fs-driver.org/]("http://www.fs-driver.org/") But I'm not certain if it works with ext 4

---

### Post by egalvan on 2010-05-27
> **Ozymandias_117 said:**
> You can try [http://www.fs-driver.org/]("http://www.fs-driver.org/") But I'm not certain if it works with ext 4

The bigger problem is that it does not support "large i-nodes", which are used by default in Linux these days.

It's possible to re-format all your Linux file-systems to use small i-nodes, but this is too much of a hassle for me.
(although I did this to my main download storage drive (and it's backup to maintain Windows compatibility))

I supported this project with $$ while using it in '08 & '09, but it's fallen too far behind.
It hasn't been updated in some 18 months.
Sad; it was a good piece of work.

There is another project out there that does work with large i-nodes, but I don't recall the link at this moment.

**EDIT** OK, here is that link...

[http://www.ext2fsd.com/](http://www.ext2fsd.com/)

---

### Post by 1991sudarshan on 2010-05-27
i downloaded the ext2 detector and it successfully detected the linux partitions but when i tried to open the partitions it is asking me to format the entire disk!!:confused:

---

### Post by 1991sudarshan on 2010-05-27
i think i chose the jfs file system option while installing the linux!!!

---

### Post by egalvan on 2010-05-27
> **1991sudarshan said:**
> ...when i tried to open the partitions **it is asking me to format the entire disk!**!:confused:

Again, I don't use extfsd... 

but under fs-driver, that message is saying that the file-system is not detected.
It's probably the same thing under extfsd.

---

### Post by varunendra on 2010-05-27
> **1991sudarshan said:**
> i have installed the ubuntu nad the kubuntu in the partitions in sda7 and sda6 respectively! but my windows xp is not detecting the the linux partitions! pls help:confused:

What is it that you want to accomplish?
I'm sure you don't want to access linux system files from windows.
To access data files (that you created, downloaded or copied), just save them on a windows partition (Fat/Fat32 or ntfs) rather than your default Home directory.

---

