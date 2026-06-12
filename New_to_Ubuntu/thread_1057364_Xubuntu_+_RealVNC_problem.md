---
title: "Xubuntu + RealVNC problem"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by 4JOKE4 on 2009-02-01
I am new in Linux and I need to install RealVNC-server (I need exactly this remote desktop application).

I downloaded file ***.deb and used command:
**sudo dpkg -i ***.deb**

It successfuly installed RealVNC.
Then I tryed commands:
**sudo vncpasswd**

And I typed 2times password i.e. "123" .
After that I run VNC server:
**sudo vncserver -display :1**

It showed me message, that VNC server is running, but when I try to connect from another PC with Windows (which is on the same LAN), then I need to type username+password.
Password was setted by vncpasswd.
But how I can set username? when I tryed to type username of linux user, it said to me that username or password is incorrect.

Can somebody help me how to set username+password for RealVNC server in Linux?

Thnx.

---

### Post by lykwydchykyn on 2009-02-02
when you run "vncserver", it creates a new desktop as the user who is running the command.  You would log in as that user.

The problem is, you ran "sudo vncserver :1", which means root owns that desktop.  Since you cannot log in as root directly in Ubuntu, you won't be able to log in to that desktop.

vncpasswd is for creating a password file for when you want to set up X to run vnc as a module.   If you want to manually launch vnc servers as a user, you won't need that.

What precisely are you trying to do, and are you following some howto?  Because there are several ways to run VNC on Linux and what you need to do depends on some of the finer details of what you want to accomplish.

---

### Post by 4JOKE4 on 2009-02-02
I need, that when I start server, It automatically start RealVNC and I am able to control Linux server from my PC with Windows.

And you are right. I have still some problems with sudo/permissions/chmod ...etc because I am no skilled in Linux.

And when I run vncserver without sudo, it says something as "permissions denied".

Any idea?!

---

### Post by lykwydchykyn on 2009-02-02
Do you want it to access your current running desktop, or to launch a new desktop session?

This will give you the former, but it doesn't use RealVNC:
[http://ubuntuforums.org/showthread.php?t=279069](http://ubuntuforums.org/showthread.php?t=279069)

Why in particular do you need to use RealVNC?

VNC works differently on Linux than it does on windows, because Linux is a multi-user environment (that is, you can have multiple users logged on simultaneously, and the same user can be logged in to multiple sessions simultaneously).  

I'm not sure why you're getting a permissions issue running vncserver without sudo.  That shouldn't be.

---

### Post by 4JOKE4 on 2009-02-02
I have old PC, which I use as Linux server at home. And everytime when I turn on it, I need to control it by remote desktop. So there will be VNC server on my old pc and on my new PC is Windows with VNC viewer.

Why I want to use RealVNC? Because:
1. It has file-transfer feature
2. When I tryed to install other vnc softwares, I was unsuccessfuly .

I don't know too, why I have "permission error". I can find out how that message exactly look like, if it can help you to solve my problem..

And thanks for guide-link, I will try to use something from it...

---

### Post by lykwydchykyn on 2009-02-02
Yes, please paste the output from running "vncserver" as a normal user.  Don't put any arguments after it, just "vncserver".

---

### Post by 4JOKE4 on 2009-02-02
> **lykwydchykyn said:**
> Yes, please paste the output from running "vncserver" as a normal user.  Don't put any arguments after it, just "vncserver".

Generating primes:
p: ....
q: .......
fopen: Permission denied (13)
Error: Can't create /home/misox/.vnc/misox-desktop:1.log: Permission denied (13)

---

### Post by lykwydchykyn on 2009-02-02
> **4JOKE4 said:**
> Generating primes:
p: ....
q: .......
fopen: Permission denied (13)
Error: Can't create /home/misox/.vnc/misox-desktop:1.log: Permission denied (13)

I'm wondering if your sudo command created that file and made it owned by root.  See if the file mentioned exists, and what permissions are on it.

---

### Post by 4JOKE4 on 2009-02-02
So I should change permissions of these files, isn't it ?

-rw------- 1 root root  4774 2009-02-02 18:08 misox-desktop:1.log
-rw-r--r-- 1 root root     5 2009-02-02 18:06 misox-desktop:1.pid
-rw------- 1 root root 14254 2009-02-01 13:37 misox-desktop:2.log
-rw------- 1 root root     8 2009-02-01 13:09 passwd
-rw------- 1 root root  2824 2009-02-01 11:01 private.key
-rwxr-xr-x 1 root root   425 2009-02-01 11:50 xstartup

...but last time when I tryed to change permissions by command **chmod**, it didn't ended very well and I rather reinstalled xubuntu...

...Could you help me with that?

---

### Post by lykwydchykyn on 2009-02-02
At this point, the simplest thing to do is probably just this:
```

sudo rm -Rf .vnc

```
You may want to do that from a graphical filebrowser, as mistyping something in that command could be fatal.  Just do:
```

gksu thunar

```
To bring up thunar as root, turn on "view hidden files" and delete the .vnc folder from your home directory.

You shouldn't have anything important in there at this point.

---

### Post by 4JOKE4 on 2009-02-02
great man!!! Now it's working ! Thank you very much :)
Now I have to only set to run it automatically when xubuntu start up.

---

