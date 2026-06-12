---
title: "Ubunrtu wont boot after restart?"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by rom3lol on 2011-08-09
I restarted my laptop I get the following error.
> 
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting / sys/ on root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or dirctory
Target filesystem doesn't have /sbin/init.
No init found. Try passing init= boot arg

BusyBox v1.13.3 (Ubuntu 1:1.13.3.-1ubuntu11) built-in shell (ash)

(initramfs)

---

### Post by lmarmisa on 2011-08-09
Boot into an Ubuntu Live CD / USB, open Firefox and go to the website:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then download the Boot Info Script, execute it and post here the results. Try to follow the instructions of the web page.

Best regards,

Luis

---

### Post by rom3lol on 2011-08-10
> **lmarmisa said:**
> Boot into an Ubuntu Live CD / USB, open Firefox and go to the website:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

Then download the Boot Info Script, execute it and post here the results. Try to follow the instructions of the web page.

Best regards,

Luis

I did the following and haven't got any results. It stays at the following

```
ubuntu@ubuntu:~/Downloads/boot_info_script060$ sudo bash boot_info_script.sh

boot_info_script version: 0.60        [17 May 2011]

Identifying MBRs...
Computing Partition Table of /dev/sda...
Searching sda1 for information... 
Searching sda3 for information... 
Searching sda5 for information... 
Searching sda6 for information... 
```

---

### Post by lisati on 2011-08-10
No sign of any file "results.txt" that you could post?

---

### Post by rom3lol on 2011-08-10
> **lisati said:**
> No sign of any file "results.txt" that you could post?

I ran the script an it didn't output the Results.txt file. I have search and have found nothing. I did a search for the file and nothing was found. Any other possibilities or workarounds?

---

### Post by jtarin on 2011-08-10
Using the Live CD boot to the desktop and in a terminal run the command ```
sudo fdisk -lu
```and post the results here.

---

### Post by rom3lol on 2011-08-10
I fixed the problem. :KS 
I honestly don't know what commands fixed it. But I did learn out of these problem!:D
Below are some of the links that helped me.

[http://ubuntuforums.org/showthread.php?t=1244466](http://ubuntuforums.org/showthread.php?t=1244466)

[http://www.linuxquestions.org/questions/linux-newbie-8/new-to-ubuntu-and-having-problems-with-hd-858664/](http://www.linuxquestions.org/questions/linux-newbie-8/new-to-ubuntu-and-having-problems-with-hd-858664/)

[http://kuniganotas.wordpress.com/2010/11/02/error-on-mounting-dev-on-rootdev/](http://kuniganotas.wordpress.com/2010/11/02/error-on-mounting-dev-on-rootdev/)

---

### Post by jtarin on 2011-08-10
My suspicion was an shutdown before things were correctly unmounted....I was going to suggest a filesystem check as a next step. Oh well! Glad your up.

---

