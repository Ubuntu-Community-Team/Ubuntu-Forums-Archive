---
title: "Linksys WMP11"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by measekite on 2007-10-03
[COLOR=Black]I understand that I can use ndis wrapper plus the Linksys CD that came with my wireless card.

I also read that I cannot use the .exe file but I need to extract the .inf and the .sys files from setup.exe.

[COLOR=Navy]Does anyone know how to do that?[/COLOR][/COLOR]

---

### Post by Lambert on 2007-10-03
These instructions are from the command line

**How do I unpack a Windows driver file in .EXE format?**

Usually these are self-extracting zip files. If that is the case, in Linux, you can run &#8216;unzip&#8217; on the .EXE file, which should extract files. Sometimes, they are .cab files, in which case, you can use &#8216;cabextract&#8217; to unpack. If you find .INF and .SYS files at this step, that is all you need. However, some drivers, after extracting, will give install shield files, usually in &#8216;data2.cab&#8217; file. To extract files out of data2.cab, run &#8216;unshield x data2.cab&#8217;. You should now have .INF and .SYS files in a sub-directory where you extracted. So, in short, a combination of unzip/cabextract/unshied can unpack driver file in most cases. This combination doesn&#8217;t always work though - sometimes you may need to use &#8216;wine&#8217; to extract. And in a few cases, even that doesn&#8217;t work and you need to use Windows to install the driver and find .INF and .SYS files.

So to try and simplify, move the files off the disk to someplace on your hard drive, open a terminal and type in unzip xxx.exe

Not knowing your experience, if you need more clarification, just ask.

---

### Post by kevdog on 2007-10-03
As stated above the .exe file is either a self-extracting zip file or a cabinet file.  cabextract will work for cabinet files.  For self-extracting zip files, you might be best to unzip on a windows machine and then just bring the drivers over on a USB stick.

---

