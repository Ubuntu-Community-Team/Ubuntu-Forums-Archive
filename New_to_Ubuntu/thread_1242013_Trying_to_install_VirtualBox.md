---
title: "Trying to install VirtualBox"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by aharown07 on 2009-08-16
Brand new to any kind of Linux.
Got Ubuntu 9 installed.
Of course, have a few Win apps I need to keep using for a while. One I know requires some kind of virtualization so I attempted to install VirtualBox... which looked easiest.

Installed per directions at virtualbox.org and even did some configuring. 
Later, reboot and try to run virtualbox and it's not there... or acts like it's not there. So I try uninstall... then--well, long story. Now, when I try to run VirtualBox (ose) I get this error
```
  p, li { white-space: pre-wrap; }     Could not load the settings file [COLOR=#0000cc]'/home/adb/.VirtualBox/VirtualBox.xml'[/COLOR].
 Cannot convert settings from version [COLOR=#0000cc]'1.7-linux'[/COLOR].
 The source version is not supported.
     Result Code: 
  VBOX_E_XML_ERROR (0x80BB000A)
   Component: 
  VirtualBox
   Interface: 
  IVirtualBox {339abca2-f47a-4302-87f5-7bc324e6bbde}

```So... what did I break? And why did it work then not work after a reboot?

---

### Post by wojox on 2009-08-16
Try and remove the package. Open the terminal:
```
sudo apt-get --purge remove virtualbox*
```

Then add it through the repos:
```
sudo apt-get install virtualbox-ose virtualbox-ose-source

```

---

### Post by Rocket2DMn on 2009-08-16
To build on wojox's instructions, a bit of FYI:  Most applications that you will ever want to use in Ubuntu are available from Ubuntu's repositories.  We don't usually install applications by downloading installers from product's websites.  The programs in the repositories are configured to work with your version of Ubuntu, so you don't often get problems like you are seeing.
You can read more about repositories here - [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by aharown07 on 2009-08-16
Thanks! 
I hadn't gotten very far, so I went ahead and reinstalled Ubuntu and I'm now installing again from the repository. So we'll see how it goes.

---

