---
title: "Safe to remove USB device w/o Unmount?"
date: 2009-12-09
forum: New to Ubuntu
---

### Post by Cuco3 on 2009-12-09
Hello. I'm just wondering how safe is it to remove USB devices, such as an iPhone and a USB stick, without unmounting it first.

Windows also preaches "safely removing" anything USB before disconnecting it, but you can remove most USB devices with no repercussions. 

FWIW, I always unmount when it comes to a conventional hard drive w/ USB converter that contains important data.

---

### Post by SteveNorman on 2009-12-09
no its not, and its not safe in windows either. You have to click add/remove hardware in win, then select the device. You risk losing data and confusing your system if you do.

Use 

```
sudo umount /dev/sdd
``` 

or whatever your usb device is named in dmesg, then wait until the mount point no longer shows your device files.

---

### Post by SteveNorman on 2009-12-09
You can also unmount by right clicking the icon of the device as well, though I am not sure what your usb converter does. Is that a program that unmounts usb devices? kids these days and their new-fangled gadgets....

---

### Post by ukripper on 2009-12-09
Can have pretty bad repercussions by unplugging usb data device without unmounting. It can lead to data corruption if it is reading/writing.it can make your usb device undetectable under OS. it can make it read-only device then you may need to reformat the whole file system on it possibly losing data.

---

### Post by bumanie on 2009-12-09
If not unmounted correctly, the filesystem is viewed as being 'unclean' and linux will not mount it in case there is something wrong. Windows is not quite as discerning and despite advocating a 'safe removal', windows will still mount the filesystem. If you want to check, just pull a usb device out of windows without using 'safely remove', then try to mount it in linux. You get a message in linux about the filesystem not being shutdown properly. You can fix it by reinserting in windows and going through the 'safely remove' procedure.

---

### Post by Cuco3 on 2009-12-09
Thank you guys for the information. :)

---

