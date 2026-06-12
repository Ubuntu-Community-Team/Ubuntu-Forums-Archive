---
title: "Mount Dir on machine A from machine B"
date: 2007-02-18
forum: Networking &amp; Wireless
---

### Post by Dr_Snapid on 2007-02-18
I have 2 machines, both ubuntu.:) 
IP / Distribution
10.0.0.2 / Dapper
10.0.0.137 / Edgy 

I use the Dapper as my workstation. The edgy is (will be) a web development server.

I want to be able to access the web root on the server by mounting it on my workstation.

So imagine if i go /mnt/webserv/www on my workstation, I would see var/www on the server's files.

I only know how to use the mount command to mount local disks:confused: ... can it mount network shares? I need to know how to make the server share the webroot, and make my workstation mount the share, can anybody tell me how?

---

### Post by solar george on 2007-02-18
Use sshfs.

Install a ssh server on your webserver.
Login as your self and give yourself permission to modify the web root.

Connect to the server using ssh and ensure that you can add files to the webroot.

Install sshfs on you workstation.

create a directory to mount the server in you home dir (say yourhome/server)
```
$ sshfs ssh *webserverip*:/var/www *yourhome*/server
```
Enter your password and you will have the server mounted securely in your homedir.

There was a thread somewhere that explains in more detail. If I can find it I will post a link.

---

### Post by Dr_Snapid on 2007-02-18
Cheers, I will give it a try.

---

### Post by Dr_Snapid on 2007-02-18
solar george,

Thanks to your help, I got it going.

You are an asset to these forums!

---

