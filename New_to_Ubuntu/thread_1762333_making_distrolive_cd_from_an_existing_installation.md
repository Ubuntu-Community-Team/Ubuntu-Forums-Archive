---
title: "making distro/live cd from an existing installation"
date: 2011-05-19
forum: New to Ubuntu
---

### Post by vkbidve on 2011-05-19
Hi,

I have ubuntu 10.04 LTS installed on my laptop with some other applications. I want to make a live CD/Setup CD from that installation and use it to install on another PC so that entire linux setup plus other apps also get set up on that pc. 

Can I make (or how to make) such a distro package from existing installation?

---

### Post by Plueonic on 2011-05-19
See [http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)

---

### Post by jre6 on 2011-05-19
Remastersys can help you with this. To install it, type the following in a terminal:
```

sudo gedit /etc/apt/sources.list

```
Add the following line at the end:
```

 deb http://www.geekconnection.org/remastersys/repository karmic/

```
Then open Synaptic and click reload, and finally type this in a terminal:
```

sudo apt-get install remastersys

```To make your own distro, type this in a terminal:
```

sudo remastersys dist

```Make sure that you have lots of disk space to spare (>15 GB).

---

### Post by vkbidve on 2011-05-19
Thanks jre6 and Plueonic!
:D
I am going to try this today itself and post my experience subsequently.....
:D

---

### Post by vkbidve on 2011-05-24
I tried the remastersys thing... and its great!

the iso image was burnt into a dvd and its working just gr8!

Now, I wnat to remove the iso file and other stuff created by remastersys as its intermediate/final output, as it is costing more than 4 GBs on my disk. But i am not able to delete them. I also tried the forums on remastersys for that, but couldn't get through.

So can u tell me how to remove those folders?

---

### Post by tea for one on 2011-05-24
> **vkbidve said:**
> I tried the remastersys thing... and its great!

the iso image was burnt into a dvd and its working just gr8!

Now, I wnat to remove the iso file and other stuff created by remastersys as its intermediate/final output, as it is costing more than 4 GBs on my disk. But i am not able to delete them. I also tried the forums on remastersys for that, but couldn't get through.

So can u tell me how to remove those folders?

Good morning

Open Remastersys
Select "Clean" (which removes the temporary files)

---

### Post by vkbidve on 2011-05-24
Oh.......... I overlooked that option in remastersys.!

Thanks a lot!

Now i am marking thread as 'solved'.

---

