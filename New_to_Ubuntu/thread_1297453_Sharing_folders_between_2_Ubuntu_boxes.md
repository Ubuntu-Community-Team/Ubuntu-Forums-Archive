---
title: "Sharing folders between 2 Ubuntu boxes"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by jeepfreak2002 on 2009-10-21
OK, I feel like a dolt...  My windows machine can see my Ubuntu shared folders, but I can't figure out how to see those shared folders on another Ununtu machine...  help please...

---

### Post by fooman on 2009-10-21
if samba is installed on both machines,  try this (its how i do it):

go to places > connect to server

in the connect to server box...change the service type to "windows share"

in the server space,  type the address of the ubuntu machine you wish to connect to (usually something like 192.168.*.***)

in the folder space,  type the name of the shared folder you want to connect to.

for user,  type in the name of the user on the machine containing the shares.

type in the domain name in the space provided....then click "connect"

you will be prompted for the password of the machine you are connecting to.  then,  hopefully...it will connect.

hope that helps.

---

### Post by jeepfreak2002 on 2009-10-22
ty!!!!!!!!!

Needed user name!!!

---

