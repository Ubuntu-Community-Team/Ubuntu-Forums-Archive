---
title: "USB in Virtualbox OSE"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by sammy0131 on 2010-08-21
Hi, I'm new to ubuntu so trying to get Windows XP still handy. I decided to try the Virtualbox OSE. I installed XP with no problem but only the issue is that I cannot access to the USB drive from the guest XP. More specifically, I would like to read the USB license key (Sentinel USB key) because I still have a couple of softwares for my work that can only run on Windows with the USB license key.

Please help me if anyone know how to solve this. Otherwise I might have to go back to the Windows but I really like Ubuntu.

Thanks in advance,

---

### Post by McNils on 2010-08-21
One of the limitations of ose is that it has disabled the usb-drives. You need to install the other version from virtualbox.

---

### Post by wilee-nilee on 2010-08-21
Here is a link to what you need.
[http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

This is the Puel version. You just need to add yourself to the vbox group in admin-users groups.

If your using the basic equal OSE version you can just use the VDI you already have.

---

### Post by sammy0131 on 2010-08-21
>Here is a link to what you need.
[>http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

>This is the Puel version. You just need to add yourself to the vbox group in admin-users >groups.

Can you please explain more how to do this? I went to the link and tried to download it. There's an error which says there's a conflict with the OSE version so that I couldn't do anything. 

>If your using the basic equal OSE version you can just use the VDI you already have.     

How do I do this?

Thanks for being patient with me but I really want to be windows free and this is the only problem!! Thanks so much!!!

---

### Post by Morbius1 on 2010-08-21
Actually there is a way to access USB using the OSE version if the host is linux and the only thing you need is access to a USB storage device:

(1) On the Linux host: Use the VirtualBox > Settings > Shared Folders to create a shared folder to /media

(2) Start the VBox WinXP then open Computer > Tools > Map Network Drive > Folder > VirtualBox Shared Folders > \\VBOXSVR\media

Make sure "reconnect at logon" is checked

Every time you boot into WinXP you will have a drive letter that points to /media and within that will be any usb ( or cd / dvd ) device that is mountable by the linux host. It won't work like inserting some usb device and having WinXP launch an application but if it's just an external hard drive then it'll work.

---

### Post by sammy0131 on 2010-08-21
Thanks for your response!

I created the shared drive and I could read the USB as an eternal drive with no problem. But what I wanted to do is, as I mentioned in the previous thread, to read the USB license key (Sentinel key) and I don't know still how to read the license from the guest Win machine. Has anyone read the license key by creating the shared drive??

I would really appreciate if anyone can give me a trick.

---

### Post by sammy0131 on 2010-08-21
I uninstalled OSE version hoping that I can install the Puel version as wilee-nilee suggested. But I keep getting the error messgae "Error:Conflicts with the installed package 'virtualbox-ose'. Can anyone please help??

---

### Post by wilee-nilee on 2010-08-21
go to synaptic and search with virtualbox to see if any ose programs are still installed.

How are you try to install the puel version?

---

### Post by bodhi.zazen on 2010-08-21
There are ways to hack usb devices with OSE, but, honestly, it is just as easy to set up samba or nfs to share files. Alternates would include ftp, http, rsync, and / or ssh (sshfs).

So you have several options ;)

---

### Post by sammy0131 on 2010-08-21
I went to Synaptic and removed all that have ose and it worked! Now I installed the Puel version and Windows XP on it, but here's another problem. I don't see the USB drive still...
Do I need to install Guest Additions just like the OSE version?

any idea??

---

### Post by wilee-nilee on 2010-08-21
> **sammy0131 said:**
> I went to Synaptic and removed all that have ose and it worked! Now I installed the Puel version and Windows XP on it, but here's another problem. I don't see the USB drive still...
Do I need to install Guest Additions just like the OSE version?

any idea??

Shutdown the Vbox. Go to system-administration-user groups-manage groups-vboxusers: click on properties then your user name ticked on.

Then go to settings for your W7 in vbox, (top panel) click on usb and on the right of the screen are add remove edit..etc buttons.

---

### Post by sammy0131 on 2010-08-21
I found that I need the Guest Additions to be able to use the USB in the Puel version. I tried to install it through Synaptic but then was asked to remove the Puel version and reinstall the OSE version:-( I didn't find on the website, where can I find it??

---

### Post by wilee-nilee on 2010-08-21
> **sammy0131 said:**
> I found that I need the Guest Additions to be able to use the USB in the Puel version. I tried to install it through Synaptic but then was asked to remove the Puel version and reinstall the OSE version:-( I didn't find on the website, where can I find it??

The guest additions part is in the upperpanel in a dropdown to add in the running vbox. You just open computer in XP and then the guest additions and click on your 32 or 64 bit setup.

---

### Post by sammy0131 on 2010-08-21
Thanks wilee-nilee.  I added myself in the group and added the usb drive in the setting as suggested. Then rebooted the XP and hooked up the usb drive. XP started looking for a driver, which means it finally recognized the usb drive, but since I don't have a driver, I let it find and failed. I also installed the guest additions, then now I can see a shared folder I've created but cannot still see the usb drive. What's going on?? I thought I was almost there;-(

---

### Post by sammy0131 on 2010-08-21
Thank God!!! It worked!!!! I simply didn't chose the right device in Devices on the top panel of Win XP. 

This was my first use of this Ubuntu forum and I'm amazed how ubuntu users are helping each other. Now I can be totally Windows free. I love Ubuntu!!! Thanks!!

---

