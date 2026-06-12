---
title: "Help, BIOS not reading usb"
date: 2010-11-14
forum: New to Ubuntu
---

### Post by fatharraxman on 2010-11-14
I am trying to install  ubuntu in a esk top but no bios window to tell to start from usb in booting
I pressed esc f1 f2 f3 f4 f5 f6 f7 f8 f9 f10 11 and f12 all not giving me boot choise to select booting from usb press delete only show BIOS utility but not helping 
what should I do lease??

---

### Post by coffeecat on 2010-11-14
Press DEL to go into the BIOS and then change the boot order priority there. Then save your BIOS changes.

---

### Post by fatharraxman on 2010-11-14
I pressed delet and in first boot device there is no usb among choices only:
1-IDE0
2-IDE1
3-IDE2
4-IDE3
4-ZIP100
5-LAN
6-DISABLED
7-FLOPPY
8-LS120
WHICE one to select??
please

---

### Post by coffeecat on 2010-11-14
In some BIOS's there is a separate entry called 'Hard Disc Boot Priority'. Plug your bootable USB device in, switch on, go into the BIOS and see if your USB is listed there. If so, put it no 1 in the list, but also check your first, second and third, boot devices.

---

### Post by fatharraxman on 2010-11-14
not listed
I tried all IDE in vain the Bios advanced utility is unalle to see my bootable usb what should I do please

---

### Post by coffeecat on 2010-11-14
I'm sorry, I'm out of ideas.

---

### Post by fatharraxman on 2010-11-14
Thank you cofeecat I appreciate you endeavors to help me 
could any one els in this forum help me please

---

### Post by mcduck on 2010-11-14
If you have no option to boot from USB in your BIOS, then it simply doesn't support such feature. Not all motherboards do. And based on the available boot options (IDE, ZIP and SuperDisk) I'd guess that's a bit older motherboard.

Check if the manufacturer has any BIOS updates available, if you have lucky such update might add support for USB booting.

If there is no BIOS update, or it doesn't add this feature, you pretty much have to use a CD or DVD instead.

---

### Post by sarc on 2010-11-14
I had a similar problem and fixed it by installing PLOP boot manager on CDROM, it works very well.  You select CDROM boot then PLOP will give you the option to boot from USB.  Search Google to download it.

---

