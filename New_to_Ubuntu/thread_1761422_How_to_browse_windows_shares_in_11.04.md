---
title: "How to browse windows shares in 11.04?"
date: 2011-05-18
forum: New to Ubuntu
---

### Post by chah on 2011-05-18
Previously, I could go to places and find windows shares, but this new unity interface is different. I can't seem to find documentation for it either. 

I want to be able to access a share like this:
\\192.168.1.33\myfile

How do I do it in 11.04?

Thanks

---

### Post by frankbooth on 2011-05-18
Usually windows partitions aren't mounted on login, unless added to fstab.

**To browse your windows files without messing with fstab:**

**1)** Open nautilus (by either launching it by itself or opening your home folder).
**2)** Your drives (mounted [has an eject arrow next to it] or unmounted [without arrow]) should be visible in the left pane of nautilus. By clicking on an unmounted drive it will automatically be mounted to */media/NAMEofYourDRIVE*.

**To make your drive(s) auto-mount when logging in:**

[http://ubuntuforums.org/showthread.php?t=959315](http://ubuntuforums.org/showthread.php?t=959315)

---

### Post by chah on 2011-05-18
Hi Frank,

Thanks for your reply. But it isn't mounting a local drive that I'm trying to do. I want to access a windows share on somebody else's computer on the LAN, akin to using smbclient. The windows equivalent is typing \\192.168.4.22\shared_drive into windows explorer.

---

### Post by coffeecat on 2011-05-18
> **chah said:**
>  The windows equivalent is typing \\192.168.4.22\shared_drive into windows explorer.

The Ubuntu Natty (Unity) equivalent is to open a Nautilus folder by clicking on the Home Folder icon in the launcher. Press ctrl-L to get the text location address bar and then type "smb://192.168.4.22/shared_drive" (no quotes) in the location field for your above example. Then press enter.

**Or**... Nautilus window > File menu > Connect to Server. Fill in the appropriate fields in the "Connect to Server" window - choose "Windows Share" in the drop-down for Service Type.

One caveat. I've read that there's some issue with browsing Windows 7 shares. This is a Windows 7 issue, not an Ubuntu one. I believe it also prevents earlier versions of Windows browsing Windows 7 shares. You have to disable something or other in Windows 7, but I can't remember what this was. If I come across this, or remember, I'll post back.

---

### Post by ghostborg on 2011-05-18
I don't remember where it is in my brief Unity experience but you should be able to open Nautilus and then from the file menu choose File and Connect to Server. Also from Nautilus in GO should be Network, Computer , etc.

---

### Post by pablolie on 2011-05-18
> **chah said:**
> Previously, I could go to places and find windows shares, but this new unity interface is different. I can't seem to find documentation for it either. 

I want to be able to access a share like this:
\\192.168.1.33\myfile

How do I do it in 11.04?

Thanks

I still think installing Samba is the way to go. It allowed my 11.04 computer to be integral part of a Windows Workgroup and I happily copy files back and forth.

---

### Post by chah on 2011-05-18
Hi all,

Thanks for your replies. I didn't know about the ctrl-L shortcut

---

