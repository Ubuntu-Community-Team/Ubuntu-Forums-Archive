---
title: "how to update to requested xorg version"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by trekki on 2011-01-26
For installation of a new driver for my graphics card i must have xorg in the version 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, 7.4, 7.5, or 7.6
I get the following
```
john@john-desktop:~$ Xorg -version

X.Org X Server 1.7.6
Release Date: 2010-03-17
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server x86_64 Ubuntu
Current Operating System: Linux john-desktop 2.6.32-27-generic #49-Ubuntu SMP Thu Dec 2 00:51:09 UTC 2010 x86_64
Kernel command line: root=UUID=ca90c57a-9e85-42c9-a16f-292dde4f7973 ro quiet splash 
Build Date: 10 November 2010  11:25:53AM
xorg-server 2:1.7.6-2ubuntu7.4 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.16.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.

```how can i update to one of the requested versions?

-trekki

---

### Post by cariboo on 2011-01-26
They are asking for the Xfree86 graphics server, that Ubuntu doesn't use. It probably would be better if you told us what driver you want to install, as most drives are compatible with Xorg.

---

### Post by trekki on 2011-01-26
Sorry, i missed this information. I want to install 
**ATI Catalyst&#8482; Proprietary Display Driver - Linux x86 & Linux x86_64**

[from]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English") [http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&#9001;=English]("http://support.amd.com/us/gpudownload/linux/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.42&lang=English")

I want to change to the closed source driver because of [this]("http://ubuntuforums.org/showthread.php?t=1660514") issue. The solution offered by TG12 seems to be reasonable, the amd driver is very new.

(please ignore the text size, i just copy-pasted this from the amd web site)

-trekki

---

### Post by trekki on 2011-02-04
I dont need the answer anymore because the update is unnessecary. I had a misunderstanding between the version numbers of xorg and x server.
The requested versions 6.7, 6.8, 6.9, 7.0, 7.1, 7.2, 7.3, 7.4, 7.5, or 7.6 are for the xorg not for x server.
x server 1.7 (as in my system) is part of xorg 7.5. Please dont ask me about other version relations, i got this hint from the german forum.ubuntuusers.de.
Finally i have installed the AMD driver and my displays are working almost OK.

---

