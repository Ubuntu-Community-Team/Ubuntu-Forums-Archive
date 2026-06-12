---
title: "I am unable to get a higher resolution in my Intrepid Ibex"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by prasaanth on 2009-02-06
Dear all,
 I am absolute newbie to linux and i installed ubuntu ver 8.10 very recently. And to my dismay i found that several features arent working properly or atleast i am not able to make them run appropriately.

Firstly i am unable to set my screen resolution to 1024*768 (4:3), if i happen to set it in that value only about 3 quarters of my screen is filled with content and the rest is blanked out. I have attached the screen shot of it for your reference.

Secondly when i happened to install all the updates recommended, openoffice got messed up and it shows that i have to fix it through broken filter. However when i fix broken packages there are still error messages shown like this

E: /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb: short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libcharttools680li.so')


Please help...
Thanks in advance...

with regards

Prando a.k.a Prasaanth

---

### Post by kspncr on 2009-02-06
Regarding your screen resolution, it sounds like your video card driver is not installed. Try clicking System->Administration->Hardware Drivers to see if the driver is listed and whether or not it's in use.

As for OpenOffice.org, you can try reinstalling it. Click Applications->Add/Remove... then search for OpenOffice. You'll then have to uncheck the checked results, click "Apply Changes," then reinstall: re-check the boxes and click "Apply Changes" again.

Hope at least one of these helps.

---

### Post by prasaanth on 2009-02-06
When i clicked to see the Hardware Drivers, it says " No proprietary hardware drivers are installed".

As for the re installation of office package, i had tried it earlier but it didnt do any good to me. :(

In the terminal when i typed sudo apt-get install

The following packages will be upgraded:
  openoffice.org-core
1 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
12 not fully installed or removed.
Need to get 0B/26.1MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 127632 files and directories currently installed.)
Preparing to replace openoffice.org-core 1:2.4.1-11ubuntu2 (using .../openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb) ...
Unpacking replacement openoffice.org-core ...
lzma: Decoder error
dpkg-deb: subprocess <decompress> returned error exit status 1
dpkg: error processing /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb (--unpack):
 short read in buffer_copy (backend dpkg-deb during `./usr/lib/openoffice/program/libcharttools680li.so')
Errors were encountered while processing:
 /var/cache/apt/archives/openoffice.org-core_1%3a2.4.1-11ubuntu2.1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
prando@prando-desktop:~$ 

This was displayed....

Please suggest some alternatives.......


With regards

Prando

---

