---
title: "Ubuntu network profiles for business enviroment"
date: 2014-01-04
forum: Networking &amp; Wireless
---

### Post by stephen14812 on 2014-01-04
Hello all,

I've recently been asked to start a project on converting some work machines into ubuntu from windows to save onmicrosoft licensing   fees. These machines had to have a single sign on which I achieved by setting up a openLDAP server and on the clients making them authenticate against it on the lightdm login screen. As for the home directories, they are stored on the same server by the means of NFS. On the server I have created an export directory to hold the home folders and gave it permissions of 777. At the moment to create a user I go to tne server machine, create a user and manually copy the home directory into the share. With the home path set in open ldap the user signs in with no problem on the client side. BUT all users have access to all other users files. If I change the permission of the home dir it won't let them login. How can I make the permissions work on the nfs server to ensure users data stays private? Also at the moment the client won't boot at all without a network connection... Not even to a local account. Do you have any ideas why this might be? 

Ps: client side it auto mounts on bootup to /home/network

---

