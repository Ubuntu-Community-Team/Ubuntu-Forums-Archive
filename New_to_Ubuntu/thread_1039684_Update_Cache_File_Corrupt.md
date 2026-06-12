---
title: "Update Cache File Corrupt"
date: 2009-01-14
forum: New to Ubuntu
---

### Post by lduplantie on 2009-01-14
Hello,

Lately I have been getting an error message when updating Intrepid.

I get a pop up message box with something to the effect that the package cache file is corrupted.

Can this be fixed in any way?

Thank you

---

### Post by handydan918 on 2009-01-14
Unlike windows, error messages are there for a reason in Ubu. Post them verbatim when possible. It helps us help you.

---

### Post by lduplantie on 2009-01-14
Thank you handydan918,

I tried to copy the text of the message (Ctrl+C) but that did not work. ext time this happens (i.e. next update) I will write it down and post it here.

---

### Post by lduplantie on 2009-01-16
Hello again,

I am back with the full details about the error message. The attached image show the message box. Part of the text is in French, here is a liberal translation:

E: the package cache file is corrupt
E: cache -> open() failed, please report

Is this a problem with my PC or a problem with the repositories?

Thanks

---

### Post by lotusalive on 2009-02-07
I am facing this same problem with Ubu I.I. 8.10

Can someone please tell me if I can fix this error in my system, and how to do so?  I got this error message when I tried to load the 'kernel.us' repository.

(The Red and White Negative Symbol)   
-  An Error Occurred
The following details are provided:

E: The package cache file is corrupted

E: _cache->open() failed, please report.

Code input (as above suggestion) resulted in this:

sol@sol-desktop:~$ chown -R us base
chown: invalid user: `us'

The 'ubuntu.rocks.org' repo would not load at all due to unresolved dependencies with Main Mirror US.  I have no troubles loading the Main Mirror for the United States.  What did I do to break it??  Main Mirror acts like nothing is broken!  Fix??  
Thx in advance.

---

### Post by Roosje on 2009-03-26
> **lduplantie said:**
> Hello again,

I am back with the full details about the error message. The attached image show the message box. Part of the text is in French, here is a liberal translation:

E: the package cache file is corrupt
E: cache -> open() failed, please report

Is this a problem with my PC or a problem with the repositories?

Thanks

Hi,
Run : apt-config dump|grep Update

on my jauty system it pointed to packagekit, 
sudo apt-get remove packagekit 
solved my problem, but you may have something else.. good luck!

Wilco

---

### Post by madtownmike1 on 2009-04-02
Thank you, Roosje- removing packagekit fixed the problem on my intrepid box.

---

