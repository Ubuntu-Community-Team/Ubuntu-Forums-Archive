---
title: "How to Install Applications From a Flashdrive"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by LongH on 2009-03-27
I have been trying to get Kubuntu working on several old computers withou an internet connection at my home. I wanted to know if I could download applications such as the compilation toolchain using my laptop which runs windows and install them on these old computers using a pen drive.

---

### Post by maddog39 on 2009-03-27
You basically just need to go to packages.ubuntu.com, search for the packages you need. Select the package you would like to install, go to the very bottom of the page and select the type of architecture you are using: i386 for 32bit and amd64 for 64bit. Copy the .deb file over to your flash drive, and when you bring it up on your other machines, simply double click on them and they will install.

---

### Post by decoherence on 2009-03-27
Yep! You have two options... first would be to point your Windows machine at

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

and find the packages you need. If you do this, make sure to pay attention to the dependencies... you'll have to get them all.

Another option would be to boot your Windows machine with the Ubuntu LiveCD. Download the packages in the standard way (again, making note of the dependencies) then check /var/cache/apt/archives for the appropriate install files (they end with .deb) 

The benefit of doing it the second way is that Ubuntu will automatically download all the dependencies. You still have to note them, though, so you know which ones to copy on to the USB disk.

Also, be sure you're using the right version. The Live CD should be the same version of Ubuntu as whatever is on your non-networked computers.

---

### Post by LongH on 2009-03-27
Thank you all very much! I am just now getting started with Linux and it has been a real challenge getting my AOL dial-up internet to work.

I was trying to download the Build-essential app and I was wondering what dependencies would be needed for it. I am getting a little confused because it appears that many dependencies themselves have dependencies.

---

