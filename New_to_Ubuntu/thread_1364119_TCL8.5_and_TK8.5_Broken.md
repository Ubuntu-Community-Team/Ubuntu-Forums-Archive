---
title: "TCL8.5 and TK8.5 Broken"
date: 2009-12-25
forum: New to Ubuntu
---

### Post by skymera on 2009-12-25
Hi

I tried installing aMSN the other day as an alternative to Emesene and my PC froze whilst apt-get was running.

After realizing that CTRL+ALT+Backspace was disabled >_<!!!!! i did a hard reboot.

Now i'm getting constant errors and not sure how to fix this:

```

scott@scott-desktop:~$ sudo apt-get install -f
[sudo] password for scott: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up tcl8.5 (8.5.7-1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing tcl8.5 (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of tk8.5:
 tk8.5 depends on tcl8.5 (>= 8.5.0); however:
  Package tcl8.5 is not configured yet.
dpkg: error processing tk8.5 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of amsn:
 amsn depends on tk8.5; however:
  Package tk8.5 is not configured yet.
dpkg: error processing amsn (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                    Errors were encountered while processing:
 tcl8.5
 tk8.5
 amsn
E: Sub-process /usr/bin/dpkg returned an error code (1)
scott@scott-desktop:~$ 

```

---

### Post by skymera on 2009-12-25
Fixed myself..

---

### Post by gad2103 on 2010-05-11
hey there. i am having this same problem. how did you fix this exactly? i've been googling to no avail. I can't seem to install anything without getting this error. Please help!

---

### Post by Platzii on 2010-06-05
I have the same problem..
Can you tell us how you fixed this?

Kind regards,
Platzii

Edit: I finally found it. Look here: [http://ubuntuforums.org/showpost.php?p=9202286&postcount=2]("http://ubuntuforums.org/showpost.php?p=9202286&postcount=2") for solution.

---

