---
title: "ubuntu software center"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by knoxemt1983 on 2010-08-15
Hi all, I'm new to linux and am just learning the ropes of this os, made the jump from windows xp to ubuntu 10.04 about a month ago. I tried to install a cannon pixma printer but have since given up and returned it since I don't really need it on my laptop. 

My problem is now I get this error message whenever I try to install from the software center. 

"package operation failed

E:I wasn't able to locate a file for the cnijfilter-common package. This might mean you need to manually fix this package. (due to missing arch): "

I googled and searched for all I could find, thats how I came to the assumption that it has something to do with the printer, but of course I could be way off base with that assumption. any have any idea what is wrong or how I can fix it? or maybe point me in a direction to find the answer?

thanks in advance for any help

---

### Post by blazemore on 2010-08-15
The easiest way is via the Terminal (Click Applications -> Accessories -> Terminal)

Copy and paste this with Edit -> Paste

```
sudo dpkg --configure -a; sudo apt-get -f install; sudo apt-get update; exit
```

Press Enter and type in your password, then press Enter again.

---

### Post by knoxemt1983 on 2010-08-15
> **blazemore said:**
> The easiest way is via the Terminal (Click Applications -> Accessories -> Terminal)

Copy and paste this with Edit -> Paste

```
sudo dpkg --configure -a; sudo apt-get -f install; sudo apt-get update; exit
```Press Enter and type in your password, then press Enter again.

thanks for the quick reply. I typed that in and it finished and closed but software center is still giving the same error.

---

### Post by Miljet on 2010-08-15
You are absolutely correct in assuming that the offending file is related to the printer install. I did a quick Google search for "cnijfilter-common ubuntu" and got numerous results. Most of the results involve installing the file, not getting rid of it. 

I guess it would depend on how you installed the file. The links I found indicate that this is a RPM file (Red Hat Package Manager) that has to be converted to a .deb package before installing. 

This link indicates that there is a dependency problem with libcupsys2 versus libcups2. 
[http://ubuntuforums.org/archive/index.php/t-1305248.html](http://ubuntuforums.org/archive/index.php/t-1305248.html)

---

### Post by jtarin on 2010-08-15
> My problem is now I get this error message whenever I try to install from the software center. Any software install?

---

### Post by sandyd on 2010-08-15
> **knoxemt1983 said:**
> Hi all, I'm new to linux and am just learning the ropes of this os, made the jump from windows xp to ubuntu 10.04 about a month ago. I tried to install a cannon pixma printer but have since given up and returned it since I don't really need it on my laptop. 

My problem is now I get this error message whenever I try to install from the software center. 

"package operation failed

E:I wasn't able to locate a file for the cnijfilter-common package. This might mean you need to manually fix this package. (due to missing arch): "

I googled and searched for all I could find, thats how I came to the assumption that it has something to do with the printer, but of course I could be way off base with that assumption. any have any idea what is wrong or how I can fix it? or maybe point me in a direction to find the answer?

thanks in advance for any help
```

sudo apt-get update
sudo apt-get -f install
sudo dpkg --remove --force-remove-reinstreq cnijfilter-common
```

---

### Post by knoxemt1983 on 2010-08-15
> **carlee said:**
> ```

sudo apt-get update
sudo apt-get -f install
sudo dpkg --remove --force-remove-reinstreq cnijfilter-common
```


that did the trick. thanks

---

### Post by knoxemt1983 on 2010-08-15
> **jtarin said:**
> Any software install?

it's now solved but yes it was any software I tried

---

