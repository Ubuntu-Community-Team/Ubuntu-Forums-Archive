---
title: "how to make windows boot able inside of Ubuntu ?any idea"
date: 2010-12-22
forum: New to Ubuntu
---

### Post by santosamaru on 2010-12-22
as sure i think i need some Photoshop also some online games that can be able to play in Ubuntu. 
anyone know how to make windows can be boot able in Ubuntu , so its looks like dual boot, without installing its . without using CD installers, any idea on its ? cause as much i can find they are asking about use your cd to installing its, i means i just want to make its like a shortcut , so with one click my Ubuntu can load the windows or playing game , or using Photoshop. thanks.

---

### Post by bodhi.zazen on 2010-12-22
You can do this with both virtualbox and KVM, probably vmware and qemu as well.

The problem is Windows sees the virtual machine as "new hardware", and you need a custom hardware profile, and if you make a mistake, you can trash windows.

So it is much easier to reinstall in a VM or run Ubuntu in windows.

Alternately you could try making a raw image of your windows install and try booting that. At least this way you would not be disturbing the actual install.

[http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html](http://mesbalivernes.blogspot.com/2008/01/virtual-box-booting-from-existing.html)

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

---

