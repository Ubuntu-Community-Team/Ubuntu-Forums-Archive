---
title: "Accessing Windows Home Server in Terminal Window"
date: 2011-01-17
forum: New to Ubuntu
---

### Post by MontrealMike on 2011-01-17
Background:
I have successfully installed Ubuntu 10.10 as a dual boot system with Windows 7.  It found my printer, network (wired and wireless) automatically.  In Nautilus I can navigate to both my Windows 7 partitions as well as to my Home Server system data.

The problem:
I am trying to write a script to synchronize my Ubuntu files to my Home Server.  I do not know how to find the path name to my Home Server file system.  Can any one steer me to a good reference or, does Nautilus have buried in one of its menus or configuration files the correct path name?

Thank you

---

### Post by cariboo on 2011-01-17
Usually if you open nautilus, and press Ctrl-L you will get an address box, in there type:

```
smb://servername
```

you should get a listing of all your shared directories

---

### Post by MontrealMike on 2011-01-17
Thanks Cariboo,

That worked.  I can find smb://MBASERVER in Nautilus.  Now if I try the following terminal command:

ls -l smb://MBASERVER 


I get 
michael@Michael-PC-Ubuntu:~$ ls -l smb://MBASERVER
ls: cannot access smb://MBASERVER: No such file or directory

I suspect I am missing something simple, any ideas?

---

