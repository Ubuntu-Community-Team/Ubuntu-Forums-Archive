---
title: "broken software updates"
date: 2011-08-30
forum: New to Ubuntu
---

### Post by obatala on 2011-08-30
new install of ubuntu 11 not installing software or updates
software center not loading programs

---

### Post by gnometorule on 2011-08-30
Please describe your problem in a little more detail: do you have the entry Software Center? Can you search it? If these two are yes, what happens when you try to install software?

---

### Post by gnometorule on 2011-08-30
Please also try from a commandline (Accessories -> Terminal):

sudo apt-cache search nasm
sudo apt-get update

You will be asked to enter your password after each line. Password entry is not visible at the shell, so just keep typing.

(1) Does it find 'nasm'? (you won't want this program, just does it find it?)

(2) Does it update after the second line? (you should see feedback on your screen)

---

### Post by waqas_butt0071 on 2011-08-30
try 

```
apt-get update
```

---

### Post by Enigmapond on 2011-08-30
> **gnometorule said:**
> Please describe your problem in a little more detail: do you have the entry Software Center? Can you search it? If these two are yes, what happens when you try to install software?

Also how did you install? Did you check your network? What errors are you getting? Really need to know more. It's like posting, "I just bought a car but it's not working. Can you tell me what's wrong?"... :)

Cheers! and oh...welcome to the forum!

---

### Post by obatala on 2011-08-31
I have copac presario  cq60 notebook
   pata host adaptor mcp785 ide cd/dvd optiarc ad-75605
   nvidia 173.14.30
   
    i downloaded ubn11.04 burned iso to cd installed good.
    Firefox workes.bit slow.other software works.
    Updater software center not connect to net.
    Bug error mes.              Update manager
                                         e: Encountered a section with no package: Header
                                         e: Problem with merge list /var/lib/apt/list
                                         us.archive.ubuntu.com_ubuntu_disk_natty_main_binar_i386
                                        _packages    packages could not be opned



           thnx for any help obatala

---

