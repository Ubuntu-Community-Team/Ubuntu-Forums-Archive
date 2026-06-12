---
title: "installation"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by yogibaba on 2010-10-18
Hi,

I have installed ubuntu with the below partition 
root-100gb
home-20gb
swap-10gb

As per my understanding the new installations and progams should go to the root folder. I am unable to find where my applications are getting installed and home directory is running out of memory. 

Any help and suggestions..!!!

---

### Post by papibe on 2010-10-18
I would recommend shrinking the / to 10-20 Gb, very rarely you need more than that. Also the swap (although arguably) should match your RAM. And then all the rest to /home (for your pics, movies, etc).

Regards.

---

### Post by cariboo on 2010-10-18
100Gb for root, is way to much, I normally setup a 10Gb partition for / (root), the same amount as ram+100Mb for swap, usually 2.1Gb and the rest of the disk for /home.

All the programs you install from the repositories go into /, the executables are in /usr/bin, while the libraries and documentation also end up in /usr. 

I use /home for two user directories, all downloaded files, music and pictures end up in them.

---

### Post by tajiknomi on 2010-10-18
[SIZE=2][I]100Gb is quite **big** for Root, Moreover your Swap Partition is also too much.......

Normally **/home** is used for Picx,Download,Documents etc..
[/I][/SIZE]

---

