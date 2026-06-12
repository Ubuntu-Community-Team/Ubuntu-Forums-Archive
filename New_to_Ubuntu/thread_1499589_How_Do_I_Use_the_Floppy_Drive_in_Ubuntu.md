---
title: "How Do I Use the Floppy Drive in Ubuntu?"
date: 2010-06-02
forum: New to Ubuntu
---

### Post by Ben_222 on 2010-06-02
Is there a guide on using the floppy drive in Ubuntu?I am having trouble finding anything .I have no blank floppies now;all are formatted for Windows.Many of them I can use for Ubuntu,but I can't mount them,and have no idea how to copy to them or read from them.Ubuntu is recognizing the drive,and "floppy drive" is in "Places" directly under "Computer".The icon for floppy drive also shows up when I open "Computer.Any help would be appreciated.

---

### Post by jerome1232 on 2010-06-02
It should get mounted when you click it's icon in the 'Places' menu.

You may be able to use a panel applet, right click you panel, click add to panel, find disk mounter, see if that helps.

---

### Post by Elfy on 2010-06-02
> **elliotn said:**
> Lol floppies are ancient technology, why wanna use em anyway

> **elliotn said:**
> Ohh stuff them and use a usb thumb drive.

That isn't addressing the issue is it.

---

### Post by bwallum on 2010-06-02
Disk Mounter works for me. As jerome1232 says:- On the top panel find a blank area, right click and choose 'Add to panel'. Look down the list for Disk Mounter, left click and it is added to your top panel.

From there, put a floppy into your floppy drive and left click on the Disk Mounter icon. You can choose to mount it and view the contents. Fat32 (vfat) or NTFS Windows style file formats can be read.

---

### Post by Butthead on 2010-06-02
Or learn to use the Linux terminal:

To mount floppy: mount /media/floppy

To unmount it when finished accessing it: umount (notice no "n') /media/floppy

To view what files are on it: ls /media/floppy | more

To read a text file on it: cat /media/floppy/filename.txt | more 

To learn how to format it, etc: apropos floppy, and then use the "MAN" command to see what each command does.

---

### Post by ron999 on 2010-06-02
With Karmic Koala I have to use this method:-


[U][B]Comment out the /dev/fd0 entry in the /etc/fstab file and reboot.
[/B][/U]
Then to mount the floppy use:-
```
sudo mount /dev/fd0 /media/floppy0

```

        
To unmount use:-
```
sudo umount /dev/fd0
```

---

