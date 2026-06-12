---
title: "Can't mount iso"
date: 2010-05-27
forum: New to Ubuntu
---

### Post by GonchuB on 2010-05-27
I'm having a problem when trying to mount a .iso file.
I tried the command "sudo mount -o loop image.iso /mnt/"
but a message shows saying: "image.iso: there is no such file or directory"
Please help, really need to mount the .iso.

---

### Post by TheStroj on 2010-05-27
The error message you got, means there is no file named 'image.iso' in the current directory. Navigate to the directory that has it and use this command again.

---

### Post by GonchuB on 2010-05-27
What do you mean with current directory. The .iso file is in my downloads folder.

---

### Post by bodhi.zazen on 2010-05-27
Open a terminal.

Either cd (change directory) into downoalds:

```
cd ~/Downloads
```

Or use the full path and name of the .iso

```
mount -o loop -t iso9660 /home/user/Downloads/name_of.iso /mnt
```

See :

[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

You may want to make a directory to mount that at

```
sudo mkdir /mnt/iso
```

Then use /mnt/iso as your mount point.

See: [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?&t=283131")

---

