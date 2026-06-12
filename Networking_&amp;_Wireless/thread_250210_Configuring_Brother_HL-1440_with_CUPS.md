---
title: "Configuring Brother HL-1440 with CUPS"
date: 2006-09-03
forum: Networking &amp; Wireless
---

### Post by butterman on 2006-09-03
I have a laptop running dapper and a desktop also running dapper with a usb connected printer.  I want to print remotely from my laptop. I followed the directions here:

[http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html#printset]("http://solutions.brother.com/linux/sol/printer/linux/cups_wrapper_install3.html#printset")

and here:

[http://www.ubuntuforums.org/showthread.php?t=123539&highlight=cups+network](http://www.ubuntuforums.org/showthread.php?t=123539&highlight=cups+network)

During installation I got the following error:

```
  sudo dpkg -i --force-all hl1440lpr-1.1.2-1.i386.deb
(Reading database ... 113511 files and directories currently installed.)
Preparing to replace hl1440lpr 1.1.2-1 (using hl1440lpr-1.1.2-1.i386.deb) ...
Unpacking replacement hl1440lpr ...
/var/lib/dpkg/info/hl1440lpr.postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: warning - old post-removal script returned error exit status 127
dpkg - trying script from the new package instead ...
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error processing hl1440lpr-1.1.2-1.i386.deb (--install):
 subprocess new post-removal script returned error exit status 127
/var/lib/dpkg/tmp.ci/postrm: line 3: /etc/init.d/lpd: No such file or directory
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 127
Errors were encountered while processing:
 hl1440lpr-1.1.2-1.i386.deb
```

Has anyone seen this?

---

