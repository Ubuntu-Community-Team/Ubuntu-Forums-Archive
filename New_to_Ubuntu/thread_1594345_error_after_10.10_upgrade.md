---
title: "error after 10.10 upgrade"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by cmcanulty on 2010-10-12
Since my 10.10 upgrade I am getting this error every time I try to run my updates-upgrade
```
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up gloobus-preview (0.4.5-ubuntu8~ppa257) ...
/var/lib/dpkg/info/gloobus-preview.postinst: 33: gdk-pixbuf-query-loaders: not found
dpkg: error processing gloobus-preview (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 gloobus-preview
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
How can I fix this?

---

### Post by Rubi1200 on 2010-10-12
Try running this command in the terminal:

```
sudo dpkg --configure -a
```
Report any errors.

---

### Post by cmcanulty on 2010-10-12
Here is the error, thanks

```
cmcanulty@Gateway:~$ sudo dpkg --configure -a
[sudo] password for cmcanulty: 
Setting up gloobus-preview (0.4.5-ubuntu8~ppa257) ...
/var/lib/dpkg/info/gloobus-preview.postinst: 33: gdk-pixbuf-query-loaders: not found
dpkg: error processing gloobus-preview (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 gloobus-preview

```
I tried entering gloobus-preview in synaptic and marked for reinstall but then got this error
E: gloobus-preview: subprocess installed post-installation script returned error exit status 127

---

### Post by Rubi1200 on 2010-10-12
It's possible you may have to re-enable the PPA for the program to work (or is this the first attempt to install it?).

---

### Post by cariboo on 2010-10-12
Use the broken package filter in Synaptic to remove globus-preview, before trying to re-install it.

---

### Post by cmcanulty on 2010-10-12
Solved I found the fix here
[https://bugs.launchpad.net/gloobus-preview/+bug/658462](https://bugs.launchpad.net/gloobus-preview/+bug/658462)
Thanks everyone

---

### Post by Rubi1200 on 2010-10-12
Excellent! Glad you got it sorted out.

Please mark this thread Solved using the Thread Tools near the top of the page. That way, others who have run into this issue can also fix it.

---

