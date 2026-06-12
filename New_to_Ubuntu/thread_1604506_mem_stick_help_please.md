---
title: "mem stick help please"
date: 2010-10-24
forum: New to Ubuntu
---

### Post by skiddly on 2010-10-24
Hi whilst keeping windows on my desktop pc, i thought id make the leap and make ubuntu my sole operating system on my netbook d/l onto mem stick and installed fine but now if i put a mem stick into usb port to put some photos etc onto netbook hd nothing happens so i assume its now not recognising them any advice please thanks skiddly :confused:

---

### Post by bprins on 2010-10-24
If I put a mem stick in my laptop, I can open the mem-stick via my Places menu. Doesn't a memory option appear there? Places -> memstick.

---

### Post by Jest3r on 2010-10-24
Hiya,
   If you run the following it might shin some light on the issue.
 
   * shows everything connected via usb.
   $ lsusb 
    
    This display a log of usb related activity.  
   $ dmesg | grep usb



Neither should show any personal/private information.


   The other would be 
   $ sudo fdisk -l

---

### Post by skiddly on 2010-10-24
cant even see my places the desktop on netbook remix is different to ordinary pc its got me beat

---

### Post by skiddly on 2010-10-24
> **Jest3r said:**
> Hiya,
   If you run the following it might shin some light on the issue.
 
   * shows everything connected via usb.
   $ lsusb 
    
    This display a log of usb related activity.  
   $ dmesg | grep usb



Neither should show any personal/private information.


   The other would be 
   $ sudo fdisk -l

i now managed to see storage devices but when i click on mount volume it fails to mount

---

### Post by Paqman on 2010-10-24
When you plug the stick in it will show up as a little USB icon in the launcher on the left. Just click on it to open the stick.

Right click on the icon and hit "eject" before you unplug it.

---

### Post by skiddly on 2010-10-24
tried 3 different mem sticks and no icon appears in left hand launcher

---

### Post by skiddly on 2010-10-24
well just tried one again and success dont know why ill try the other 2

---

### Post by tajiknomi on 2010-10-24
[SIZE=2][I]Note that windows can't recognize **Formate(ext-3, ext-4)**
try to formate ur stick to fat/ntfs....
[/I][/SIZE]

---

### Post by skiddly on 2010-10-24
thanks as other 2 wont work ill try that cheers

---

