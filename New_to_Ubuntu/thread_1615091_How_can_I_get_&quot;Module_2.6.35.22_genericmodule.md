---
title: "How can I get &quot;Module 2.6.35.22_generic/modules.dep&quot;"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by eric901 on 2010-11-06
Every time I boot my computer I get the following message: 
FATAL: Module 2.6.35.22_generic/modules.dep not found.

Everything seems to run normally regardless, but if I'm missing important files I want to get them. I tried updating my kernel, but the message persists. 
So how do I get the module?

---

### Post by Hippytaff on 2010-11-06
What kernel are you running on
```

uname -a

```

---

### Post by eric901 on 2010-11-06
The uname -a output is:
2.6.35-22-generic #35-Ubuntu SMP Sat Oct 16 20:36:48 UTC 2010 i686 GNU/Linux

---

### Post by Hippytaff on 2010-11-06
try
```

sudo apt-get dist-upgrade

```it seems odd that that module is there and yet your getting this error :-s
also give
```

sudo apt-get -f install

```
a try

---

### Post by eric901 on 2010-11-06
```
$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
there doesn't seem like anything's missing, yet I get the fatal error every time I boot up.

Given that no harm has come of this so far, I think I'll just live with the message; unless someone knows the message will give me trouble in the future. 

Thanks for the help though :)

---

### Post by Hippytaff on 2010-11-06
It certainly doesn't seem that 'fatal' if everything still works ok:-s
odd

---

### Post by Bluenoser81 on 2010-11-06
I get this exact same message on the same kernel, but since everything seems to be working fine it was lower down on my list of things to look into.  I did occasionally run across something about this error, but I can't remember where it was. Anybody know?

---

### Post by gsocker on 2010-11-06
The error message is a bit odd. "modules.dep" is actually a file listing module dependencies - which modules require other modules. It is not a module in and of itself.

Run 
```
 ls -l /lib/modules/`uname -r`/modules.dep
```If you get "No such file or directory", then this file has somehow been erased.

If it exists, I have no idea why the startup scripts are complaining.

You can recreate it if missing with
```

sudo depmod -a

```This will scan all modules and recreate the "modules.dep" file for the kernel you are running.

---

### Post by Hippytaff on 2010-11-06
I've got the same kernel...no issues

---

### Post by Bluenoser81 on 2010-11-06
Just ran that code, the modules.dep is there. Any other ideas? Like I said, not a major issue, because everything seems to work, but it does look ugly on boot.

---

### Post by coffeecat on 2010-11-06
> **gsocker said:**
> If you get "No such file or directory", then this file has somehow been erased.

If it exists, I have no idea why the startup scripts are complaining.

I had this blood-curdling error a couple of times with a new install of Maverick and the modules.dep file was definitely there. And everything worked too. So I did what I always do when I get blood-curdling errors and things work anyway. I ignored it. :)

And now I don't get the error message. Which is nice.

---

### Post by Bluenoser81 on 2010-11-06
> **coffeecat said:**
>  And now I don't get the error message. Which is nice.

Did you do any updates since you installed 10.10? I haven't yet, so maybe that's the problem.  I'm curious as to why it just seemed to go away, because I've been using 10.10 since it's release and it has said that error on every boot (maybe I am not ignoring it hard enough :P )

---

### Post by Hippytaff on 2010-11-06
maybe update and upgrade?
```

sudo apt-get update && sudao apt-get upgrade

```
Haven't re-read the posts, so apologies if this is not relevant :-)

---

### Post by 0x656b694d on 2010-11-15
i got the issue with 2.6.35-22 on my eeePC 1015 (don't know about any older kernels), upgraded to 2.6.35-23 with no luck — same error notification about the new kernel.

---

### Post by MrGreen on 2010-11-29
Having the same problem after upgrading my laptop to 10.10

```
2.6.35-23-generic
```

modules.dep is on my system

tried update-initramfs -u

System is up to date

Did anyone get a fix for this?

---

