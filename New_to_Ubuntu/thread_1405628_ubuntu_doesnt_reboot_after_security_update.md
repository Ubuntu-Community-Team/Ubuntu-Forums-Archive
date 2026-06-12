---
title: "ubuntu doesnt reboot after security update"
date: 2010-02-12
forum: New to Ubuntu
---

### Post by orcurrentresident on 2010-02-12
I'm currently running Ubuntu 9.10 x64. After a recent security update my ubuntu refuses to reboot from the system menu. If I click System --> Shutdown and choose Restart, Ubuntu logs me out and immediately presents me with a Log-in Screen.

I can force a reboot by going to a terminal and doing a "sudo init 6" command

At the same time, my internet started behaving strangely. immediately after starting up, i can access the internet perfectly fine. Within 30 minutes of being rebooted, I am unable to access google.com or gmail. (i'm still able to access most other sites.) I've tried restarting my cable modem & router but the only thing that seems to fix it is doing a reboot via "init 6".

The two problems may be unrelated, but since they started at the same time I thought I'd mention it.

Any thoughts, comments, suggestions, or icecream will be greatly appreciated. (especially the icecream)

Thanks in advance!

---

### Post by byStanderone on 2010-02-12
...have you tried a restore mode?

---

### Post by jken146 on 2010-02-12
It's rather crude to use telinit to reboot. Instead you ought to use the command ```
sudo shutdown -r now
```

---

### Post by orcurrentresident on 2010-02-14
> **jken146 said:**
> It's rather crude to use telinit to reboot. Instead you ought to use the command ```
sudo shutdown -r now
```


I know its crude... but when I try to use "shutdown" it says command not found.

omatic@omatic-desktop:~$ sudo shutdown -r
[sudo] password for omatic: 
sudo: shutdown: command not found
omatic@omatic-desktop:~$ 


thoughts?

---

### Post by orcurrentresident on 2010-02-14
> **byStanderone said:**
> ...have you tried a restore mode?


Yes.. I've tried to restore but no luck...

---

### Post by orcurrentresident on 2010-02-14
My computer can't seem to find other core programs, too.   

[sudo] password for omatic: 
sudo: wget: command not found

---

### Post by jken146 on 2010-02-14
Looks like you might have removed a load of packages that you didn't want to.  Try ```
sudo apt-get install ubuntu-desktop
```

---

### Post by Julita on 2010-02-14
For your reboot problem, type in terminal 
```
sudo reboot
``` that should do the trick, you will see if there are any errors. As to your shaky internet connection, try wicd instead of Network Manager because the latter is confirmed to be less stable.

---

