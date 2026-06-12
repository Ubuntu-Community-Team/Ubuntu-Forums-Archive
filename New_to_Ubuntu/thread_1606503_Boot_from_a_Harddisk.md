---
title: "Boot from a Harddisk"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by jkveenstra on 2010-10-26
I'm new to this forum and please excuse me if the questions is asked before (i used the search button and searched the internet for several hours now).

I Use Ubuntu for a couple of weeks now on my MSI Wind and I like it very much. 

I have an older laptop (NEC P520) on which I would like to install Ubuntu as well. The BIOS does not allow to boot from USB nor from CD (drive is probably broken). I used Plop boot manager on a floppy drive to boot from USB, but is doesn't work either.

Now I thought of installing Ubuntu on the harddrive (using my MSI wind) and make it bootable somehow. I tried to do this with UNetbootin. If I install the Harddrive back into the NEC and boot from that, I tells me that no OS is installed.

What am I doing wrong. Any help is greatly appreciated!

---

### Post by spiky001 on 2010-10-26
Do you mean you swapped hard drives in laptops then loaded Ubuntu on it then put it back in other machine?

---

### Post by jkveenstra on 2010-10-26
I did not swap them. I installed the NEC harddrive in a external harddisk case, which I access through USB on my MSI.

Sorry I wasn clear.

---

### Post by spiky001 on 2010-10-26
I have swapped drives before loaded it then swapped it back,

---

### Post by spiky001 on 2010-10-26
Have a look here [http://linuxers.org/howto/how-install-ubuntu-910-without-cddvd](http://linuxers.org/howto/how-install-ubuntu-910-without-cddvd)

---

### Post by jkveenstra on 2010-10-26
thanks Spiky.

It will have a go at it.

---

### Post by jkveenstra on 2010-10-26
I followed the procedure as mentioned in the link.

It still didn't work. Then I checked the fommating of the drive, which was ext4. Since the laptop is quite old, I formatted on NTFS.

Apparently something works. But now I get the message: BOOTMGR is missing.

therefore I changed the hd0,1 into 2 through 4 in the menu.lst file (in /boot/grub). Still no result.

if I install the drive into the external case and onto my MSI the drive shows "dev/sdc1". Should I use another hd0 number? (maybe a stupid question, but i'm not familiar with this)

---

### Post by spiky001 on 2010-10-26
Not sure on terminology but as a usb device it see,s it as sdc. "Mine shows as sdb". When it is installed as main drive will it boot? Is it the only OS on harddrive?

---

### Post by jkveenstra on 2010-10-26
when I boot from my MSI, the problem occurs as well. I only installed the OS, nothing else.

Thanks for your replies

---

