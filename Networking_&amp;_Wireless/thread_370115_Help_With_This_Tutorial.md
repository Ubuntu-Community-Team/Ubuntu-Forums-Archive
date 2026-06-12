---
title: "Help With This Tutorial"
date: 2007-02-25
forum: Networking &amp; Wireless
---

### Post by cessna_89702 on 2007-02-25
[HTML]https://help.ubuntu.com/community/WifiDocs/Device/Belkin_F5D7050_ver_3000_%28Ralink_rt73_driver%29?highlight=%28WifiDocs%2FDevice%29[/HTML]
Thats the link of the tutorial and I am trying to configure the Linksys USB. Step 4 Extract and Prepare the Archive is where it goes wrong. I run ```
zach@zach-laptop:~$ cd RT73_Linux_STA_Drv1.0.3.6/Module
zach@zach-laptop:~/RT73_Linux_STA_Drv1.0.3.6/Module$

``` and then it sends me the second line. Then I run ```
RT73_Linux_STA_Drv1.0.3.6/Module$ chmod -R 775 *
``` and I get ```
bash: RT73_Linux_STA_Drv1.0.3.6/Module$: No such file or directory

```

Thanks

---

### Post by finer recliner on 2007-02-25
is the folder you are running chmod in empty?

do an ls -a to make sure something is in there before trying to run that command.

---

### Post by cessna_89702 on 2007-02-25
Do what? Im new to Linux Im just doing what the tutorial says.

---

### Post by highneko on 2007-02-25
Maybe do it with sudo? Like this:
```
sudo chmod -R 775 *
```

---

### Post by cessna_89702 on 2007-02-25
sudo didnt work with it. I have a dv9000 laptop with a wireless card but I just bought the Linksys USB instead, thought it would work out of the box. Is there a tutorial for whatever wireless card that might be

---

### Post by cessna_89702 on 2007-02-25
any suggestions for the linksys

---

### Post by finer recliner on 2007-02-25
> **cessna_89702 said:**
> Do what? Im new to Linux Im just doing what the tutorial says.

ok so the command your stuck on is "chmod -R 775 *". this command will recursively (-R) change all files (*) to have the permissions of 775 (chmod). 

what i was trying to say in my previous post was that if the folder you perform this command from is EMPTY, then you will get an error. This is because without any files in the folder, there are no permissions to change. 

to view files in the folder you are currently in, type "ls". to view ALL files in the current folder (including hidden ones) you type "ls -a". you will always have two items (. and ..) when you do an ls -a. 

please let us know if your folder is empty, if it is, maybe you didnt extract the tar ball correctly

---

### Post by cessna_89702 on 2007-02-25
when I run tar xvzf RT73_Linux_STA_Drv1.0.3.6.tar.gz  I get the code ```
tar: RT73_Linux_STA_Drv1.0.3.6: implausibly old time stamp 1969-12-31 19:00:00

``` back does that matter

---

### Post by cessna_89702 on 2007-02-25
i get more than that above it also

---

