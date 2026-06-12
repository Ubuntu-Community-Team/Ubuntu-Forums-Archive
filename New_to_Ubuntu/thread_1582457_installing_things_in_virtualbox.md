---
title: "installing things in virtualbox"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by Commisar Jimp on 2010-09-26
Hi,
I just installed windows 7 in virtualbox, and I want to install programs that are on my computer to it, but it isn't on the windows file system. How can I open files that are on my Linux file system in Virtualbox?

---

### Post by thomas144 on 2010-09-26
I think I might be able to help. I use Virtualbox, but I don't use Windows in it. Right now I'm launching my Virtualbox and doing some Googling...

---

### Post by thomas144 on 2010-09-26
Here's a link I found:
[https://help.ubuntu.com/community/VirtualBox/SharedFolders](https://help.ubuntu.com/community/VirtualBox/SharedFolders)
If you don't understand it, I'm not sure if I do, either. Still looking.

---

### Post by Commisar Jimp on 2010-09-26
I don't completely follow that, but it gives me a starting place, thanks for the help.

---

### Post by thomas144 on 2010-09-26
First, you have to install guest additions:
Start you Windows 7 Virtualbox and go to Devices > Install Guest Additions.
Then, in Windows 7, open up Windows Explorer to the guest additions CD.
Right-click on the correct installer (32 or 64-bit).
Run it in Compatibility mode for Windows Vista.
Install the guest additions as usual.
Reboot the Windows 7 virtual machine.
...and the guest additions should be installed.

I got this from [http://blogs.sun.com/fatbloke/entry/windows_7_on_virtualbox](http://blogs.sun.com/fatbloke/entry/windows_7_on_virtualbox).

And here's a good howto for sharing folders:
[http://news.softpedia.com/news/How-to-Fix-Windows-7-Sharing-in-VirtualBox-123021.shtml](http://news.softpedia.com/news/How-to-Fix-Windows-7-Sharing-in-VirtualBox-123021.shtml)

Does this help?
Please bear with me, I've never done this before.

---

