---
title: "Exposing Vista files to Ubuntu on VMWare"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by earthroamer on 2009-03-11
Ubuntu 8.10 running in VMWare player on Vista

How do move files from Vista to Ubuntu?

---

### Post by arqbrulo on 2009-03-11
Hmmmm...... Well, obviously you would have to share a folder, the question is how. I remember doing it, I just can't remember how, or where I got the information from. I do remember that you have to edit one of the .vmdk or .vmx or one of those files. Let me redo my research and I'll post back once I find something.

---

### Post by arqbrulo on 2009-03-11
Aha, I found something that can help you, here's the link, [www.visoracle.com/download/debian/sharedfolders.html]("www.visoracle.com/download/debian/sharedfolders.html"). It was the .vmx that you have to edit and add a few lines.

After you do what they tell you, start VMPlayer and on the menus on top, find the option to share a folder, you should be able to select which folder you want to mount on Ubuntu.

---

### Post by earthroamer on 2009-03-11
Thanks arqbrulo, I'll give this a try.

---

### Post by arqbrulo on 2009-03-11
Sorry for making too many posts about nothing, it's my first time at trying to help someone out. Anyways, it seems that there is something I forgot to mention, you need to install VMWare Tools. Here is a guide: [http://yy416808.awardspace.com/InstallingVMwareToolswithVMwarePlayer.html]("http://yy416808.awardspace.com/InstallingVMwareToolswithVMwarePlayer.html"). Now, from what I understand, you have Ubuntu as guest and Vista as the host. I think all those steps can be done with Ubuntu running, just change "windows.iso" to "linux.iso".

---

### Post by earthroamer on 2009-03-12
yes, Vista host, ubuntu guest

I've got everything but the VMWare Tools. Followed the link you provided, mounted the linux.iso, ran the perl script, but it choked about halfway through with a mismatched kernel (I think). I'll look for another way install the tools. Thanks for the help.

---

### Post by arqbrulo on 2009-03-12
Well, I managed to find two more "tutorial" on how to install the tools on ubuntu guest, but they are for VMWare Server. At least they will guide you in the right direction. Anyways, here are the links, I hope they help.

[http://ubuntu-tutorials.com/2008/06/07/how-to-install-vmware-tools-on-ubuntu-804-guests/]("http://ubuntu-tutorials.com/2008/06/07/how-to-install-vmware-tools-on-ubuntu-804-guests/")
and
[http://ubuntu-tutorials.com/2007/10/02/how-to-install-vmware-tools-on-ubuntu-guests/]("http://ubuntu-tutorials.com/2007/10/02/how-to-install-vmware-tools-on-ubuntu-guests/")

They're both from the same place, the first one is newer than the second one. Good luck.

---

### Post by earthroamer on 2009-03-12
Thanks a lot, arqbrulo. I'll work on these. I have VMWare Server on my work computer, so I may just copy the vm files over and install it from there.

---

