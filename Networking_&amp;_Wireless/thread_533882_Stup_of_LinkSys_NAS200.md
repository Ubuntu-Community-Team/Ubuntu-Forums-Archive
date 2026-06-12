---
title: "Stup of LinkSys NAS200"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by theooftheoretic on 2007-08-24
Hello, all.

I am a fairly experienced Linux user, but for the first time have tried to setup and use a Network Attached Storage system. I bought a LinkSys NAS200 (2 SATA drive bays, I have installed a 750GB SATA drive in one). I was thinking it would be like installing and using an external USB hard drive (very easy). It is turning out to be much more difficult.

First: How can I format the 750GB hard drive in it? The NAS200 came with a CD for Win32 setup, but since I'm running Ubuntu, that's of no use. The NAS200 is not automatically showing up anywhere for me to simply "format drive" on like I assumed a secondary hard drive would. It is not showing up at all anywhere that I can see.

Although I am experienced Ubuntu user, I have no experience with SAMBA or any other network storage system. Any pointers?

---

### Post by mcdsco on 2007-08-24
This is a Network Attached Storage device, not to be connected locally to your computer.  You will have to access it and manage it via the ethernet port.  Here is the user guide that Linksys provides:

[http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1175233467604&packedargs=sku%3D1175233152539&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=6760452539B03&displaypage=nodata#versiondetail](http://www.linksys.com/servlet/Satellite?c=L_CASupport_C2&childpagename=US%2FLayout&cid=1175233467604&packedargs=sku%3D1175233152539&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=6760452539B03&displaypage=nodata#versiondetail)

Once it has an IP Address which you can get from the administration page on your router, from within Ubuntu, you can click on Places --> Connect to Server, then select which option you want.   Ftp is supported out of the box.

You can also click on Places --> Network, and it might find the device under Windows Network.

Hope this helps <><Scott><>

---

### Post by BartInTN on 2008-01-14
I did not use the install CD and had no problem setting up the NAS200 device... I just plugged it in to my network and let it DHCP an address.  I had to look at the DHCP logs to see what IP it was assigned, then I http'd to the device.  I think the default was admin/admin to enter administrator mode.  There is a Disk Utlity option in the menu where I formatted my drives.  I set up smb and ftp, added a user, etc.

But I do have one problem with the device:  I can smb (Windows file share) to the NAS200 from my XP machine but not from my Ubuntu laptop.  For now, I'm using ftp... but I would like to use the filesharing.  My username and password are the same, and I am not prompted when I browse to it in Nautilus.  When I connect to the NAS200 host, it just shows me an empty window - no directories.  Any ideas?

---

### Post by BartInTN on 2008-01-15
Figured it out.  Nautilus by default tries the guest account.  The NAS200 has a guest account that cannot be deleted.  So in my setup, the guest account had no priv's - and when I connect to the NAS200 that is exactly what I get... a blank window.  I used smbclient command to troubleshoot.

---

