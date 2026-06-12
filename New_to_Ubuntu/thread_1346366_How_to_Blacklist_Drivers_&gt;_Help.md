---
title: "How to Blacklist Drivers &gt; Help ?"
date: 2009-12-05
forum: New to Ubuntu
---

### Post by mrsmurray on 2009-12-05
SUPER NEWBY HERE! Brand spanking new to the Ubuntu world, somewhat savy from the windows world, but feel like a preschooler over here.  Just loaded 9.10 on an oldish HP laptop but booted up with no wireless conectivity.  Came across this link, [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx")
and I am pretty sure it will solve my wireless issues.... but got as far as  "add the following two lines to /etc/modprobe.d/blacklist.conf:"

blacklist b43
blacklist ssb

What EXACTLY does that mean... how do I do that????

Thanks in advance for your help!

Michelle
Long Beach, Ca

---

### Post by natex on 2009-12-05
You need to create (or edit if it exists already) the file at /etc/modprobe.d/blacklist

Open a terminal and type "sudo gedit /etc/modprobe.d/blacklist" (no quotes of course).

Add the lines (again no quotes)
"blacklist b43"
"blacklist ssb"

Save the file. You've just opened that file as **root** (superuser) and blacklisted those modules (drivers). Now when you reboot the blacklisted drivers can't be used by modprobe.

Hope this helps.

nate

---

### Post by mrsmurray on 2009-12-05
Thanks for taking the time!!!  I appreciate it. 



It's like learning to walk again!

---

### Post by cartisdm on 2009-12-05
> **mrsmurray said:**
> Thanks for taking the time!!!  I appreciate it. 


It's like learning to walk again!

What wireless card do you own and were you able to solve the problem after blacklisting the drivers?

(just so future users will know of a usable fix):D

---

### Post by lkraemer on 2009-12-05
mrsmurry,
There has been a change in the name of the file on version's > 9.04, if
my memory serves me correctly.........I'm still on Ubuntu 8.04.3

Use these Terminal commands to locate your file name.
```

cd /
cd /etc/modprobe.d
ls

```
Your file's name could be blacklist OR blacklist.conf
Edit the one shown by the ls command.....

lk

---

### Post by natex on 2009-12-05
Thanks for pointing that out lkraemer. I just confirmed on a Karmic (9.10) install that it is indeed **/etc/modprobe.d/blacklist.conf**

---

