---
title: "How Do I delete a Network I created on my laptop?"
date: 2016-10-08
forum: Networking &amp; Wireless
---

### Post by baconchicken42 on 2016-10-08
I recently noticed that there was an option to "create new network" in the networking tab on ubuntu. I decided to try it out, but ultimately deemed it unnecessary as I already have a network. My question is, Is there a way to remove it entirely (not just remove it from my connections list, but delete it so that it's gone forever)? I would really appreciate any help on the subject.

---

### Post by #&amp;thj^% on 2016-10-08
Have you tried to delete the files in the directory /etc/NetworkManager/system-connections/ ?

You should have 1 file for every net you have tried to connect, open a terminal and use the commands:

```
sudo ls -l /etc/NetworkManager/system-connections/
```

To list all the files, after you have found the network that you want to delete, remove them with the command:

```
sudo rm /etc/NetworkManager/system-connections/NETWORK_NAME
```
Or navigate to it with your File Manager as Admin...and Delete the one you want to remove.

---

### Post by Hadaka on 2016-10-08
Hi try this..
 #1. Click the wifi signal icon
 #2. Click Edit Connections
 #3. Click Wireless
 #4. Click the connection to delete
 #5. Click Delete

---

### Post by baconchicken42 on 2016-10-09
That seems to have done the trick. Thanks!

---

### Post by Hadaka on 2016-10-09
Glad that worked for you ! and 
thank you for marking your thread
Solved.

---

