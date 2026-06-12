---
title: "File browsing another Ubuntu computer"
date: 2007-07-12
forum: Networking &amp; Wireless
---

### Post by theDentist on 2007-07-12
Can anyone tell me how to browse the directories from one Ubuntu computer to another one  on my LAN at home. Selecting the "Network Servers" from the "Places" menu only enables you to browse the Windows network, not a Linux network.  How can I achieve the same result with another Ubuntu computer.

---

### Post by dannyboy79 on 2007-07-12
well you need to install samba on the computers you want to be able to browse. When it says Windows Network, it's not really only for windows networks, it merely stating that it's browsing using the smb protocol which was reverse engineering by developers to be just like windows NT networking. there are literally tons of guides on samba, check them out. OR, you can use NFS if you're trying to view the files from another Linux OS. Good luck

---

### Post by theDentist on 2007-07-12
Thanks I'll give it a try   :(

---

### Post by theDentist on 2007-07-12
For all who are interested I managed to get samba working between two Ubuntu computers for file browsing over a LAN. I ran into a problem with the smb.conf file for samba. In the Share Definitions section I followed advice given in another thread. Un- comment the following lines

  [homes]
  comment = Home Directories
  browseable = yes   ( I changed this from no)

It didn't work, so I entered an extra line  

   path = /home/peter                 (my user name is peter)

and changed the [homes] to:
 
   [peter]

so the finished lines were:

[peter]
  comment = Home Directories
  path = /home/peter
   browseable = yes

And it works !!!!    :)

---

