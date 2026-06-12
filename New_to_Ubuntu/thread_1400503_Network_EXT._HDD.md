---
title: "Network EXT. HDD"
date: 2010-02-07
forum: New to Ubuntu
---

### Post by m4nm4n on 2010-02-07
I have a networked 1TB Iomega HDD.
It's already connected to my router, and showed up when 
I was running on windows.
How do I 'see' it in my file system?
How do I access it's files?

running on ubuntu 9.10 Karma

---

### Post by nhasian on 2010-02-07
i guess it depends on how your router is configured to share it.  if windows sees it then i'm going to guess its using samba.  if thats the case, simply go to Places->Network and you should see the share there.

---

### Post by 3rdalbum on 2010-02-07
Once you've opened the share in Places > Network, it will appear on your desktop. However, it is actually mounted in a folder called ".gvfs" inside your home directory. The full-stop at the start of the folder name means that it's hidden. You will want to add this folder as a bookmark in a Gnome program and a KDE program so you can access your share from Open/Save windows inside your programs.

---

### Post by m4nm4n on 2010-02-07
Well actually. I needed to install a program that came with a companion CD. On Windows, to be able to access the stuff on the HDD.

I don't think the installation will work on linux. The box says only installable on windows and Mac.

(so,BTW, it's not showing up on my Places>Network)

---

### Post by nhasian on 2010-02-07
probably the softare iomega provides is only windows/mac but that doesnt mean you cannot use the drive in linux.  actually you shouldnt use their software in windows either hehe

NOTE: no additional drivers are required when installing an external usb hard disk.  the software the manufacturer provides on the installation CD may be tools for backup or encryption which is not required for the operation of the drive.

> **m4nm4n said:**
> Well actually. I needed to install a program that came with a companion CD. On Windows, to be able to access the stuff on the HDD.

I don't think the installation will work on linux. The box says only installable on windows and Mac.

(so,BTW, it's not showing up on my Places>Network)

---

### Post by m4nm4n on 2010-02-07
Yeah, I know. I CUSTOM install a lot of programs on Windows.
It was basically a small gui management program, so you could access files without having to go into the Network Storage folder and stuff.

I can't open my 'Windows Network' folder in Places>Network

"Unable to mount location"
Failed to retrieve share list from server.

I do have the ExtHDD under the "workgroup" network name. Does that provide any new useful info?

---

### Post by m4nm4n on 2010-02-07
Solved! ok i went to 

Places>Connect To Server

"windows share" put in the drive's IP

and it 'saw' the drive. YAY!

---

