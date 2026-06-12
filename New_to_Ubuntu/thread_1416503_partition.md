---
title: "/ partition"
date: 2010-02-26
forum: New to Ubuntu
---

### Post by grobar87 on 2010-02-26
Hi! I try to install ubuntu:
120 HD,1 GB Ram,Dual Core 2GHz

What size my /root partiton should be(best size) and what size of swap partiton i need?

---

### Post by Kakers on 2010-02-26
Well this is how I have mine laid out for a 320GB HDD

```

Filesystem              Size  Used  Avail   Use%    Mounted on
/dev/sda1              38G   4.8G   33G     13%     /
/dev/sda3             234G  3.6G  219G      2%     /home

```I'm only using 4.8G for my / you could have yours at about 10G or 20G if you like. I think it's best to have about 10% of the space for / though.

And for Swap... a quote from the Ubuntu page.

> **Example Scenarios**

 Low RAM and low disk space With 512 MB RAM and 30 GB hard disk, use 512 MB for swap since RAM is very low. 
Low RAM and high disk space With 512 MB RAM and 100 GB hard disk, use 1 GB for swap since RAM is very low and hard disk space is in plenty. 
High RAM and low disk space With 2 GB RAM and 30 GB hard disk, use 1 GB for swap since hard disk space is very low. 
High RAM and high disk space With 2 GB RAM and 100 GB hard disk, use 2 GB for swap since hard disk space is plentiful. 

---

### Post by ibuclaw on 2010-02-26
10GBs is usually recommended.

20GBs if you plan to install quite a few big applications.

```

[~] df
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3              19G  2.9G   15G  17% /
/dev/sda5             124G   25G   94G  21% /home

```

(edit):
Swap should be 1.5x the size of your total System RAM. Unless you have more than 2GB RAM, then a swap size equal to will be sufficient.

Regards
Iain

---

### Post by skymera on 2010-02-26
I have Ubuntu on a 15GB partition with 2GB swap partition.

Though i run a 10GB partition for over 2 years

---

### Post by grobar87 on 2010-02-26
tnx for advice 
:)

---

### Post by nothingspecial on 2010-02-26
I manage fine with 7(ish)
```

df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             6.8G  3.8G  2.7G  58% /
udev                  497M  264K  497M   1% /dev
none                  497M  2.0M  495M   1% /dev/shm
none                  497M  116K  497M   1% /var/run
none                  497M     0  497M   0% /var/lock
none                  497M     0  497M   0% /lib/init/rw
/dev/sda4             131G   31G   93G  25% /home
rob@192.168.2.10:/media/music/
                      459G  425G   11G  98% /home/rob/music
/dev/sda3             7.2G  1.6G  5.2G  24% /media/buntu
```

You can see the amount of space a full install and minimal instal differ by /dev/sda1 is regular old Ubuntu

/dev/sda3 is Ubuntu minimal with openbox, even with firefox, guayadeque and quite a few other apps, it still uses less than half the space.

---

### Post by philinux on 2010-02-26
```
df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              12G  4.2G  6.4G  40% /

```

I've installed quite a few things on top of the base install and as you can see my 12gig root is only 40% used.

---

