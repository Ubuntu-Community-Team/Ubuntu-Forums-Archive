---
title: "Update Manager Fails To Install"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by johngodi on 2009-05-19
Hello, 
I'm new to Linux so I just wanted to get that out. Recently did a clean install of 
Ubuntu 9.04 and when I select <System> <Administration> <Update Manager > 
Shows the available updates and when I go to install the following error is generated. 

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.

Anyone out there know how what steps I need to do to fix this? 

Thanks in advance!

---

### Post by kostkon on 2009-05-19
Open a terminal (Applications &#8594; Accessories &#8594; Terminal) and give:
```
sudo dpkg --configure -a
```
it will ask for a password, give yours.
Then give
```
sudo apt-get update
```
and you should be fine. You can then open the Update Manager to apply any updates that you may have.

---

### Post by Cheesemill on 2009-05-19
> **johngodi said:**
> E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report.

You just need to do what it tells you, open a terminal and type
```
sudo dpkg --configure -a
```

Cheesemill

---

### Post by johngodi on 2009-05-19
Thanks for the quick response, completed steps outlined and get the following code
back when logged in as ubuntu or root 

ubuntu@ubuntu:~$ su root
Password: 
root@ubuntu:/home/ubuntu# sudo dpkg --configure -a 
Setting up libc6 (2.9-4ubuntu6) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135
root@ubuntu:/home/ubuntu# su root
root@ubuntu:/home/ubuntu# sudo dpkg --configure -a 
Setting up libc6 (2.9-4ubuntu6) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135
root@ubuntu:/home/ubuntu#

---

### Post by johngodi on 2009-05-19
Any ideas how to proceed?

---

### Post by johngodi on 2009-05-19
Anyone out their that knows what the code returned means?

---

### Post by Zoowey on 2009-05-20
> **johngodi said:**
> Thanks for the quick response, completed steps outlined and get the following code
back when logged in as ubuntu or root 

ubuntu@ubuntu:~$ su root
Password: 
root@ubuntu:/home/ubuntu# sudo dpkg --configure -a 
Setting up libc6 (2.9-4ubuntu6) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135
root@ubuntu:/home/ubuntu# su root
root@ubuntu:/home/ubuntu# sudo dpkg --configure -a 
Setting up libc6 (2.9-4ubuntu6) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Bus error (core dumped)
dpkg: subprocess post-installation script returned error exit status 135
root@ubuntu:/home/ubuntu#

Restart your computer.

---

### Post by oOarthurOo on 2009-05-20
Who told you to write "su root"? That's not correct.

---

