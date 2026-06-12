---
title: "Cant Get  boot_info_script to run"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by Thinder on 2011-02-12
I downloaded boot_info_script055.sh to my dowloads file and ran terminal:  sudo bash ~/downloads/boot_info_script055.sh  
 

It says no such file or directory,

 I moved it to my desktop and tried again and still nothing.  What am i doing wrong?

---

### Post by presence1960 on 2011-02-12
> **Thinder said:**
> I downloaded boot_info_script055.sh to my dowloads file and ran terminal:  sudo bash ~/downloads/boot_info_script055.sh  
 

It says no such file or directory,

 I moved it to my desktop and tried again and still nothing.  What am i doing wrong?

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

---

### Post by Rubi1200 on 2011-02-13
Hi Thinder,
are you using Ubuntu to do this?

I ask because if you are on another LiveCD other than Ubuntu, you could try prefacing the command with su instead of sudo.

---

### Post by oldfred on 2011-02-13
In Linux caps and small letters are different. 

In your post you said you tried to run from downloads, but the directory is Downloads??

---

### Post by Thinder on 2011-02-13
Well dont I feel like an idiot now.  Works like a champ! Thanks!!  


> **oldfred said:**
> In Linux caps and small letters are different. 

In your post you said you tried to run from downloads, but the directory is Downloads??

---

