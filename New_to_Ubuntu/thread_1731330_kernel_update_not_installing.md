---
title: "kernel update not installing"
date: 2011-04-17
forum: New to Ubuntu
---

### Post by kapi on 2011-04-17
Morning all,
Have tried twice but the header updates are not installing.

I would show you the message I received but am unsure how to add an image here as the image section requests a url and the image is on my local drive

Thanks

---

### Post by coffeecat on 2011-04-17
> **kapi said:**
> I would show you the message

That would be useful. To attach an image, use the "New Reply" button, not the "Post Quick Reply" one. Below the message field, click on the "Manage Attachments" button and you'll be able to browse to the image on your computer and upload it to the forum, when it will appear as a clickable thumbnail. No need for URLs.

If you are getting a terminal error message, highlight the text you want to post, right-click on it and "Copy". Then simply paste it into the message field, but enclose it between [noparse]```
 and 
```[/noparse] tags for clarity.

---

### Post by kapi on 2011-04-17
Hi again the output message was:

This package provides kernel header files for version 2.6.35 on x86/x86_64.
This is for sites that want the latest kernel headers.
Please read /usr/share/doc/linux-headers-2.6.35-28/debian.README.gz for details.

---

### Post by coffeecat on 2011-04-17
I've just updated and installed the same linux-headers package (2.6.35-28-50) in Maverick without any problem but there was a matching linux-image package installed as well. Also, the package linux-headers-2.6.35-28-generic needs the package linux-headers-2.6.35-28 as a dependency. It may be that there was a temporary repository inconsistency when you tried to update last. Click the check button in Update Manager and see if there are any other updates to install and see if it works then.

If that doesn't work, close Update Manager and open Synaptic. Check which version of he package linux-image-2.6.35-28-generic you have. Is it 2.6.35-28-49 or 2.6.35-28-50?

---

### Post by kapi on 2011-04-17
hi again Coffeecat;

checked my file and have these, 

thanks for the help . . . what next please?

---

### Post by coffeecat on 2011-04-17
The contents of /usr/share/doc is not of any help.

Did you try a check and update in Update Manager? My second question referred to System > Administration > Synaptic. You need to open it, but only after closing Update Manager.

---

### Post by kapi on 2011-04-18
Hi Coffeecat,

check synaptic as mentions and received the following, it says I already have 50 installed.

---

### Post by kapi on 2011-04-19
hi there, wondered if anyone has an idea of how to get the update issue working?

---

### Post by ttshivers on 2011-04-19
Try and install it from the terminal.

First type
```
sudo apt-get update
```

Next, type
```
sudo apt-get dist-upgrade
```

---

### Post by kapi on 2011-04-21
doing it now - thanks for the help

got this error though


eb) ...
Unpacking replacement policykit-1 ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_GB.utf8.cache...
Processing triggers for man-db ...
Processing triggers for python-support ...
Errors were encountered while processing:
 /var/cache/apt/archives/linux-headers-2.6.35-28-generic_2.6.35-28.50_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
craig@craig-Satellite-L300:~$ ^C
craig@craig-Satellite-L300:~$

---

### Post by coffeecat on 2011-04-22
Two thoughts.

Perhaps the deb package for the linux headers is damaged. Try deleting it and downloading a fresh copy  with:

```
sudo rm /var/cache/apt/archives/linux-headers-2.6.35-28-generic_2.6.35-28.50_i386.deb
sudo update
sudo upgrade
```Or - do you have a separate boot partition? It could be full, preventing the installation of the headers. Run and post the output of:

```
df -h
```Run it anyway in case there is a space problem somewhere.

---

