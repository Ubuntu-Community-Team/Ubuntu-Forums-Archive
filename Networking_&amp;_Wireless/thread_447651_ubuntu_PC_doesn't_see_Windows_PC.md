---
title: "ubuntu PC doesn't see Windows PC"
date: 2007-05-18
forum: Networking &amp; Wireless
---

### Post by The Pinny Parlour on 2007-05-18
How can I see my windows PC through ubuntu?

---

### Post by ntetreau on 2007-05-18
Try to search the forum for samba and windows, they are numerous howto on the subject.  Samba is a communication protocol which is used by most platforms and will let you, after a bit of fiddling, transfer files and share printers between computers on your network.

Nic

---

### Post by The Pinny Parlour on 2007-05-19
Now ubuntu can't see windows.  It bugs me how difficult it is to set up a what should be a simple share network.  Don't get me started about printers working with ubuntu as I have NEVER EVER got a printer to work correctly.    :mad:

---

### Post by ntetreau on 2007-05-20
Sorry to hear about all your problems, I've had the opposite experience, especially with Feisty.  

You can follow this link to add samba/window shares:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)


This guide only uses the command line.  You need to add the users as prescribed in the guide.  However, you can create the shares using the Graphical user interface.  First you need to make sure that the samba packages are installed (this is also covered in the guide).  Normally, you can try to simply go to System> Admin > Shared folders and you shold get a prompt to install the relevant packages.  Then add the folders you would want to share (with samba) without forgetting to unclick the "read-only" option. Then, take the time to configure the General Properties tab hidding behind the shared folders tab.  Make sure you have the same Domain name as the one you use with your windows machine.

Don't forget to add the users and passwords as described in the guide!  You should be able to see and browse the windows share when clicking Places>Network

Nic

---

