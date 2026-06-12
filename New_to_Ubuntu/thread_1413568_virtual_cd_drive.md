---
title: "virtual cd drive"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by degarb on 2010-02-22
Again, in windows, there are program for a virtual cd drive that mounts an iso.

Is there such a program for ubuntu?

---

### Post by sandyd on 2010-02-22
acetoneiso

---

### Post by degarb on 2010-02-22
> **carlee said:**
> acetoneiso
not in my repository.  spelling correct?

---

### Post by k3rnelmustard on 2010-02-22
you do NOT need a special program for this, this is built-in to the OS.  Try out something like

sudo mount -o loop,ro /path/to/iso /media/myMountedIso

---

### Post by ajgreeny on 2010-02-22
Just double click on it to unpack it in archive manager (file-roller) or mount it as shown in above post.

---

### Post by bodhi.zazen on 2010-02-22
Personally I user mount -o loop

If you want a graphical tool:

[http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html](http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html)

[http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html](http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html)

---

### Post by mkvnmtr on 2010-02-22
gISOmount is easy to use if you dont want to look up the command every time you need to use it.

---

### Post by MadCatmkII on 2010-02-23
AcetoneISO was pretty easy to use when I tested it in my previous install (a couple of weeks ago). But Now it seems to have disappeared from the repositories? Does anyone know why?

---

### Post by degarb on 2010-02-23
> **mkvnmtr said:**
> gISOmount is easy to use if you dont want to look up the command every time you need to use it.


I like gisomount since I don't see easy mnemonic for the command line and won't remember months from now. 

But now for second question,  how to create an iso in linux.  I know in winders, but what program or command is used to create an iso image?

---

### Post by LatinHacker on 2010-03-08
> **bodhi.zazen said:**
> Personally I user mount -o loop

If you want a graphical tool:

[http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html](http://www.ubuntugeek.com/furius-iso-mount-mount-and-unmount-iso-images-with-gui-tool-in-ubuntu-linux.html)

[http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html](http://www.ubuntugeek.com/mount-and-unmount-isomdfnrg-images-using-acetoneiso-gui-tool.html)

I cannot remember the full iso -o loop command I used tu use on fedora, and fedoraforums its been close, do you know the whole command?

---

### Post by bodhi.zazen on 2010-03-08
> **LatinHacker said:**
> I cannot remember the full iso -o loop command I used tu use on fedora, and fedoraforums its been close, do you know the whole command?

Assume your .iso is in ~/Desktop and you want to mount it as /media/iso :

```
sudo mkdir /media/iso
sudo mount -o loop -t iso9660 ~user/Desktop/your.iso /media/iso
```

Change ~user to you user name.

Adjust mount point (/media.iso), location of .iso, and user name as needed.

---

### Post by LatinHacker on 2010-03-08
> **bodhi.zazen said:**
> Assume your .iso is in ~/Desktop and you want to mount it as /media/iso :

```
sudo mkdir /media/iso
sudo mount -o loop -t iso9660 ~user/Desktop/your.iso /media/iso
```Change ~user to you user name.

Adjust mount point (/media.iso), location of .iso, and user name as needed.

Thank you very much!!!:KS

---

