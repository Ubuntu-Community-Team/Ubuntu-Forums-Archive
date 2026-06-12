---
title: "Can this be done -Join windows domain"
date: 2007-09-07
forum: Networking &amp; Wireless
---

### Post by Jay_Rock on 2007-09-07
I have been using Ubuntu 7.04 for about 5 weeks and I love it but it would be nice to be able to join it to my Windows 2003 domain. 

I was able to figure out (Places,Connect to Server) how to connect to my server so I could share files. 
My server see it as if it were in a workgroup, putting it under MSHOME. 


Please help their has got to be a way to do this.

---

### Post by Megaqwerty on 2007-09-07
If I understand your question correctly, you want to know how to browse your network. **Places>Network** will display the windows shares on your network. 
If you were asking how to change your domain, I believe it can be done in **System>Administration>Network>General**. I know for sure you can do it by editing **/etc/samba/smb.conf** and changing: ```
workgroup = **workgroupname**
```

---

### Post by Jay_Rock on 2007-09-07
[http://www.youtube.com/watch?v=Ad17kma8rNM]("http://www.youtube.com/watch?v=Ad17kma8rNM")

This is what I needed.

---

