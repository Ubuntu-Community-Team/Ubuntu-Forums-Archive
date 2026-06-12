---
title: "installNC.sh problem"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by flylehe on 2009-05-14
Hi, 
I am trying to use some remote access software provided by my school. However while connecting I got this "installNC.sh" window popped out, saying:

"/home/lehe/.juniper_networks/network_connect/installNC.sh: 9: cannot open 1: No such file
/home/lehe/.juniper_networks/network_connect/installNC.sh: 9: 1: not found
service needs to be installed for the first time
Please enter the root/su password
Password:"

I thought it was asking for my root password, but that failed.
Can someone tell me what's going on and how to do?
Thanks and regards!

---

### Post by achase79 on 2009-05-14
ubuntu uses sudo instead of the original root user account.  This program however looks for the root user.  You will have to go to settings -> administration -> users and groups, unlock and view all users, select root and change the password to a very secure password.  Then use that password when installing the software.

---

