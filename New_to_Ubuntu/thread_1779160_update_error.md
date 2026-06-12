---
title: "update error"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by beew on 2011-06-10
Hi, 

I having getting this error message in Synaptic during updates for the last couple of days.
> Errors were encountered while processing:
 bcmwl-kernel-source
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bcmwl-kernel-source (5.100.82.38+bdcom-0ubuntu3.1) ...
/var/lib/dpkg/info/bcmwl-kernel-source.postinst: 53: Syntax error: "fi" unexpected (expecting ";;")
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source

Other than that everything else goes through with no issue. Ubuntu version is 11.04.Thanks  any help/suggestion in advance.

---

### Post by jtarin on 2011-06-10
Do you have a Broadcom chip?

---

### Post by jtarin on 2011-06-10
[A bug......and a probable solution.]("https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/793890")

Read the comments

---

### Post by beew on 2011-06-10
> **jtarin said:**
> Do you have a Broadcom chip?

Well yes and no. This is an installation on an external drive. I use it in a computer with a Broadcom wifi card sometimes,--and WIFI works flawlessly, but in other times no. :)

---

### Post by jtarin on 2011-06-10
> **beew said:**
> Well yes and no. This is an installation on an external drive. I use it in a computer with a Broadcom wifi card sometimes,--and WIFI works flawlessly, but in other times no. :)
Well it would be your decision....either uninstall it or follow the directions on that page. They give the option of editing the file or downloading a working one.

---

