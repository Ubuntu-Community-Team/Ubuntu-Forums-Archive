---
title: "Ubuntu instructions on creating VirtualBx shared folders appear not to work"
date: 2015-01-20
forum: Networking &amp; Wireless
---

### Post by vincej on 2015-01-20
I'm following the instructions given here: 

[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)

I have executed them meticulously about 4 times now, and each time I get the same error back: 

/sbin/mount.vboxsf: mounting failed with the error: No such device

I have created my device on my windows guest under "Machine Folders" as per the instructions,

Name: share
Path: /home/vince/share


 then I create my virtual network with: 

sudo mount -t vboxsf -o uid=$UID,gid=$(id -g) share /home/vince/share

Boom - repeated errors ... 

What am I am doing wrong .. or are the instructions wrong ??? 

Many thanks 

using VB 4.3.2

---

### Post by TheFu on 2015-01-20
Did you load the guest additions into the guest VM?

Mounting doesn't have anything to do with creating a virtual network.  Sorry, but you've lost me.
What is the hostOS and what is the guestOS?

---

### Post by kpatz on 2015-01-20
You say you have a Windows guest but are using "sudo mount" to mount the shared folder?  That looks to me like you have a Linux guest.  Is it a Windows host?

You're doing the mount in the guest OS, right?  It won't work in the host OS.

EDIT: try **sudo modprobe vboxsf** in the guest and then try mounting.

---

### Post by vincej on 2015-01-20
I have  Ubuntu host and a win 7 guest and yes I have guest additions loaded. 

Ok "virtual network" may not be the correct term ... I thought that is how host to guest works ...

---

### Post by SeijiSensei on 2015-01-20
The default in VirtualBox is for the host to impersonate the guest on the network using "network address translation."  The host and guest have complementary virtual addresses using emulated adapters in a private address space.  The host acts as a NAT router, just like the border router between you and the Internet. 

VB has many other options available depending on your needs.  I recommend reading the documentation on networking at the VB site itself: [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

---

### Post by howefield on 2015-01-20
Is it a problem to use the VM manager settings ?

---

### Post by SeijiSensei on 2015-01-20
The default in VirtualBox is for the host to impersonate the guest on the network using "network address translation."  The host and guest have complementary virtual addresses using emulated adapters in a private address space.  The host acts as a NAT router, just like the border router between you and the Internet. 

VB has many other options available depending on your needs.  I recommend reading the documentation on networking at the VB site itself: [https://www.virtualbox.org/manual/ch06.html](https://www.virtualbox.org/manual/ch06.html)

I think kpatz has the right insight, though.  If you're using a Windows guest, then you need to mount the shared directory in Windows. The manual states:
> 
In a Windows guest, shared folders are browseable and therefore visible in Windows Explorer. So, to attach the host's shared folder to your Windows guest, open Windows Explorer and look for it under "My Networking Places" -> "Entire Network" -> "VirtualBox Shared Folders". By right-clicking on a shared folder and selecting "Map network drive" from the menu that pops up, you can assign a drive letter to that shared folder.


[https://www.virtualbox.org/manual/ch04.html#sharedfolders](https://www.virtualbox.org/manual/ch04.html#sharedfolders)

---

### Post by vincej on 2015-01-20
nope - no problem. The Ubuntu instructions tells me to first create a shared folder using the VB -> devices -> shared folders settings. Done that. Made in permanent  though. Hope that's ok. 

Then I must "prepare" the shared folder from the Ubuntu end. Did that.

---

### Post by vincej on 2015-01-20
SUCCESS !! I looked at the link you provded: [https://www.virtualbox.org/manual/ch...#sharedfolders]("https://www.virtualbox.org/manual/ch04.html#sharedfolders")

I attached the shared folder from the Windows guest perspective and it worked !! 

However, the instructions lead the reader to believe that to establish a shared folder, it is a 2 step process ...first, create the share in the guest, then "prepare" the share in Ubuntu. It is this 2nd step which still gives and error of : 

sudo mount -t vboxsf -o uid=$UID,gid=$(id -g) share /home/vince/share
/sbin/mount.vboxsf: mounting failed with the error: No such device

---

### Post by kpatz on 2015-01-20
Setting up and mounting a shared directory in VB is similar to setting up and mounting a network share, but instead of setting up the share on a server and mounting it on a client, you set up the shared directory on the host and mount it in the guest.

So, for example, if you wanted to share /home/vince/share on the host with your Windows guest, you'd set up a shared folder in the VM settings for your Windows guest (see howefield's post above).  You'd specify the host directory (/home/vince/share) and give it a share name (we'll use "share").  Then, in the guest OS (Windows), you can open \\vboxsvr\share to view the contents of the shared folder, or map a network drive to it (**net use s: \\vboxsvr\share**, and then the S drive will contain the contents of your shared folder).

If you're sharing to a Linux guest, you'd use the **sudo mount -t vboxsf share /mnt/share** type of command to mount it.

> **vincej said:**
> However, the instructions lead the reader to believe that to establish a shared folder, it is a 2 step process ...first, create the share in the guest, then "prepare" the share in Ubuntu. It is this 2nd step which still gives and error of : 

sudo mount -t vboxsf -o uid=$UID,gid=$(id -g) share /home/vince/share
/sbin/mount.vboxsf: mounting failed with the error: No such deviceThe "2nd step" you refer to is to mount the share in the guest, and that command is for a Linux guest.  There's no "preparation" required on the host side other than setting up the share in the VM settings (and creating the directory you're sharing if it doesn't already exist).  The remaining steps are on the guest side, to mount the share.

---

### Post by vincej on 2015-01-20
Many thanks!   Like so much in software - when you know how it is easy ! :o)

---

