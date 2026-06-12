---
title: "Ubuntu Won't Start"
date: 2009-03-17
forum: New to Ubuntu
---

### Post by theolyons on 2009-03-17
Hi, I have been running ubuntu intrepid on my laptop for a few months and have been using it for everything / am glad to have escaped windows.

As of yesterday I have been unable to boot it up. While Ubuntu is loading I get taken to a text screen with the message:

/dev/sda1 contains a file system with errors.

the file system check won't run because there is an "error reading block 230875"

I really really need to get my files off the computer (I am currently running ubuntu in trial mode off the boot disk, but cannot access my documents). Is there a way to reinstall without losing everything? Thanks

---

### Post by taurus on 2009-03-17
Maybe you need to run fsck your root filesystem, /dev/sda1 from the LiveCD.

```
sudo fsck /dev/sda1
```
Otherwise, mount it first before you can access it.

```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/sda1 /media/ubuntu
df -h
```

---

