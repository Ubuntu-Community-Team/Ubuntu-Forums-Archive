---
title: "Folder Sharing"
date: 2007-10-29
forum: Networking &amp; Wireless
---

### Post by greg.collver on 2007-10-29
I installed Ubuntu 7.10 this weekend and I like it. I wanted to share a folder with some Window PCs and when I right clicked the folder and tried to share it, a dialog box informed me that I would need to install Unix or Windows sharing. I clicked OK and I thought it would install it from the installation CD, but it did nothing. I assumed it was trying to find the software on the internet, but I did not have an internet connection. The puzzling thing is that it didn't give me an error message, it just closed the dialog and appeared to do nothing.

---

### Post by petit.padavoine on 2007-10-29
I don't think the installation CD has Samba on it (samba is the file-sharing server).

You'll need to get a connection or download the .deb packages from another computer to a usb key or something.

Is the network itself already set up (ie can you ping the windows pcs)?

---

### Post by greg.collver on 2007-10-29
Yes, that part was very easy. I was able to connect my Ubuntu PC to my Window PC shares just fine. So far I really like this new version of Ubuntu, it just keeps getting better and better. :) I just need to learn how to download software and install it on Ubuntu when I don't have an internet connection.

---

### Post by petit.padavoine on 2007-10-30
In Ubuntu (and most Linux distros), software is organized into packages.
[This](https://help.ubuntu.com/7.04/add-applications/C/index.html) should explain a little bit more about packages.

Since you don't have a connection, you need to find exactly which packages are required to share files, download them from a computer which HAS an internet connection to a USB key or something, and then install them from your PC.
[This page](https://help.ubuntu.com/7.04/server/C/windows-networking.html) should help you find the exact packages you need and set up Samba correctly.
[This](http://packages.ubuntu.com/gutsy/net/samba) page gives you more info about the samba package (requirements, etc...)

---

### Post by greg.collver on 2007-10-30
Thanks.

By following the last link and scrolling to the bottom, I was able to download "samba_3.0.26a-1ubuntu2_i386.deb" file and copy that to my thumb drive.

From reading the info on the first link and following to this page:
[https://help.ubuntu.com/7.04/add-applications/C/advanced.html](https://help.ubuntu.com/7.04/add-applications/C/advanced.html)
I think what I need to do is open a console window and issue this command:
sudo apt-get install samba_3.0.26a-1ubuntu2_i386.deb

---

### Post by petit.padavoine on 2007-10-31
> **greg.collver said:**
> Thanks.

By following the last link and scrolling to the bottom, I was able to download "samba_3.0.26a-1ubuntu2_i386.deb" file and copy that to my thumb drive.

From reading the info on the first link and following to this page:
[https://help.ubuntu.com/7.04/add-applications/C/advanced.html](https://help.ubuntu.com/7.04/add-applications/C/advanced.html)
I think what I need to do is open a console window and issue this command:
sudo apt-get install samba_3.0.26a-1ubuntu2_i386.deb

Actaully sudo apt-get is for an install from repositories, and not for a single .deb package. The command is dpkg -i samba_etc...

I think you also need to get samba's dependencies, so if when you try to install it it asks you for another package, get it from packages.ubuntu.com (you can search from a specific package by googling "site:package.ubuntu.com <specific package>".

---

