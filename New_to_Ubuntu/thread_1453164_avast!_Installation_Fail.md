---
title: "avast! Installation Fail"
date: 2010-04-12
forum: New to Ubuntu
---

### Post by kristine12 on 2010-04-12
So, here is the scenario. When I partially upgrade my Ubuntu 9.04 to the new Ubuntu distribution my avast! Anti-virus doesn't work anymore. I decided to reinstall it, but when I looked at Synaptic Package Manager the Reinstall menu is disabled. I mark it as Completely Remove then manually install it again. When the download had finished and the installation start an error occurred. Here is the error message:
[INDENT]sudo dpkg -i avast4workstation_1.3.0-2_i386.deb
(Reading database ... 192548 files and directories currently installed.)
Unpacking avast4workstation (from avast4workstation_1.3.0-2_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing avast4workstation_1.3.0-2_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/avast4workstation/lib-gtk2/libglib-2.0.so.0.0.7')
Errors were encountered while processing:
 avast4workstation_1.3.0-2_i386.deb
[/INDENT]I want to install the avast! so that I'm sure that there are no virus on the files that I've add to my Windows and backup. You're immediate response is highly appreciated!

---

### Post by sandyd on 2010-04-12
> **kristine12 said:**
> So, here is the scenario. When I partially upgrade my Ubuntu 9.04 to the new Ubuntu distribution my avast! Anti-virus doesn't work anymore. I decided to reinstall it, but when I looked at Synaptic Package Manager the Reinstall menu is disabled. I mark it as Completely Remove then manually install it again. When the download had finished and the installation start an error occurred. Here is the error message:[INDENT]sudo dpkg -i avast4workstation_1.3.0-2_i386.deb
(Reading database ... 192548 files and directories currently installed.)
Unpacking avast4workstation (from avast4workstation_1.3.0-2_i386.deb) ...
dpkg-deb (subprocess): short read in buffer_copy (failed to write to pipe in copy)
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing avast4workstation_1.3.0-2_i386.deb (--install):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/avast4workstation/lib-gtk2/libglib-2.0.so.0.0.7')
Errors were encountered while processing:
 avast4workstation_1.3.0-2_i386.deb
[/INDENT]I want to install the avast! so that I'm sure that there are no virus on the files that I've add to my Windows and backup. You're immediate response is highly appreciated!
it is likely due to a problem with the download.
try downloading it again and installing.

---

### Post by JohnL2009 on 2010-04-12
I have a similar problem but I get this error message:

"An error occured in avast! engine: Invalid argument"

Any Ideas as to how to fix?

---

### Post by Sir Jasper on 2010-04-13
Hi JohnL2009,

Your problem is different. See the first sticky: [http://forum.avast.com/index.php?board=5.0](http://forum.avast.com/index.php?board=5.0)

There are also two other threads a little below that.

Happy fixing

---

### Post by Kyluke on 2010-04-13
installing anti-virus on linux....

---

### Post by philinux on 2010-04-13
> **Kyluke said:**
> installing anti-virus on linux....

Needed if you interact with windows machines and wish to stop the spread via email etc.

---

### Post by Moyamo on 2010-12-11
I have the exact same problem on Ubuntu 10.10 Maverick Meerkay

---

### Post by I'mGeorge on 2010-12-11
try installing the deb package from their site [http://www.avast.com/en-eu/linux-home-edition#tab4](http://www.avast.com/en-eu/linux-home-edition#tab4) After you install it you will need to register to get a free license key. I've tried it and it works like a charm.

---

### Post by Moyamo on 2010-12-11
I did. I did try it like that and when I typed the command

```
yaseen@yaseens-desktop:~$ sudo dpkg -i ./Downloads/avast4workstation_1.3.0-2_i386.deb 
(Reading database ... 278847 files and directories currently installed.)
Unpacking avast4workstation (from .../avast4workstation_1.3.0-2_i386.deb) ...
dpkg-deb (subprocess): short read on buffer copy for failed to write to pipe in copy
dpkg-deb: subprocess paste returned error exit status 2
dpkg: error processing ./Downloads/avast4workstation_1.3.0-2_i386.deb (--install):
 short read on buffer copy for backend dpkg-deb during `./usr/lib/avast4workstation/bin/avastgui'
Errors were encountered while processing:
 ./Downloads/avast4workstation_1.3.0-2_i386.deb

```

that was the output

---

### Post by I'mGeorge on 2010-12-11
try it like this

```

cd /path_to_avast_deb
dpkg -i --force-all avast4workstation_1.3.0-2_i386.deb

```

by the way there's an error in your dpkg command "./Downloads/...". When you're using dpkg you don't have to put the dot in front of your path. That's only used when you're trying to execute a linux executable,. like a bin file for example.

---

### Post by Moyamo on 2010-12-11
It stilll doesn't work even with the --force-all option. I get the same error message.

---

### Post by CharlesA on 2010-12-11
Redownload the file and verify the md5sum before trying to install it.

---

### Post by Moyamo on 2010-12-11
I'm sorry but could you please explain what a md5sum is?

---

### Post by CharlesA on 2010-12-11
Nevermind, I guess they don't give you the MD5SUM of the file to make sure the download is ok.

Just download it again and see if it'll install.

---

### Post by Norm24 on 2010-12-11
If its really that much of a problem maybe try another av like Clamtk,AVG or BitDefender?

---

### Post by Moyamo on 2010-12-11
It worked after I re-downloaded the .deb package
Thanks for the advice

---

