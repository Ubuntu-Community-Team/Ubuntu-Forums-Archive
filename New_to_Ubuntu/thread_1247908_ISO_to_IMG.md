---
title: "ISO to IMG?"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by coldReactive on 2009-08-23
I read this: [http://ubuntuforums.org/showthread.php?t=557237](http://ubuntuforums.org/showthread.php?t=557237)

But AcetoneISO doesn't convert ISOs to IMG. If it does, it doesn't do it via gui, which is what I'd like. Opening an ISO mounts it, but nothing else can be done.

---

### Post by gali98 on 2009-08-24
IMG = ISO...
Just rename it.
Is this about you trying to get windows xp installer on a usb?
Kory

---

### Post by coldReactive on 2009-08-24
> **gali98 said:**
> IMG = ISO...
Just rename it.
Is this about you trying to get windows xp installer on a usb?
Kory

Yep, it is.

---

### Post by gali98 on 2009-08-24
Okay... 
You can try using this with wine:
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?swItem=MTX-UNITY-I23839](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?swItem=MTX-UNITY-I23839)

(I am almost positive it works with wine.)
Rename your iso to img, then with this program, "Restore" the usb drive with the img file. I have had some success doing this with different isos...
Kory

---

### Post by coldReactive on 2009-08-24
> **gali98 said:**
> Okay... 
You can try using this with wine:
[http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?swItem=MTX-UNITY-I23839](http://h20000.www2.hp.com/bizsupport/TechSupport/SoftwareDescription.jsp?swItem=MTX-UNITY-I23839)

(I am almost positive it works with wine.)
Rename your iso to img, then with this program, "Restore" the usb drive with the img file. I have had some success doing this with different isos...
Kory

When clicking install, it says: "Unable to load DLL contents" or whatever, so it couldn't install, sorry.

With these terminal outputs:
```
ian@ian-desktop:~/.wine/drive_c$ wine cp006049.exe
fixme:process:SetProcessShutdownParameters (00000064, 00000000): partial stub.
fixme:msvcrt:MSVCRT__wsetlocale 0 L""
fixme:shell:BrsFolder_OnCreate flags BIF_NEWDIALOGSTYLE partially implemented
```

---

### Post by zeroseven0183 on 2009-08-25
Here's another option for you: [img2iso: A IMG to ISO converter]("http://www.t2-project.org/packages/img2iso.html")

---

### Post by coldReactive on 2009-08-25
> **zeroseven0183 said:**
> Here's another option for you: [img2iso: A IMG to ISO converter]("http://www.t2-project.org/packages/img2iso.html")

Err, I want the OTHER way.

---

### Post by gali98 on 2009-08-25
Erg... Sorry that didn't work. But an ISO file IS an IMG file. Just rename it.
Kory

---

### Post by coldReactive on 2009-08-25
> **gali98 said:**
> Erg... Sorry that didn't work. But an ISO file IS an IMG file. Just rename it.
Kory

I got WinXP Install CD on to the USB Drive on my grandma's windows machine, but... it installed but... it could only boot if the USB Drive was inserted.

I couldn't edit the boot.ini manually to make it not do this because I didn't know what disk number the HDD was for the netbook.

---

### Post by gali98 on 2009-08-25
You can use another flash drive and install ubuntu on it, then use that to change the boot.ini...
Kory

---

### Post by brunogirin on 2009-08-25
Jaunty has a built-in tool for this. Go to: System -> Administration -> USB Startup Disk Creator. Select the source ISO in the top list by either inserting a CD or clicking 'Other' and selecting a .iso file. Insert a USB flash drive and select it in the bottom list. Click on the 'Create startup disk' button and it will do the rest for you. You can even ask it to keep some space on the flash drive for your own files.

It will only work if you select an ISO of an Ubuntu desktop distribution but I'm assuming that's what you want to do.

---

### Post by coldReactive on 2009-08-25
> **brunogirin said:**
> It will only work if you select an ISO of an Ubuntu desktop distribution but I'm assuming that's what you want to do.

Nope, I want to do it for my Windows Install CD.

---

