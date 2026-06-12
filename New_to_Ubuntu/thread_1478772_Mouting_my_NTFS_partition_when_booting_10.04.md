---
title: "Mouting my NTFS partition when booting 10.04"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by Chlorhydrikk on 2010-05-10
Hello,
I've done some researches about the subject but I really want to be sure about what I am doing because i'm going to edit a core file as root [IMG]http://www.siteduzero.com/Templates/images/smilies/langue.png[/IMG]
So here we go: I have 3 partitions on my laptop, / for ubuntu files, /home for ubuntu documents, and /media for my windows ntfs partition.
The matter is that I put all my files on the windows partition (to be able to access them with both OS) and I have to click on my hard drive to mount it and access my data.
I saw that I had to add the following line to my /etc/fstab :

/dev/sda3  /media/data    ntfs   user,users,ro,exec,auto   0  0

But I have really no idea if this is going to work and if it's going to damage my laptop. I don't know what is my windows partition (I guess it's sda1 as it's the first one on the HDD) and I just can tell you that my HDD is called Kirith Core and that the path seems to be /media.

Thank you for your very appreciated help, :)

Cheers
Llywelyn

---

### Post by Chlorhydrikk on 2010-05-10
Just something I wanted to add: I made a swap partition! (logical)

---

### Post by Matt__ on 2010-05-10
easy mode for automounting  ntfs on boot.
```
sudo apt-get install ntfs-config
```
and yo may also have to 
```
gksudo ntfs-config
```

---

