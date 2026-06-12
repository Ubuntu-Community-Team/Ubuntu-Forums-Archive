---
title: "Connecting to Windows shared files with Samba"
date: 2007-03-03
forum: Networking &amp; Wireless
---

### Post by jonlemur on 2007-03-03
Hello all,

I"m at a University and I'm trying to connect to other people's shared files on the network.  I have xsmbrowser, and it's able to find all of the computers on the network, but when I try to click on one, I get the following message: "No Shares Offered," even though I know they do have a share available.  Is there something I need to set up in order to see their shares or something else I need to install?

I'm also trying to connect to a University supplied storage server that I would access from Windows by typing in the Run window "\\storagesrv1\" or "//storagesrv1/" (I can't remember which way Windows requires it).  Is there a way to do the same in Linux from the command line with samba?  

Thanks for any help you may be able to provide, and I'm happy to provide any more information you may require in answering these questions.

---

### Post by jonlemur on 2007-03-13
Whoa... There should be a sign there.  "Caution: BUMP ahead."

---

### Post by jonlemur on 2007-03-15
Anyone?

---

### Post by techboyjk on 2007-03-16
> **jonlemur said:**
> Hello all,

I"m at a University and I'm trying to connect to other people's shared files on the network.  I have xsmbrowser, and it's able to find all of the computers on the network, but when I try to click on one, I get the following message: "No Shares Offered," even though I know they do have a share available.  Is there something I need to set up in order to see their shares or something else I need to install?

I'm also trying to connect to a University supplied storage server that I would access from Windows by typing in the Run window "\\storagesrv1\" or "//storagesrv1/" (I can't remember which way Windows requires it).  Is there a way to do the same in Linux from the command line with samba?  

Thanks for any help you may be able to provide, and I'm happy to provide any more information you may require in answering these questions.

are these shares on a linux machine or windows machine?

---

### Post by jonlemur on 2007-03-16
They're on each students' personal Windows machines.  I figured out how to connect to storagesrv1 (one of the original problems) by going to "Connect to Server" in Places, and I can connect to a students shared file on Windows if I know the IP address, by using Connect to Server again.  But I don't know the IP addresses for most of the ones that I would like to be able to access.  If I run xsmbrowser, I can see all of the students shared files (or at least see their computers), but when I try to connect to one that I know is offered, it tells me that it can't find the share.

---

