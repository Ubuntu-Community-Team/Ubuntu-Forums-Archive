---
title: "No-ip on ubuntu"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by lukanikos on 2007-07-10
How can I install the no-ip software on my ubuntu?

---

### Post by yota on 2007-07-10
Hi,
you can download the software at:
[http://www.no-ip.com/downloads.php?page=linux](http://www.no-ip.com/downloads.php?page=linux)

Extract the archive to the folder you like, you will find a README file inside that explains everything.
Basically you should have to copy the binaries/noip2-linux command to /usr/local/bin, and then you can invoke it from anywhere.

Hope this helps.

---

### Post by lukanikos on 2007-07-10
Trying to copy the file you said : binaries/noip2-linux command to /usr/local/bin

and I get this message



```
Error while copying to "/usr/local/bin".
You do not have permissions to write to this folder.
```

---

### Post by splintercellguy on 2007-07-10
Run the installer with sudo :).

---

### Post by lukanikos on 2007-07-10
can you give me the whole command?

---

### Post by yota on 2007-07-10
Sure!
```

sudo cp noip2-linux /usr/local/bin

```
This assumes that you are in the binaries folder, otherwise adapt the path to noip2-linux.

Please note that this is only a (suggested) commodity, you are not forced to copy the command in /usr/local/bin. If you want you can place the command everywhere you like, go there and launch it with
```

./noip2-linux

```
Please note also that you can do the copy with gui using a file manager with elevated privileges: press alt+F2 and type 'gksudo nautilus'; this will open a file manager that let you do any operation on the filesystem.

---

### Post by az on 2007-07-10
sudo apt-get install no-ip

[http://packages.ubuntu.com/feisty/net/no-ip](http://packages.ubuntu.com/feisty/net/no-ip)

---

### Post by yota on 2007-07-10
> **az said:**
> sudo apt-get install no-ip

[http://packages.ubuntu.com/feisty/net/no-ip](http://packages.ubuntu.com/feisty/net/no-ip)

Whoops! Didn't know it was on the repositories... :oops:

---

### Post by lukanikos on 2007-07-10
```
lukanikos@lukanikos-desktop:~$ sudo cp noip2-linux /usr/local/bin
Password:
cp: cannot stat `noip2-linux': No such file or directory
lukanikos@lukanikos-desktop:~$ ./noip2-linux
bash: ./noip2-linux: No such file or directory
lukanikos@lukanikos-desktop:~$ sudo apt-get install no-ip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  no-ip
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.4kB of archives.
After unpacking 135kB of additional disk space will be used.
Get:1 http://gr.archive.ubuntu.com feisty/universe no-ip 2.1.3-3build1 [21.4kB]
Fetched 21.4kB in 0s (105kB/s)
Selecting previously deselected package no-ip.
(Reading database ... 108211 files and directories currently installed.)
Unpacking no-ip (from .../no-ip_2.1.3-3build1_i386.deb) ...
Setting up no-ip (2.1.3-3build1) ...
Starting dynamic address update: Can't locate configuration file /etc/no-ip.conf. (Try -c). Ending!

no-ip.

lukanikos@lukanikos-desktop:~$ 
```

---

### Post by az on 2007-07-10
cat usr/share/doc/no-ip/README.Debian

man no-ip

I can't help you out any more that that since I don't have it installed and am not at home...

---

### Post by halocog on 2008-07-11
> **lukanikos said:**
> ```
lukanikos@lukanikos-desktop:~$ sudo cp noip2-linux /usr/local/bin
Password:
cp: cannot stat `noip2-linux': No such file or directory
lukanikos@lukanikos-desktop:~$ ./noip2-linux
bash: ./noip2-linux: No such file or directory
lukanikos@lukanikos-desktop:~$ sudo apt-get install no-ip
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  no-ip
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 21.4kB of archives.
After unpacking 135kB of additional disk space will be used.
Get:1 http://gr.archive.ubuntu.com feisty/universe no-ip 2.1.3-3build1 [21.4kB]
Fetched 21.4kB in 0s (105kB/s)
Selecting previously deselected package no-ip.
(Reading database ... 108211 files and directories currently installed.)
Unpacking no-ip (from .../no-ip_2.1.3-3build1_i386.deb) ...
Setting up no-ip (2.1.3-3build1) ...
Starting dynamic address update: Can't locate configuration file /etc/no-ip.conf. (Try -c). Ending!

no-ip.

lukanikos@lukanikos-desktop:~$ 
```

i am getting the exact same problem, can anyone help?

---

### Post by hyper_ch on 2008-07-11
```

sudo apt-get install noip2

```

no need to manually install.

---

