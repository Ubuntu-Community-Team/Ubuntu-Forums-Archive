---
title: "Broken dependencies when trying to install OpenOffice"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by ptviperz on 2009-01-29
Hi guys, have a fun one here....my openoffice wouldn't run, kept starting up and crashing so I thought I'd upgrade it but apparently I had 12 broken OO packages. I tried to fix the packages using Synaptics->'Fix Broken Packages' but it kept failing. Obviously I couldn't install OO 3.0 either. 

I've uninstalled everything that has to do with OO and I have no broken packages anymore but when I try to start over I hit the same thing. Broken dependencies, etc etc, can't install OO. 

I've tried installing using apt-get, doing the install -f, I'm out of ideas at this point and a little frustrated. Any ideas?

---

### Post by gettinoriginal on 2009-01-29
Found this for you:
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

---

### Post by Thelasko on 2009-01-29
You used synaptic to install OO in the first place?  Or did you download it from OpenOffice.org?

P.S. Try running 
```
sudo apt-get clean
```
and then try reinstalling with synaptic.

---

### Post by ptviperz on 2009-01-29
> **gettinoriginal said:**
> Found this for you:
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

Hmm, I'll try this.

> **Thelasko said:**
> You used synaptic to install OO in the first place?  Or did you download it from OpenOffice.org?

It was installed with 8.10....2.6? I tried to use it and it was broken...that's when the saga started.

---

### Post by Thelasko on 2009-01-29
> **ptviperz said:**
> It was installed with 8.10....2.6? I tried to use it and it was broken...that's when the saga started.

Yeah, remove it and do the clean thing, and then reinstall it.

Here's why it might work:

APT downloads software once and then saves it in a cache so if you need to reinstall it, it doesn't have to download it again.  If those installation files were corrupted, we should get rid of them.  The "clean" command for APT gets clears the cache so it will have to download OpenOffice all over again.

---

### Post by ptviperz on 2009-01-29
> **gettinoriginal said:**
> Found this for you:
[http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/](http://tombuntu.com/index.php/2008/10/14/install-openofficeorg-30-in-ubuntu-804-and-810/)

This archive is no longer available. Thanks anyway!

---

### Post by ptviperz on 2009-01-29
> **Thelasko said:**
> Yeah, remove it and do the clean thing, and then reinstall it.

Here's why it might work:

APT downloads software once and then saves it in a cache so if you need to reinstall it, it doesn't have to download it again.  If those installation files were corrupted, we should get rid of them.  The "clean" command for APT gets clears the cache so it will have to download OpenOffice all over again.

Wow, that actually worked! I did apt-get clean && autoclean for good measure. Went to synaptics and it built with no broken packages. 

Thanks a ton!

---

### Post by Thelasko on 2009-01-29
> **ptviperz said:**
> Wow, that actually worked! I did apt-get clean && autoclean for good measure. Went to synaptics and it built with no broken packages. 

Thanks a ton!

Glad I could help.

---

### Post by ptviperz on 2009-01-29
> **Thelasko said:**
> Glad I could help.

Isn't there a thanks button on here somewhere? I'd hit it if I could find it.

---

### Post by Thelasko on 2009-01-29
> **ptviperz said:**
> Isn't there a thanks button on here somewhere? I'd hit it if I could find it.

It's not working at the moment.  There was a problem with the server and they had to disable it.  "Mark thread [solved]" doesn't work either.

---

### Post by stchman on 2009-01-29
> **ptviperz said:**
> Hi guys, have a fun one here....my openoffice wouldn't run, kept starting up and crashing so I thought I'd upgrade it but apparently I had 12 broken OO packages. I tried to fix the packages using Synaptics->'Fix Broken Packages' but it kept failing. Obviously I couldn't install OO 3.0 either. 

I've uninstalled everything that has to do with OO and I have no broken packages anymore but when I try to start over I hit the same thing. Broken dependencies, etc etc, can't install OO. 

I've tried installing using apt-get, doing the install -f, I'm out of ideas at this point and a little frustrated. Any ideas?

I have a script to install OO3.0 on 32 bit.

[http://www.stchman.com/tools_page.html](http://www.stchman.com/tools_page.html)

Down in the Scripts section.  I understand there is an Openoffice.org repo somewhere.

---

