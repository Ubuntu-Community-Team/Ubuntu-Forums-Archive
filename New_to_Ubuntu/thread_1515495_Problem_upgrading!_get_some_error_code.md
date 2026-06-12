---
title: "Problem upgrading! get some error code"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by vivek40 on 2010-06-22
Hii all!
I have Lucid installed on my system. . have also installed gnome shell through the ricotz repository. today when the system asked me to upgrade and I went ahead with it.. I get an error

> 
Vivek@vivek-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up gnome-shell (2.31.2+git20100621.9af97909-0ubuntu1~10.04~ricotz1) ...
/var/lib/dpkg/info/gnome-shell.postinst: 9: glib-compile-schemas: not found
dpkg: error processing gnome-shell (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 gnome-shell
E: Sub-process /usr/bin/dpkg returned an error code (1)

I tried "sudo apt-get -f install".. but even that did not work.. there were close to 14-15 upgrades which had shown , and all of them have upgraded fine.. aprt from this... can someone please help!

---

### Post by cariboo on 2010-06-22
If you install libglib2.0-dev, you should have no problems. there is a gnome-shell thread [here]("http://ubuntuforums.org/showthread.php?t=1476241") if you run into any other problems.

---

### Post by vivek40 on 2010-06-22
Thanks cariboo... installed libglib 2.0-dev... did an upgrade again after that... it installed fine.. but then while upgrading there is some sort of warning displayed in the terminal. I had a look at the thread pointed out by you , but it does not talk anything about this ....

> 
Setting up gconf2 (2.31.4-0ubuntu2~10.04~ricotz1) ...
WARNING: Failed to parse default value `[????????? ???????;gnome-appearance-properties.desktop,????????? ???????????? ???????????;gnome-default-applications.desktop,?????????? ??????????;system-config-printer.desktop] ' for schema (/schemas/apps/control-center/cc_actions_list)



---

