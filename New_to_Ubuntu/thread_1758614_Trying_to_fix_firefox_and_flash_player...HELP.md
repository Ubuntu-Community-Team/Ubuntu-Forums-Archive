---
title: "Trying to fix firefox and flash player...HELP??"
date: 2011-05-14
forum: New to Ubuntu
---

### Post by CrhisCarter on 2011-05-14
this is the error i get. i think im using Kubuntu Karmic..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
adept is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up linux-headers-2.6.32-21-generic (2.6.32-21.32) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing linux-headers-2.6.32-21-generic (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-2.6.32-21-generic; however:
  Package linux-headers-2.6.32-21-generic is not configured yet.
dpkg: error processing linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                 Errors were encountered while processing:
 linux-headers-2.6.32-21-generic
 linux-headers-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)

anyone feeling ninja enough to help? i am very into the linux world and would like to learn much more :)

---

### Post by Rubi1200 on 2011-05-15
Hi and welcome to the forums :-)

You can find out which version you are using with this command:

```
cat /etc/*release
```

To try and fix the error, run this:

```
sudo dpkg --configure -a
```

followed by 

```
sudo apt-get update

```
Post back with errors.

---

### Post by no2498 on 2011-05-15
in/on fire fox install the plug-in flash aid and then run it

---

### Post by 5149.5 on 2011-05-15
+1 on the flashaid. After it is installed, click Preferences to run it.

---

### Post by sammiev on 2011-05-15
+1 for Flash Aid. GL :)

---

### Post by uRock on 2011-05-15
Hello and welcome to the forums,

Looks like the Lucid kernel listed. The second and third commands offered by Rubi1200 should fix your package manager, if not, then please copy the errors and post them here.

[FlashAid]("https://addons.mozilla.org/en-US/firefox/addon/flash-aid/") can help you get the correct flash installed for your system.

Please let us know if the fixes work for you.

Cheers,
uRock

---

