---
title: "Accessing an external hard drive from command line"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by alfa_80 on 2011-08-14
Hi,

I need to backup my data from ubuntu 10.04 system to an external hard drive, however, when I navigate to /media, there is no such an external hard drive. How do I access is via command line for I am on console..I have to back up my data before reinstalling my ubuntu..BTW, I am just a beginner in ubuntu and on the internet there're a lot of guide which are quite advance to me..

Can anybody guide me on this..

Thanks in advance.

---

### Post by elgordodude on 2011-08-14
Did you mount the drive? If you open the drive and then navigate to media it should appear.

---

### Post by alfa_80 on 2011-08-14
> **elgordodude said:**
> Did you mount the drive? If you open the drive and then navigate to media it should appear.

How to mount the drive? 

Thanks..

---

### Post by spiky001 on 2011-08-14
1st you need output of ```
sudo fdisk -l 
```Then make dir in media called harddrive

```
sudo mount /dev/sdb /media/harddrive
```sdb is the result of fdisk on my machine

---

### Post by elgordodude on 2011-08-14
Just click places and click the drive

For example, if do 
```

gordo@gordohome:~$ cd /media
gordo@gordohome:/media$ ls

```

I get:

1654-9594  floppy  floppy0

But wait, I know I also have a 1.5 TB hard drive for backups, wheres that? Since I haven't used it the computer hasn't mounted it even though it knows its there. So I click on places, click on the drive, try the list command again and get:

1.5 TB    1654-9594  floppy  floppy0

There it is. If for some reason it's not in /media you can get there in command line by typing cd and draging the folder into the terminal.

---

### Post by AlphaLexman on 2011-08-14
Modern versions of ubuntu (> 7.04) should auto-mount any usb drive without going through mount procedures. Can you find the drive with Nautilus??

If so, click the 'up' button on the toolbar, and then right-click the drive and click properties.. what does it say at 'Location:' ??

---

### Post by alfa_80 on 2011-08-14
> **spiky001 said:**
> 1st you need output of ```
sudo fdisk -l 
```Then make dir in media called harddrive

```
sudo mount /dev/sdb /media/harddrive
```sdb is the result of fdisk on my machine

This is on the right track, because it is similar to this link [https://help.ubuntu.com/community/Mount/USB](https://help.ubuntu.com/community/Mount/USB)

Now, it successfully mounted but I was using ```
sudo mount -t vfat /dev/sdb1 /media/external -o uid=1000,gid=1000,utf8,dmask=027,fmask=137
```

found from the link. However, I receive a lot of error messages saying "cp:cannot create symbolic link..bla2..:operation not permitted..

Any idea?

---

### Post by spiky001 on 2011-08-14
try sudo cp

---

### Post by alfa_80 on 2011-08-14
> **spiky001 said:**
> try sudo cp

The output is with SUDO already..

---

### Post by spiky001 on 2011-08-14
can you cd into harddrive ```
cd /media/external
```
I take it you read the troubleshoot down the bottom of your link

---

### Post by alfa_80 on 2011-08-14
> **spiky001 said:**
> can you cd into harddrive ```
cd /media/external
```
I take it you read the troubleshoot down the bottom of your link

Yes, I can "cd" into the hard drive and access the contents..

---

