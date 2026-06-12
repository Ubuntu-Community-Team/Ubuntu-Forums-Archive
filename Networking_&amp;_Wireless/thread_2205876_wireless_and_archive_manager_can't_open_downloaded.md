---
title: "wireless and archive manager can't open downloaded driver"
date: 2014-02-16
forum: Networking &amp; Wireless
---

### Post by jbocean on 2014-02-16
1) trying to get linksys wusb300n working
2) have ndisgtk installed
3) went to linksys website and downloaded driver for the wusb300n 
4) archive manager opened up and i got the following message:

"Archive:  /home/john/Downloads/setup.exe
[/home/john/Downloads/setup.exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/john/Downloads/setup.exe or
          /home/john/Downloads/setup.exe.zip, and cannot find /home/john/Downloads/setup.exe.ZIP, period."

5) don't know what to do next

---

### Post by varunendra on 2014-02-16
Clearly, either the download is broken or the file is indeed not a simple executable zip archive.

In the former case, try re-downloading, preferably with a download manager (like "downthemall" plugin in FireFox).
In the latter case, either run it on windows, or on 'Wine' in Ubuntu to make it extract its contents by itself.

As a side note, make sure this driver is for windows XP, the same architecture (32 or 64 bit) as your Ubuntu installation is. Else it may not work with ndiswrapper.

---

