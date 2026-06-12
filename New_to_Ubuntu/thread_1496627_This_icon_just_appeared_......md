---
title: "This icon just appeared ....."
date: 2010-05-29
forum: New to Ubuntu
---

### Post by ubantunovice on 2010-05-29
I am very new to Linux. I just installed Ubuntu 10.04 in an Oracle virtualbox. Works fine.

1. After I restarted it, I find this "disc like" icon  has appeared on my desktop which was not there when I shut Ubuntu down.  What is it? Do I need it?  How do I get rid of it if not needed?

2. Can I access my Windows 7 files from Ubuntu? how?

Thanks.

---

### Post by wilee-nilee on 2010-05-29
Hows about a screen shot. I know this is a dumb question, but you checked the disc player. Also does it reappear on rebooting the desktop or computer?

---

### Post by oleink on 2010-05-29
> **ubantunovice said:**
> I am very new to Linux. I just installed Ubuntu 10.04 in an Oracle virtualbox. Works fine.

1. After I restarted it, I find this "disc like" icon  has appeared on my desktop which was not there when I shut Ubuntu down.  What is it? Do I need it?  How do I get rid of it if not needed?

2. Can I access my Windows 7 files from Ubuntu? how?

Thanks.

1)  Is it an actual disc?  If you have a cd in than that will appear (I know you might think that is rude if you already know this but some people don't.  I didn't know when I first came to ubuntu cause it was my first linux kernel)

2) Sorry can't help you with that as I do not really use windows anymore

---

### Post by CharlesA on 2010-05-29
Probably have an ISO attached to the VM, since it's running in VirtualBox.

---

### Post by oleink on 2010-05-29
> **CharlesA said:**
> Probably have an ISO attached to the VM, since it's running in VirtualBox.

Yeah that is a good point.  Another thing is that you may be able to access your windows files via filesystem>media> (insert name of partition here)_______

---

### Post by CharlesA on 2010-05-29
If it's running in a VM, you could use the "shared folders" part of VBox, but I haven't really had much success with it.

You'd be better off creating a share, but I am not sure how you can get Ubuntu to see a share on a Win7 machine.

---

### Post by ubantunovice on 2010-05-30
I had nothing in the DVD drive which is what threw me. But you were right, the iso I used to install was still "mounted".  What confused me was that it was not present as an icon when I installed but only appeared on the desktop after I shut Ubuntu down and restarted it.  Now all is cool.

Thanks. (learning)

---

### Post by allexkii on 2010-05-30
You can share files between win7 and ubuntu .
1) just start shares-admin in terminal and install Samba service when asked 
2)than edit /etc/samba/smb.conf with your favourite Text editor ( example. sudo gedit /etc/samba/smb.conf) 
3)Find Line "# Change this to the workgroup/NT-domain name your Samba server will part of workgroup = NAMEOFYOURWINDOWSWORKGROUP" 
4)Save and close it.
5) type in terminal : 
service smbd restart
6) Have fun .:)


Alex

---

### Post by ubantunovice on 2010-05-30
Thank you.  Will try.

---

### Post by ubantunovice on 2010-05-30
> **allexkii said:**
> You can share files between win7 and ubuntu .
1) just start shares-admin in terminal and install Samba service when asked 
2)than edit /etc/samba/smb.conf with your favourite Text editor ( example. sudo gedit /etc/samba/smb.conf) 
3)Find Line "# Change this to the workgroup/NT-domain name your Samba server will part of workgroup = NAMEOFYOURWINDOWSWORKGROUP" 
4)Save and close it.
5) type in terminal : 
service smbd restart
6) Have fun .:)


Alex

Thank you Alex for the excellent instructions.  Everything worked just as you indicated (installed ntfs support and samba) except the last step.  When I did 
"service smbd restart", I got what I show in the attached image.

Maybe that is because I am using Ubuntu inside an Oracle virtualbox?

---

### Post by ubantunovice on 2010-05-30
More info:
I used the virtualbox devices\shared folders to add my Windows 7 data partition and it was accepted as such.  But in Ubuntu's file manager I cannot find it or a way to access it.  (That Windows partition is named F:\)

---

### Post by oleink on 2010-05-30
> **ubantunovice said:**
> More info:
I used the virtualbox devices\shared folders to add my Windows 7 data partition and it was accepted as such.  But in Ubuntu's file manager I cannot find it or a way to access it.  (That Windows partition is named F:\)

Did you try what I said?  Not sure if it will work but it has worked via a few other things and virtual box may work the same way.

---

### Post by wilee-nilee on 2010-05-30
If windows is the host a share folder in ubuntu is found by just right clicking on the W7 computer icon and then one of the drop down tabs I forget which one I don't have access to my W7 setup right now. It does a auto search for you.

The only time you have to use samba is when Ubuntu is the host.

---

### Post by ubantunovice on 2010-05-30
I cannot find something called "filesystem" on my Ubuntu window. Under applications I have something called "File Browser" that either came with the system or I installed. On this I went up and found "Media" but it is empty. "Mnt" is also empty, and under my WORKGROUP network name F: is not visible either.
But under Virtualbox  Devices\shared folders the F: drive is clearly visible as shared. See attachment. 
(I also checked in Windows 7 and that F:\ data partition is shared as read only).

Is there a command I can use in the terminal to mount this ntfs data partition?

---

### Post by migs73 on 2010-06-01
Hi there, me again. You can find file system under Places>Computer. ( I'm not a stalker, just have had similar experiences to yourself and find myself in the same old haunts)

---

