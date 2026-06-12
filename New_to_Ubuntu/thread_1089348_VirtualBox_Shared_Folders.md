---
title: "VirtualBox Shared Folders?"
date: 2009-03-07
forum: New to Ubuntu
---

### Post by Gp. on 2009-03-07
Hi,
I've made some shared folders with Virtualbox, but where do I access them inside vista? (VM)


They don't seem to be anywhere?

I have the guest additions installed.

Please help.

---

### Post by Xiong Chiamiov on 2009-03-07
It should be the same as [in XP](http://www.giannistsakiris.com/index.php/2007/09/28/virtualbox-access-shared-folders-from-windows-xp-guest-os/).

---

### Post by albandy on 2009-03-07
first ensure to have installed the virtualbox guest additions in windows
then the path to acces shared folders is : \\vboxsvr\sharedname

---

### Post by Gp. on 2009-03-07
Neither of these worked :(

---

### Post by howefield on 2009-03-07
You have created the shared folder and put it into the virtualbox settings, yes ?

Then load up your virtual machine, right click on "my computer" and select Map Network Drive, select the drive letter you want to give it, default is probably Z and then press the browse button.

You should see VirtualBox Shared Folders, click on the plus sign to the left, highlight the folder and ok your way back out.

Did that work ?

---

### Post by albandy on 2009-03-07
See this video I've made for you:

[http://www.linuxlleida.com/out-3.ogv](http://www.linuxlleida.com/out-3.ogv)

---

