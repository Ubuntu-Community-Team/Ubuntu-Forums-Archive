---
title: "COpying files to and fro from host and vm"
date: 2010-06-07
forum: New to Ubuntu
---

### Post by Skslives on 2010-06-07
Hi
guys i am using ubuntu 10.o4 on virtual machine using windows virtual pc 2007
i want to know how to copy file from host os to virtual machine(vm)
in host i am running vista and in vm i am running ubuntu 10.04

i know we can tranfer file using vm additions but that is available with windows only(wht about ubuntu)
and is there any other way??

thanks in advance

---

### Post by HermanAB on 2010-06-07
The absolutely easiest way is with FTP.  On Windows, you can use Filezilla Server and Client.  On Linux, you can use vsftpd and the Nautilus file browser (File, Connect to Server).

---

### Post by gmargo on 2010-06-07
You should be able to run Samba on the Ubuntu side, and the Windows side should be able to see it.  It shouldn't matter which is the host and which is the VM.

---

