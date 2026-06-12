---
title: "Virtual Box Folder Paths"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by JREAM on 2009-11-15
Yeh, I installed Virtual Box and it works very nicely.

I am wondering how come if I save a text file in VirtualBox, it won't allow me to save higher than the c drive? Wine allows me to do this.

Is there a way to make the windows system allow me to save to the linux folders? I heard of Samba but I dont know where to start,  they are large manuals and I just want to do 1 thing which is **pass the virtual file to the linux filesystem.**

You knaht very much :)

---

### Post by howefield on 2009-11-15
Use the shared folders feature ?

Third video down the page, it is a short one.

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)

---

### Post by JREAM on 2009-11-15
Thank you this is very exciting. Sorry I did not see the videos here!

---

### Post by lordyosch on 2009-11-15
+1

> **howefield said:**
> Use the shared folders feature ?

Third video down the page, it is a short one.

[http://www.virtualbox.org/wiki/VirtualBoxTV](http://www.virtualbox.org/wiki/VirtualBoxTV)



Also, you could always have a web-based storage doodah, like dropbox or similar. This is how I do it, I can also share stuff with work PC this way too

---

### Post by JREAM on 2009-11-15
Well I have DropBox for my laptop XP to Linux, vise versa, very nice!

but for virtualized OS I dont want to drop box everything, I will consider that though if i cant get a share to work :d

Basically because it takes longer to upload/download than swap a file locally.

---

### Post by shwallace on 2009-11-15
I'm assuming you're running a windows os in vitual box right? If so, open vbox and start windows. Look for the Devices tab in the vbox window. click that and go to Shared Folders. This will allow you to access any mounted partion on your hard drive. Once you've added a shared folder you can then map it as a network drive in the windows virtual machine.

---

### Post by JREAM on 2009-11-15
Do I need SAMBA to get all this to work?

---

### Post by JREAM on 2009-11-15
Okay I got it working I needed a Guest install thing,
this is amazing :D

---

### Post by Paqman on 2009-11-15
> **JREAM said:**
> Do I need SAMBA to get all this to work?

No, Samba is for getting a Windows machine and a Linux machine to talk to each other over a network.

---

