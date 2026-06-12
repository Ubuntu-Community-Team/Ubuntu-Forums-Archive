---
title: "Remote directory write permissions"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by dougie_boy on 2009-11-01
I am in the process of setting up a LAMP webserver with a wordpress site on it.

all is going okay at the moment, i have access from the net to view the page, and i have local access on the host machine. i am trying to use a remote blogging app but cannot create files and folders from it. how can i set up ubuntu to allow remote file creation/uploads?

what ports do i need to open?
do i also need an FTP sever on the machine hosting wordpress?

---

### Post by theozzlives on 2009-11-01
> **dougie_boy said:**
> I am in the process of setting up a LAMP webserver with a wordpress site on it.

all is going okay at the moment, i have access from the net to view the page, and i have local access on the host machine. i am trying to use a remote blogging app but cannot create files and folders from it. how can i set up ubuntu to allow remote file creation/uploads?

what ports do i need to open?
do i also need an FTP sever on the machine hosting wordpress?

```
cd /var
sudo chmod 777 www -R
```

Note that's an R not an r.

---

### Post by dougie_boy on 2009-11-01
cheers theozzlives,

Not to sound ungrateful but what does this code do?

---

### Post by ZankerH on 2009-11-01
You shouldn't need an FTP server if you've already got httpd, but you might want to check that with the provider of whatever software you're using for your blog.

---

### Post by dougie_boy on 2009-11-02
bump*

---

### Post by NickJones on 2009-11-02
> **theozzlives said:**
> ```
cd /var
sudo chmod 777 www -R
```Note that's an R not an r.
CD /Var - Changes the directory to "Var"
Sudo runs as Root (Admin)
chmod - Changes Mode
777 - Read & Write permission are defined by numbers, 777 allows everyone to read, write & execute.
www - The file/folder you are setting the permission for

Hope I helped,
Nick

---

### Post by dougie_boy on 2009-11-02
Thanks Nic.

---

