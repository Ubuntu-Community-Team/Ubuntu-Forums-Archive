---
title: "mount point doesnot exist"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by nns2006 on 2011-05-13
Hello,

I am trying to mount the .iso file of MATLAB to the /media/cdromo accroding to the instruction given by "JustMeMyself" [here]("http://thepiratebay.org/torrent/5272375/Mathworks.Matlab.R2009b.UNIX.ISO-TBE_(Mac_OS_X__Linux__Solaris)")

This the output I am getting while trying to mount it.
```
nityanand@nityanand-Vostro-1500:/media/984C083C4C0817A0/software/Ubuntu/Mathworks.Matlab.R2009b.UNIX.ISO-TBE$ sudo mount matu2k9b.iso /media/cdrom0
```
```
mount: mount point /media/cdrom0 does not exist

```

What is the problem? any help will be good.

---

### Post by TeoBigusGeekus on 2011-05-13
Your cd rom mount point is probably named something else.
That's not a problem as you can create a new mount point for it
```
sudo mkdir /media/isomountpoint
```
and then mount your image
```
sudo mount -o loop matu2k9b.iso /media/isomountpoint
```
After you're done with the iso, don't forget to delete the folder,
```
sudo rm -r /media/isomountpoint
```
you don't need it any longer.

---

### Post by nns2006 on 2011-05-13
Thank you very much TeoBigusGeekus . I am installing it now.

---

