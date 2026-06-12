---
title: "Alternate way to install flash"
date: 2010-01-21
forum: New to Ubuntu
---

### Post by rkakkar on 2010-01-21
For some reason flashplugin-installer is taking ages to download the adobe flash deb and is failing numerous times. Is there any other way I can install flash without using the flashplugin-installer? The adobe site just gives me the apt for the same.

---

### Post by lijcam on 2010-01-21
You could try installing the restricted formats package. This includes support for various audio/video codecs, flash, java, windows true type fonts etc.

sudo apt-get install ubuntu-restricted-formats

---

### Post by Grenage on 2010-01-21
On the adobe site, there should also be a tar.gz download of the latest release.  I managed to get my Flash working correctly by downloading that, and manually removing the old files.

---

### Post by rkakkar on 2010-01-21
> **Grenage said:**
> On the adobe site, there should also be a tar.gz download of the latest release.  I managed to get my Flash working correctly by downloading that, and manually removing the old files.

this is SO much easier! at least you have control on the download. thanks!!

---

### Post by rkakkar on 2010-01-21
> **rkakkar said:**
> this is SO much easier! at least you have control on the download. thanks!!

i spoke too soon!! although about:plugins shows flv support as yes .. adobe is still not able to pick up on flash .. i have copied the .so file to /usr/lib/firefox/plugins .. any ideas?

---

### Post by rkakkar on 2010-01-21
> **rkakkar said:**
> i spoke too soon!! although about:plugins shows flv support as yes .. adobe is still not able to pick up on flash .. i have copied the .so file to /usr/lib/firefox/plugins .. any ideas?

oops! i should have copied it to /usr/lib/mozilla/plugins ... works now :)

---

### Post by prenoob on 2010-01-21
> **rkakkar said:**
> this is SO much easier! at least you have control on the download. thanks!!

This is what I miss from Windows (...wince ..cower!)

---

### Post by Grenage on 2010-01-21
> oops! i should have copied it to /usr/lib/mozilla/plugins ... works now 

Glad it's working.  I don't know why the debs never worked (I didn't investigate), but the manual install is nice and easy.

---

### Post by cressrt on 2010-01-21
Hi,
I am new to ubuntu and am trying to install flash; I have tried the solution above but I do not have permissions to add the file to the relevant folder. Any ideas what I am doing wrong?

---

### Post by Grenage on 2010-01-21
You'll need elevated permissions to modify that directory:

```
gksu nautilus /usr/lib/mozilla/plugins
```

Will open the folder with root rights (prompting you for your password)

---

### Post by cressrt on 2010-01-21
Thanks, copied filr over no problem. Will remember the code for the future.

---

