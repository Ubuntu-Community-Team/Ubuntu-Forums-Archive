---
title: "Strange files in root"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by Paddy Landau on 2009-05-30
I found some strange files in my root drives. They look like Windows files!

On my 8.04 Hardy drive, I have these odd-looking files:

```
eula.1028.txt
eula.1031.txt
eula.1033.txt
eula.1036.txt
eula.1040.txt
eula.1041.txt
eula.1042.txt
eula.2052.txt
eula.3082.txt
install.exe
install.ini
install.res.1028.dll
install.res.1031.dll
install.res.1033.dll
install.res.1036.dll
install.res.1040.dll
install.res.1041.dll
install.res.1042.dll
install.res.2052.dll
install.res.3082.dll
VC_RED.cab
vcredist.bmp
VC_RED.MSI

```The eula text files indicate that they have something to do with Visual Studio. How in heck did they get there?

On my 8.10 Intrepid drive, I have these odd-looking directories:
```
086450fa1b7670362e
0c637a512315a38d8680e8910c
0ce1401611587cba76fc0c870e
0fac8ecbfb679dcd9e7904e9ebded610
7d05e5b9a4fea0c2036a2a3133da
af725dae6f060eff0719244de422de18
f8c5848d31027eea70
fd5bb714404b592b6723ea379eed
```Each of these directories contains a file called [FONT=Courier New]$shtdwn$.req[/FONT].

Question: Is it safe to delete these files and directories?

---

### Post by lykwydchykyn on 2009-05-30
Those files surely have nothing to do with Linux.

Do you dual boot?  If so, does your Windows partition have access to the Linux partitions, e.g. using fs-drivers.org drivers?

Did you try to install something with wine?

