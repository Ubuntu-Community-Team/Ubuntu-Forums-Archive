---
title: "restting permissions"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by rivkinnator on 2009-04-27
i have a hard drive that the permissions are all out o fwhack from my last install and now i cant acces any thing and i dont know how to remove the permissions i know that i might need to use chmod but have no idea how to use it. i need help and i idont know what the file system format was it that effects anything i think it was ext2

---

### Post by powerpleb on 2009-04-27
It depends on who you want it to belong to.

This transfers ownership of the directory and its contents to the user and group specified
```
sudo chown user:group -Rv /dir
```

This gives read/write/execute permissions of directory and all contents to the owner, read/execute permissions to everyone else.
```
sudo chmod 755 -Rv /dir
```

This may also help:
[http://catcode.com/teachmod/](http://catcode.com/teachmod/)

---

### Post by rivkinnator on 2009-04-27
i tried this to the dir o fthe hard drive but it didnt do it to all the directories below it and i dont know how to path to lower dir's i knwo /dev/sda2 is my device

---

### Post by powerpleb on 2009-04-27
Don't use /dev/sda2 for commands like that, you need to run the command on the directory the drive is *mounted* to. To find this out run:
```
mount | grep /dev/sda2
```

It will show up with something like this:
```
/dev/sda2 on **/media/hard_disk** type ext3 (rw,relatime,errors=remount-ro)

```
The bold part will obviously be different as it is the path your drive is mounted to. 

If nothing shows up then its not mounted and you will need to mount it, [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux) <--this page will help you do that.

Once you know where it is mounted you can run chmod.
```
sudo chmod 755 -Rv **/media/hard_disk**
```

Hope that helps. :)

---

### Post by rivkinnator on 2009-04-28
it comes up with many errors that are a;ll the smae and it reads " read only file system"

---

### Post by powerpleb on 2009-04-28
It might be mounting as read only. Could you post the contents of /etc/fstab here?

Also, you could try remounting with read/write permissions:
```
sudo mount -o remount,rw /dev/sda2 /mnt/hard_disk
```
Remember to change /mnt/hard_disk to your regular mount point.

---

