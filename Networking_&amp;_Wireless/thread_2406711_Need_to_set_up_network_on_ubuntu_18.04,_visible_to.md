---
title: "Need to set up network on ubuntu 18.04, visible to windows laptop"
date: 2018-11-24
forum: Networking &amp; Wireless
---

### Post by aramchekian on 2018-11-24
I have looked into this extensively and not been able to fix the problem. Basically, I need to be able to print to a printer connected by usb to a linux desktop (ubuntu 18.04) from a windows laptop in the same house. I understand there is a program called Samba that may work. I have found resources online for using Samba and other methods, but the instructions are either too vague or too technical for me to follow.

[http://paste.ubuntu.com/p/c5CC9hJ8Dt/](http://paste.ubuntu.com/p/c5CC9hJ8Dt/)

---

### Post by TheFu on 2018-11-25
Unix-like OSes follow long-time standards for networking.  If you want a Windows PC to have named access to another system, make an entry in the /etc/hosts file on Windows with the IP and hostname you want to use.  Obviously, the Unix machine should have a static IP for this to work.  I don't recall exactly where Windows keeps that file, but there are hundreds, if not thousands, of how-to guides.  I think it is somewhere under /windows/system32/drivers/etc/  but don't quote me on that.

Samba isn't necessary and it a complex solution best used in corporate environments.  If the printer supports IPP, then just install and configure CUPS on the Ubuntu machine, then make certain CUPs service is available on the LAN for access by Windows.
[https://help.ubuntu.com/lts/serverguide/cups.html.en](https://help.ubuntu.com/lts/serverguide/cups.html.en)

And I should say this - I don't have 18.04, too new for me, but I would be surprised if CUPS wasn't the same.

---

### Post by aramchekian on 2018-11-26
Thanks so much for your reply.
> Obviously, the Unix machine should have a static IP for this to work.
I  have no idea what a static address is, or how to go about getting one. I'm sure  it's not rocket science but, to someone with no knowledge of math, 2+2=4  is meaningless... This is probably the best way to describe my  knowledge of networking. It's not that I'm coming up with 2+2=3 instead.  My understanding is not even that sophisticated. Rather, I'm still  trying to figure out what "2" means. If someone could walk me through  it, step by step, I think probably I would be able to get this working  though.

---

### Post by TheFu on 2018-11-26
Sorry, step by step things are beyond my ability, but there are many how-to guides. Google should find one for 18.04 easily.  Nobody here can tell you exactly what to type, since each of our situations are a little different. Following a reputable guide is probably best.

Be certain you can put everything back, if anything goes wrong.  Take sufficient notes along the way for exactly what you do so it can be undone.

This is definitely NOT rocket science.

---

### Post by 1clue on 2018-11-26
For Samba, the complicated part is for domain authentication/windows domain controller. Don't go there. If your guide gets into that then you have the wrong guide for printing.

---

### Post by aramchekian on 2018-11-28
> Be certain you can put everything back, if anything goes wrong.  Take  sufficient notes along the way for exactly what you do so it can be  undone.

This tip is extremely helpful. I have spent many hours reinstalling Ubuntu and copy/pasting commands from my notes only to mess something up again and start over. The most recent reason for this has been my failure to get dejadup or backintime to work correctly, particularly when it comes to unwanted installed programs, printers, and configurations still existing even after I restore from a backup. Fortunately, I have been experimenting with timeshift and it seems to work well for taking snapshots of the entire system. My latest problem has to do with saving a copy of a snapshot from timeshift to an external drive for later use, in case something happens to the original. I have posted yet another thread on this. I am probably going to postpone this project until I get my ducks in a row, but I will be checking this thread for replies regularly. Thanks again, you guys are amazing.

---

