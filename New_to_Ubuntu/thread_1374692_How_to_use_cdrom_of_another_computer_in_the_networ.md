---
title: "How to use cdrom of another computer in the network from server PC"
date: 2010-01-07
forum: New to Ubuntu
---

### Post by Ashishkhandelwal on 2010-01-07
I am sitting in front of a suse server computer and i have to install php-mysql package in this server.When i am doing that through yast it is asking for the cd of suse.I have that cd but i cannot connect the cdrom to that server.The cdrom is connected to another PC which i can also access.Is there anyway to install that package using the cdrom connected to other PC.

---

### Post by benfindlay on 2010-01-07
There used to be a similar issue to this in ubuntu. It was caused by the install CD being treated as a repository for certain packages. Try lokking at yast's repository list, and you may find a CD drive listed there. If it is, remove it from the list and refresh the package list. That way it will not ask for th3e CD and will instead download the package from the internet, and I think that will be (likely) much easier to accomplish than getting a CD shared across the network

Hope this helps

Ben

---

