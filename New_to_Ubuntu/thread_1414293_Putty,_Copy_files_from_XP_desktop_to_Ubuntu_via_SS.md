---
title: "Putty, Copy files from XP desktop to Ubuntu via SSH"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by Swerve1000 on 2010-02-23
Hi,

I have freshly installed Ubuntu 9.10 Server Edition on a machine and have logged into it via SSH from a windows machine using Putty.

I'd like to copy some files from C:\ForServer\ folder to my home folder in my ubuntu server machine.

I have found the terminal command 'copy':

> cp -R **/WindowsFolder/** **/pathtodestination/**

How do I change **/WindowsFolder/** to represent my C:\ForServer\ folder, and change **/pathtodestination** to represent my home folder in 9.10?

Thanks for any help with this,

really appreciate it!

---

### Post by San_SS! on 2010-02-23
You can't do that from a shell running in the ubuntu server. For that you should use the pscp command from the putty package, you can download it from [http://www.chiark.greenend.org.uk/~sgtatham/putty/download.html]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/download.html")

To use it:
pscp.exe -r <from path> <user>@<ubuntu ipaddress>:<path to destination>

Hope this is helpful for you

---

### Post by pirateghost on 2010-02-23
[http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)
for all your ssh file copy needs

---

### Post by ratcheer on 2010-02-23
> **pirateghost said:**
> [http://winscp.net/eng/index.php](http://winscp.net/eng/index.php)
for all your ssh file copy needs

+1

Tim

---

### Post by juanoleso on 2010-02-23
I use [[color="blue"]filezilla[/color]]("http://filezilla-project.org/").

---

