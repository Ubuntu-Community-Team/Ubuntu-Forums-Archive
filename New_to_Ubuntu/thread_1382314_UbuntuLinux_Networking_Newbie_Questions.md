---
title: "Ubuntu/Linux Networking Newbie Questions"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by darc26 on 2010-01-15
Hello,

I think I have a good book, "A Practical Guide to Ubuntu Linux."  I am really interested in learning more about networking with it and was wondering if there was some safe site that I can connect to and play around with utilities such as finger and things like that.  These things are hard to learn on a local setup. If you have an even better idea, please let me know.  Thanks again.

---

### Post by bcn17 on 2010-01-15
I would do your best to find an old computer and install ubuntu server edition. Make your first project installing openssh-server (which can actually be done during the install) and then try all your networking ideas connecting to your server. Keep in mind, you don't need a monitor, or keyboard after install. If you want a tutorial explaining ssh in reasonable detail I have made one. [http://bryanroller.com/computers/openssh-server.html](http://bryanroller.com/computers/openssh-server.html)

---

### Post by superprash2003 on 2010-01-15
here are a few good links
1)[http://ubuntuguide.org/wiki/Ubuntu:Karmic](http://ubuntuguide.org/wiki/Ubuntu:Karmic)
2)[www.ubuntugeek.com](www.ubuntugeek.com)

---

### Post by darc26 on 2010-01-15
I have a mac and and my ubuntu box which is also a dual boot of Windows XP.  I currently don't have the server addition of Ubuntu installed, but is there a way I can learn these utilities between my Mac and Ubuntu?  I really don't have the room for another computer.  Thanks again.

---

### Post by pirateghost on 2010-01-15
> **darc26 said:**
> I have a mac and and my ubuntu box which is also a dual boot of Windows XP.  I currently don't have the server addition of Ubuntu installed, but is there a way I can learn these utilities between my Mac and Ubuntu?  I really don't have the room for another computer.  Thanks again.
virtualbox or vmware....

---

### Post by darc26 on 2010-01-15
Umm, Im not familiar with those terms.  Its a physically separate computer if that is what you are asking.

---

### Post by pirateghost on 2010-01-15
> **darc26 said:**
> Umm, Im not familiar with those terms.  Its a physically separate computer if that is what you are asking.
google virtualbox or vmware.....they both will allow you to virtualize an entire OS inside of your OS, and you can practice all you want

i would recommend Virtualbox, because it is free.  vmware workstation costs money and vmware server is free but buggy and not linux friendly on releases like ubuntu

the best part of Virtual machines is that if you screw one up, you can just revert back to a snapshot or blow it away and start from scratch, and you dont have to worry about downtime on your regular desktop workstation...

---

### Post by adam814 on 2010-01-15
VirtualBox FTW

It's Virtualization software that lets you run multiple operating systems on the same physical machine.  You can set the NICs to an Internal Network so that you can experiment with networking them without risking messing things up for your host.  As a plus when you're learning these things it doesn't hurt to have internet access so you can look things up.

[http://www.virtualbox.org]("http://www.virtualbox.org/")

---

### Post by bcn17 on 2010-01-16
+1 virtual box. I have only used it for running windows, but linux should be no problem. 

And also, there is no reason you have to use the server edition of ubuntu. Server and desktop are the same, except they have some different packages. They can be easily installed though with aptitude. 

I would probably recommend downloading the server edition though. If your running a server there is no reason to have a GUI and it will just eat up resources (that are already limited when implementing a virtual machine). Furthermore, you will learn more using the command line. If you really want to get into networking all the juicy stuff is in editing text files and running some CLI only programs.

---

