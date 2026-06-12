---
title: "nfs entries in fstab file"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by honey_bee on 2010-05-12
Hi,
     I have made a NFS server at my home.The IP address of the server is 192.168.1.10. The folders which i want to share are /music and /home . With manual mounting from client side i use

      mount@192.168.1.10:/music /mydata/music

and i successfully share the files.well each time I have to use mount command.I want that when the client computer which has ip address 192.168.1.30 should automatically load the nfs share from the server.For this I add the lines in fstab

vi /etc/fstab
 reboot the system but it does not get the nfs shares.

my entries in fstab is

**192.168.1.10:music       /mydata/music         nfs        default        0 0**

please please help me.
honey

---

### Post by Kobalt on 2010-05-12
There is a slash missing in your fstab entry : 
> 192.168.1.10:music /mydata/music nfs default 0 0

When it should be : 
```
192.168.1.10:**/**music /mydata/music nfs default 0 0
```

---

### Post by honey_bee on 2010-05-12
thanks for the help. well these is a question not related to Linux but about my account. please can u guide me that how can I see alll my previous post  which i have  submit.
I have checked my user cp but does't find it.

---

### Post by Kobalt on 2010-05-12
Click on "Search" and "Find all your posts" in the upper bar of this page.

---

### Post by cbecker78 on 2010-05-12
> **honey_bee said:**
> thanks for the help. well these is a question not related to Linux but about my account. please can u guide me that how can I see alll my previous post  which i have  submit.
I have checked my user cp but does't find it.

Or click on your username when logged in and click on "show all statistics" on the right hand side of the screen.  An option will come to display all threads you have started or display all of your posts.

---

