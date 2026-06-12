---
title: "How can I network my Xubuntu machin to Apple?"
date: 2007-12-05
forum: Networking &amp; Wireless
---

### Post by thenetduck on 2007-12-05
HI

First let me tell you, I am terrible at network. I don't really understand the basic concept or something. I have read lot of stuff on it and still just seem to be terrible. sorry if this doesn't modivate you, but I need really simple "laymens" terms :) 

moving on.....


I just installed Xubuntu Gusty Gibbon and connected it to my NetGear Wireless router. I also have an iMac osX and it is connected to the internet though the same NetGear router. I also have a printer connected to my iMac. This is what I would like to be able to do.

1) Share that printer. I would like to be able to print things from both my Xubuntu machine and iMac machine. 

2) Transfer and Share files. If i am working on my iMac, I would like to be able to move a file to a shared folder and access it with my Xubuntu machine. 

I have went to the "Shared Folders" and installed both of what it told me to install and then created a folder on my users home called "Network Shared" and then enabled it as my shared folder. 

My question is what do I do next? How can I 1 and most importantly, print from my Xubuntu machine and share files back and forth? Should I plug my printer's USB into my router? Would this give me access to the printer both ways ? 

Sorry if that was a stupid suggestion to get things to work. Like I said networking kind of scares me. Thank you for any help you give me .

The Net Duck

---

### Post by Seti on 2007-12-05
I would recommend looking into NFS, its a nice and simple way to mount a file-system over a network and easily accessible. 
Also, ssh and scp are awesome when it comes to remote access and copying.
As far as printing, it should be a snap to set up the printer attached to your Mac as the default printer on your Ubuntu desktop.

---

