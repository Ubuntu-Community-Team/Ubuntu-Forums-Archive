---
title: "Sharing Files between Ubuntu and Fedora"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by bbuy2k on 2010-08-14
Hello family,

I've got vmware running with Ubuntu 10.4 and Fedora 13 simultaneously. I would like to transfer a file from one to the other, is it possible to use gftp? If not i'm open for suggestions.

Thanks

---

### Post by JustinR on 2010-08-14
I thought there was a software like VMWare tools that allowed you to do this, like VirtualBox Guest Additions in VirtualBox.

---

### Post by bbuy2k on 2010-08-14
actually there is a tool for vmware called VM Disk Mount, I'll try it out, but there is another way I found out from a Fedora guru. You can transfer files via scp (secure copy) here is the command in root or just sudo "scp file_name ipaddress_of_destination:destination_folder" without the quotes. so for example if you want to transfer a file called quiz.htm to the destination you would type. " sudo scp quiz.htm 192.168.x.x:Desktop" and presto, there it is.

I hope this helps out anyone who has the same issue I had.

Thanks.

---

