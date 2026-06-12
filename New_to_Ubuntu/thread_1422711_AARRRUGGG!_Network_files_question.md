---
title: "AARRRUGGG! Network files question"
date: 2010-03-05
forum: New to Ubuntu
---

### Post by Don1500 on 2010-03-05
I have searched everywhere but I always run into the same problem. I want to set up from an Ubuntu (my desktop) to an ubuntu (my laptop) but every file share how to I find sets up from Windows to Ubuntu or from Ubuntu to Windows. I am able to get to my laptop from my desktop but not from the laptop to the desktop whe I try to load the same thing in "Places>Connect to server" as I did on the desktop all I get is "Can Not Display Location "smb://192.168.2.3"

The address for my laptop is 192.168.2.2
for my desktop it is 192.168.2.3

I believe I set every other paramiter exactly the same.

All I want to do is Print from my Ubuntu running laptop to my printer located on my Ubuntu running Desktop. There is something simple I am missing and I just can't find it.

---

### Post by Iowan on 2010-03-05
Did you install the (Samba) server on the desktop?  
Another option for Linux-Linux is [NFS]("http://ubuntuforums.org/showthread.php?t=249889").
[Another]("http://ubuntuforums.org/showthread.php?t=1169149") How-To that might help.

---

### Post by Don1500 on 2010-03-05
> **Iowan said:**
> Did you install the (Samba) server on the desktop?  
Another option for Linux-Linux is [NFS]("http://ubuntuforums.org/showthread.php?t=249889").
[Another]("http://ubuntuforums.org/showthread.php?t=1169149") How-To that might help.

actually when I entered samba into the terminal on both machines it was not loaded. I have now loaded both and still get the same thing.

In the desktop I can read the files on the laptop

on the laptop the desktop does not exist.

If I am ever going to find the printer connected to the desktop, using the laptop, I will need to see the desktop from the laptop.


The complete error I get is: [COLOR="Red"]Cannot display location "smb://192.168.2.3"    Failed to retrieve share list from server.[/COLOR]

---

### Post by baddnady23 on 2010-03-05
you could also set up SSH, by going to  

```
Places->Connect to Server...
```

and under the "Server" field, type:

```
host_username@host_IP
```

replacing host_username with the user of the machine your connecting to and host_IP with the local IP address of the machine you are trying to connect to.  It will then prompt you for the password of the machine.  For example, I would type something along the lines of jimbob@192.168.1.70.  Using this method correctly will then place a link to the file system of the machine you are connecting to on your desktop and should let you browse it like any other folder.

---

### Post by Don1500 on 2010-03-05
> **baddnady23 said:**
> you could also set up SSH, by going to  

```
Places->Connect to Server...
```

and under the "Server" field, type:

```
host_username@host_IP
```

replacing host_username with the user of the machine your connecting to and host_IP with the local IP address of the machine you are trying to connect to.  It will then prompt you for the password of the machine.  For example, I would type something along the lines of jimbob@192.168.1.70.  Using this method correctly will then place a link to the file system of the machine you are connecting to on your desktop and should let you browse it like any other folder.

Yes, and I get :[COLOR="Magenta"]Cannot display location "smb://192.168.2.3" Failed to retrieve share list from server.[/COLOR]
My original post.
It's not how to set up the printer, it's how to make the connection. I have activated samba 16 different ways, still the Desktop is invisible to the laptop. But I can see the laptop just fine from the desktop. (BTW The desktop is a hard wire connection, the laptop is wireless)

---

### Post by Don1500 on 2010-03-05
Now I am really flumixed! It doesn't work anywhere. I get the same error message from both sides. And I don't know what I did.

---

### Post by Don1500 on 2010-03-06
Solved. Turn off BOTH firewalls:
in terminal:
```
sudo UFW disable
```
do that to all your machines.

---

### Post by Don1500 on 2010-03-06
bump

---

