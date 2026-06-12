---
title: "computer janitor"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by jimbean on 2009-09-23
used computer janitor
and this is what happens every time update manager pops up
Not all updates can be installed
run a partial upgrade to install as many updates as possibe

then its says broken packages
and to run sudo apt-get install -f
i typed this so it may not be typed correctly
usually i just copy and paste

but when i run that command sudo apt-get install -f
it says errors and does not fix anything

and i ran synaptic
and this is what it says
E: brscan2: subprocess post-removal script returned error exit status 1

---

### Post by wojox on 2009-09-23
What happens when you run:

```
sudo apt-get remove --purge brscan2
```

---

### Post by jimbean on 2009-09-23
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

any ideas thankyou

---

### Post by jimbean on 2009-09-23
sorry had two programs runnung at once

this is what it said after i closed synaptic and the terminal


Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  brscan2
0 upgraded, 0 newly installed, 1 to remove and 2 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 174095 files and directories currently installed.)
Removing brscan2 ...
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/ALL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData/AL': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane/GrayCmData': No such file or directory
rmdir: failed to remove `/usr/local/Brother/sane': No such file or directory
dpkg: error processing brscan2 (--remove):
 subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
 brscan2
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Peacefulpieofdeath on 2009-09-23
Close down all the other synaptic that are open, then do what he said...

also that sudo apt-get install -f should have the pacage you want after

LIKE:

sudo apt-get install -f pidgin

also try sudo apt-get update

---

### Post by jimbean on 2009-09-23
thanks for reply

allready did that

i found this post



Thanks Dave the H

I still get the same results when I use the --force option. I am posting the results below. (as aside How do I get the output to be in one of those neat scroll boxes I see some times?)

# apt-get --purge remove --force-yes brscan2
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED
brscan2
0 upgraded, 0 newly installed, 1 to remove and 73 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 161584 files and directories currently installed.)
Removing brscan2 ...
rmdir: /usr/local/Brother/sane/GrayCmData/ALL: No such file or directory
rmdir: /usr/local/Brother/sane/GrayCmData/AL: No such file or directory
rmdir: /usr/local/Brother/sane/GrayCmData: No such file or directory
rmdir: /usr/local/Brother/sane: No such file or directory
dpkg: error processing brscan2 (--remove):
subprocess post-removal script returned error exit status 1
Errors were encountered while processing:
brscan2
E: Sub-process /usr/bin/dpkg returned an error code (1)
#

The out put seams to me to be indicating that the script is trying to remove those folders twice. Yes they do exist when the package is in the installed state. I haven't tried to make a couple of dummy folders an rerunning the script yet. Also I am not familiar with "touch", but making the dummy folders through Konqueror as root should serve the same purpose I suppose.

What if I put an extra read only file in the folder that is not normally there. I have seen that cause the uninstall complete but leave the folder behind for manual removal. Think I will try that first.

Thanks for listening to me ramble on. Sometimes that is the best help.





 and it said to create folders in my usr/local/brother file
the prob is i cant create files in that folder i dont have permission
how do i get permission
i am using the gui

i am not terminal savvy
could you post a command that will let me put folders in that file

---

### Post by krakerjak on 2009-09-25
I had the same problem.  I fixed it (it seems) by opening nautilus as root (gksudo nautilus), and manually creating the folders and then running: sudo apt-get install -f in the terminal.

HTH
KJ

---