The "$shtdwn$.req"  might be spyware related.  See this: 
[http://www.pcreview.co.uk/forums/thread-2237807.php](http://www.pcreview.co.uk/forums/thread-2237807.php)

---

### Post by Paddy Landau on 2009-05-30
> **lykwydchykyn said:**
> Do you dual boot?  If so, does your Windows partition have access to the Linux partitions, e.g. using fs-drivers.org drivers?
Yes, and yes. (I use [Ext2 File System]("http://sourceforge.net/project/showfiles.php?group_id=43775")).

> **lykwydchykyn said:**
> Did you try to install something with wine?
Yes. Perhaps it was something to do with that, although I wouldn't know which program it was.

> **lykwydchykyn said:**
> The "$shtdwn$.req"  might be spyware related...
Thanks for that (worrying) link. I will check it out.

---

### Post by pmigneous on 2009-05-30
[QUOTE="Paddy Landau"]root drives[/QUOTE]

drive**[color="red"]s[/color]**?
are the files actually in /?

regardless,
[QUOTE="Paddy Landau"]Question: Is it safe to delete these files and directories? [/QUOTE]
there's no reason any of those would be critical to Ubuntu. so yes, they are safe to delete.. worst case scenario, if you're using wine, and you've somehow managed to install a program to / (serious permission issues/sudo wine?) anything that needs that specifically may stop functioning.

also, in regards to the 8.10 partition, and the odd folders. if you do ```
file \$shtdwn\$.req
``` what does it say? if it's an ascii/text file, open it, see what's in it. Use your judgment, If it seems harmless, delete it. Else, post back.

---

### Post by Paddy Landau on 2009-05-31
> **pmigneous said:**
> drive**[COLOR=red]s[/COLOR]**?
Two different computers.

> **pmigneous said:**
> there's no reason any of those would be critical to Ubuntu. so yes, they are safe to delete.. worst case scenario, if you're using wine, and you've somehow managed to install a program to / (serious permission issues/sudo wine?) anything that needs that specifically may stop functioning.
Well, I deleted the files (after making a backup just in case!), and everything seems to still work fine. Regarding the serious permission thing, I'm wondering whether my son did something...

> **pmigneous said:**
> also, in regards to the 8.10 partition, and the odd folders. if you do ```
file \$shtdwn\$.req
``` what does it say? if it's an ascii/text file, open it, see what's in it. Use your judgment, If it seems harmless, delete it. Else, post back.
I can't get to that computer at the moment. However, yesterday I looked at the file with a hex editor, and contained a few bytes at the front followed by hex zeroes.

In all, it seems to have been solved (for now); I'll check regularly in case they reappear.

Thanks to everyone for your help and advice.

---

### Post by shaun_54au2 on 2010-03-31
$shtdwn$.req is one of the files extracted during a .net Framework 3.0 installation.  perhaps it was run through wine?

When I run the .net framework 3.0 pack I get a folder created with similar files:

/home/user/30f4b9f02dfcb3d8e4/baseline.dat
/home/user/30f4b9f02dfcb3d8e4/deffactory.dat
/home/user/30f4b9f02dfcb3d8e4/DeleteTemp.exe
/home/user/30f4b9f02dfcb3d8e4/dlmgr.dll
/home/user/30f4b9f02dfcb3d8e4/DW20.EXE
/home/user/30f4b9f02dfcb3d8e4/DWINTL20.DLL
/home/user/30f4b9f02dfcb3d8e4/eula.1025.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1028.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1029.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1030.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1031.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1032.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1033.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1035.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1036.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1037.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1038.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1040.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1041.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1042.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1043.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1044.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1045.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1046.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1049.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1053.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.1055.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.2052.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.2070.rtf
/home/user/30f4b9f02dfcb3d8e4/eula.3082.rtf
/home/user/30f4b9f02dfcb3d8e4/gencomp.dll
/home/user/30f4b9f02dfcb3d8e4/HtmlLite.dll
/home/user/30f4b9f02dfcb3d8e4/LocData.1025.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1028.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1029.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1030.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1031.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1032.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1035.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1036.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1037.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1038.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1040.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1041.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1042.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1043.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1044.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1045.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1046.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1049.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1053.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.1055.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.2052.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.2070.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.3076.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.3082.ini
/home/user/30f4b9f02dfcb3d8e4/LocData.ini
/home/user/30f4b9f02dfcb3d8e4/logo.bmp
/home/user/30f4b9f02dfcb3d8e4/RebootStub.exe
/home/user/30f4b9f02dfcb3d8e4/runmsi.exe
/home/user/30f4b9f02dfcb3d8e4/setup.exe
/home/user/30f4b9f02dfcb3d8e4/setup.sdb
/home/user/30f4b9f02dfcb3d8e4/setupres.1025.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1028.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1029.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1030.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1031.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1032.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1035.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1036.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1037.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1038.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1040.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1041.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1042.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1043.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1044.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1045.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1046.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1049.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1053.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.1055.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.2052.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.2070.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.3082.dll
/home/user/30f4b9f02dfcb3d8e4/setupres.dll
/home/user/30f4b9f02dfcb3d8e4/$shtdwn$.req
/home/user/30f4b9f02dfcb3d8e4/SITSetup.dll
/home/user/30f4b9f02dfcb3d8e4/vs70uimgr.dll
/home/user/30f4b9f02dfcb3d8e4/vsbasereqs.dll
/home/user/30f4b9f02dfcb3d8e4/vsscenario.dll
/home/user/30f4b9f02dfcb3d8e4/vs_setup.dll
/home/user/30f4b9f02dfcb3d8e4/vs_setup.msi
/home/user/30f4b9f02dfcb3d8e4/vs_setup.pdi
/home/user/30f4b9f02dfcb3d8e4/WapRes.1025.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1028.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1029.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1030.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1031.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1032.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1035.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1036.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1037.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1038.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1040.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1041.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1042.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1043.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1044.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1045.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1046.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1049.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1053.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.1055.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.2052.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.2070.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.3082.dll
/home/user/30f4b9f02dfcb3d8e4/WapRes.dll
/home/user/30f4b9f02dfcb3d8e4/WapUI.dll
**/home/user/30f4b9f02dfcb3d8e4/$shtdwn$.req**

---

### Post by Paddy Landau on 2010-03-31
Interesting response, thank you.

However, since removing my Windows partition, these directories have not returned.

So I think that they might have been caused by the driver in Windows accessing the Linux partition.

---

