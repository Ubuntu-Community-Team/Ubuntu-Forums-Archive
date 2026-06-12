---
title: "Downloading updates whilst using a UK university's internet proxy?"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by loobyloo on 2009-03-11
Hi

I'm trying to download the system updates whilst here in a university library. Somewhere (I can't find it now for some reason) there was a thread about how to alter the settings in Synaptic or Network Settings or something, which would enable you to update while connected to the internet via the university's proxy.  Can anyone remind me what these settings are?

Thanks

---

### Post by aeiah on 2009-03-11
does this help?
[http://ubuntuforums.org/showthread.php?t=35308](http://ubuntuforums.org/showthread.php?t=35308)

---

### Post by loobyloo on 2009-03-11
No, that's not working for some reason.  I didn't have an apt.conf file so I logged in as root, and went to etc/apt.  I got the port off our Computer Services website and I made a file apt.conf.

acquire::http::proxy "http://myusername:mypassword@http://wwwcache.myuni.ac.uk/:8080";

I saved it in /etc/apt

But when I go to run the update manager, there are several lines of errors, all in the following form.

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/i18n/Translation-en_GB.bz2)  Could not resolve ‘http’

Is there something I'm missing?

---

### Post by loobyloo on 2009-03-11
Obviously, without the smiley!

---

### Post by loobyloo on 2009-03-11
Aha...got it. A stray http:// in my version.  

Here it is again in case anyone else needs it:

Connecting for Updates through a UK university's proxy:

Write this in gedit

acquire::http::proxy "http://username:password@wwwcache.university.ac.uk:8080";

add this to apt.conf in /etc/apt/

I didn't have it so I had to log in as root and make a new file and save it there.

Thankyou aeiah!

---

