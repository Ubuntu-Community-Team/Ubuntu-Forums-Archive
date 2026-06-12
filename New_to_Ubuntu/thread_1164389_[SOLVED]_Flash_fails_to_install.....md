---
title: "[SOLVED] Flash fails to install...."
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Dark Aspect on 2009-05-19
Flash was installed and was working fine on Ubuntu 9.04 but after installing required libraries in Synaptic Package Manager, it removed flash and gives an error when I try to reinstall it.

```
Setting up flashplugin-installer (10.0.22.87ubuntu2) ...
Downloading...
--2009-05-19 15:13:35--  http://archive.canonical.com/pool/partner/a/adobe-flashplugin/adobe-flashplugin_10.0.22.87.orig.tar.gz
Resolving archive.canonical.com... 91.189.90.142
Connecting to archive.canonical.com|91.189.90.142|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 3968445 (3.8M) [application/x-gzip]
Saving to: `./adobe-flashplugin_10.0.22.87.orig.tar.gz'

2009-05-19 15:13:43 (505 KB/s) - `./adobe-flashplugin_10.0.22.87.orig.tar.gz' saved [3968445/3968445]

Download done.
Flash Plugin installed.
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-installer/libflashplayer.so
dpkg: error processing flashplugin-installer (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of flashplugin-nonfree:
 flashplugin-nonfree depends on flashplugin-installer; however:
  Package flashplugin-installer is not configured yet.
dpkg: error processing flashplugin-nonfree (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 flashplugin-installer
 flashplugin-nonfree
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Whats wrong?

---

### Post by Dark Aspect on 2009-05-19
Ok never mind I fixed it, some how my packages were broken. I fixed it with

```
sudo apt-get install -f
```

sorry to waste a post

---

