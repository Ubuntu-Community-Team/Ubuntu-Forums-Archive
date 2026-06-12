---
title: "cifs mount suddenly no longer works"
date: 2023-09-01
forum: Networking &amp; Wireless
---

### Post by velsd on 2023-09-01
hello

I have been using this command for years to connect to my old Lacie Cloudbox NAS: 

```
sudo mount -t cifs //192.168.1.16/danny /media/cloudbox -o username=danny,password=xxx,vers=1.0
```

and today it suddenly stopped working:

```
mount.cifs kernel mount options: ip=192.168.1.16,unc=\\192.168.1.16\danny,vers=1.0,user=danny,pass=********
mount error(5): Input/output error
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) and kernel log messages (dmesg)

```

is it possible that a recent update in for example cifs-utils would have caused this?

```
cifs-utils is already the newest version (2:6.14-1ubuntu0.1).
```

if yes, is there a workaround, or would this be a recent bug?

I can access the storage device through the browser interface, and I can see that for instance Volumio can read from this NAS...

I have tried other mount options, 
```
-o rw,
 -o sec=ntlm
 -o nounix,sec=ntlm
-o sec=ntlmssp
```
but none that I know of seem to solve this issue.

I can also see a very similar remark here:
[https://superuser.com/questions/1806285/ubuntu-22-04-3-lts-cifs-mount-failed-w-return-error-5](https://superuser.com/questions/1806285/ubuntu-22-04-3-lts-cifs-mount-failed-w-return-error-5)

regards, Danny.

---

### Post by velsd on 2023-09-02
-

---

### Post by Morbius1 on 2023-09-03
Change this:
> sudo mount -t cifs //192.168.1.16/danny /media/cloudbox -o username=danny,password=xxx,vers=1.0
To this:
> sudo mount -t cifs //192.168.1.16/danny /media/cloudbox -o username=danny,password=xxx,vers=1.0**[COLOR="#FF0000"],nodfs[/COLOR]**
Better?

---

### Post by velsd on 2023-09-04
yes, thanks!!! that works! can you explain why this is now required?

---

### Post by Morbius1 on 2023-09-04
> **velsd said:**
> yes, thanks!!! that works! can you explain why this is now required?
To be painfully honest no I cannot.

I started seeing reports of this problem when people updated to new Linux kernels on the client machine and only if the server was limited to using SMBv1 only.

CIFS isn't controlled by samba on the client it's controlled by the Linux Kernel itself. The Kernel changelogs might as well be written in Klingon but I saw no reference to SMBv1 but there were many references to dfs.

I'm not the shiniest apple in the bushel but I did know there was a parameter in the man pages for mount.cifs that disabled dfs on the client side ( nodfs ) so I tried it and it worked against a SMBv1 only server.

If you try to connect to a modern SMB / SMBx / Samba server like Windows, MacOS, or Ubuntu it's not required. It's only these old systems that use SMBv1 only.

---

### Post by snorlax212 on 2023-09-04
> **Morbius1 said:**
> Change this:

To this:

Better?

Thank you! Had same issue with SMBv1 after kernel update.

---

### Post by velsd on 2023-09-05
you are one of the shiniest apples that I know !!!

---

### Post by bluesmax83 on 2023-09-18
Thank you very much... mount gave me error 22 since august when ubuntu update the kernel and your solution worked like a charm. I tried every solution found around but nothing worked (exept yours of course). I was going crazy. hahaha

---

