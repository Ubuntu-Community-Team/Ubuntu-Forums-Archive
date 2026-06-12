---
title: "mount a thumb drive through COMMAND LINE INTERFACE"
date: 2010-02-28
forum: New to Ubuntu
---

### Post by p3ar on 2010-02-28
Hello,

My terminology is lacking, so this may be difficult.

The OS on my computer was deleted, but I can sign in through the command line interface.  I'm trying to mount a thumb drive so I can just transfer the precious file of mine and open it on another computer.

Can someone walk me through the process of mounting a thumb drive?

Thanks!

---

### Post by johngreth on 2010-02-28
Is the output from
```
dir /media
```
any different with or without the drive plugged in?

---

### Post by flyingsliverfin on 2010-02-28
are using ubuntu or type of ubuntu?

post the output of fdisk -l when the flash drive is plugged in

---

### Post by p3ar on 2010-02-28
I'm using Ubuntu.

And I think I've mounted the USB, but now I am not sure how to copy the file.  
When I copied it using **sudo cp oldlocation newlocation** it doesn't ask for my password or anything, and when I booted from the live CD and tried to open it, the flash drive was empty.

---

### Post by johngreth on 2010-02-28
I don't see any reason the live cd would need a sudo password, but as for the actual file transfer, are you sure you're putting it in the right spot?

---

### Post by p3ar on 2010-02-28
Er.  Ok, so I don't have a GUI on my laptop, I deleted it somehow.  I can, however, access my files through the command line interface.  So my goal is to mount a USB drive through the command line interface and transfer the file I need onto the USB drive.  Then I would like to open the file while booting from a Live CD so I can e-mail the doccument to a non-Linux computer (when I plug the USB drive into the non-linux computer, it asks me if I'd like to format the USB drive and that is my only option).

---

### Post by p3ar on 2010-02-28
Also, I'm not sure what I did to make this happen, but my HDD is visible when using the Live CD.  How can I access the files on this drive?  I imagine I'll need to use the terminal, but I can't remember how to open files that way.

---

### Post by johngreth on 2010-02-28
> when I plug the USB drive into the non-linux computer, it asks me if I'd like to format the USB drive and that is my only option

I think you reformatted the usb drive to a Linux file system (ext4?). Maybe you could reformat the drive to "fat" from the non-Linux computer. That way both computers could read it.

I don't know of any way to send email from a command prompt.

---

### Post by p3ar on 2010-02-28
I'm not looking to send it that way, just open it from the Live CD, be that directly from the Live CD or through a USB accessed on the Live CD

---

### Post by johngreth on 2010-02-28
If you have gui, you should be able to read the files like normal. just double click the drive in "computer" that isn't "filesystem". "filesystem" is the cd.

---

### Post by p3ar on 2010-02-28
but it is protected as a root directory, which is why I thought i'd need the terminal to access it

---

### Post by johngreth on 2010-02-28
You could type
```
gksudo nautilus
```
to access everything with root permissions.

---

### Post by p3ar on 2010-02-28
ubuntu@ubuntu:/home$ gksudo nautilus
(nautilus:3534): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
Initializing nautilus-gdu extension

** (nautilus:3534): WARNING **: No marshaller for signature of signal 'UploadFinished'

** (nautilus:3534): WARNING **: No marshaller for signature of signal 'DownloadFinished'

** (nautilus:3534): WARNING **: No marshaller for signature of signal 'ShareCreateError'
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

---

### Post by matchett808 on 2010-02-28
have you thought about reinstalling ubuntu-desktop from your cd?

---

### Post by p3ar on 2010-02-28
Yes, but I need to retrieve this file first. :/  Paper due tomorrow.

---

