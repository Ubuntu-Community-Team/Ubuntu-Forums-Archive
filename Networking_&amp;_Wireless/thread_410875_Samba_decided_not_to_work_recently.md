---
title: "Samba decided not to work recently"
date: 2007-04-16
forum: Networking &amp; Wireless
---

### Post by DarKmaN-07 on 2007-04-16
I have access to my local machines media files through the windows workgroup network. I'm using Ubuntu edgy and XP pro on the other mahines. Recently I changed the server's computer name and now I can't access the network group all together. I had a short cut on my Ubnuntu desktop for one of the machines in the XP group and I could access that but not the actual workgroup to check the other machines status. 

Whats happened to the access?
The workgroup still has the same name btw. 
I can still RDC into the XP machines. 

Maybe there is a setting that I've over looked in the XP machines ?

---

### Post by DarKmaN-07 on 2007-04-16
Aha, I fixed it. Not how I wanted, but I had to change the workgroups name in all the machines and the smb.conf file. 
I got the result i was looking for and now I can access all my media files (almost 1tb)
Ya can't lose that kinda freedom!

---

