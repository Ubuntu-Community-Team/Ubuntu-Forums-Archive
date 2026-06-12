---
title: "How to get  ATI/AMD Catalyst 9.1?"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by DukeJP2010 on 2009-01-30
So I saw on digg that there is a [new version of Catalyst that fixes a ton of stuff ]("http://digg.com/linux_unix/Latest_ATI_Linux_Video_Driver_Introduces_Full_OpenGL_3_0_Sup").

I am new to Ubuntu, and I was wondering how to take advantage of this on my computer? I found [this thread]("http://ubuntuforums.org/showthread.php?t=1054492"), but it's a little to advanced for me.

Thanks!

---

### Post by buffy^ on 2009-01-30
You should be able to download the file from the AMD website and then you will need to compile it.

[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)

It looks to me like you can run them stright out.

---

### Post by DukeJP2010 on 2009-01-30
So I should be able to just download the file to the desktop, and double click it?

Sorry, I'm completely new to Lunix.

Are there any commands that I can type into the console to help you? I'm pretty sure I have the ATI propriety driver installed. Do I need to uninstall it somehow?

Thanks!
-Jason

---

### Post by DukeJP2010 on 2009-02-02
I'm sorry to bump my post, but my issue has not been resolved. I am happy to provide any information that may help you.

Thanks in advance for the help!

-Jason

---

### Post by Mark Phelps on 2009-02-02
All your questions are answered in the Installer Instructions link that is at the top of the page containing the driver download link.

Download the instructions and read through them.  Would suggest you use the Automatic option since you are new to Linux.

---

### Post by DukeJP2010 on 2009-02-04
Following this guide: [http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

When I type in this: 
```
sh ati-driver-installer-9-1-x86.x86_64.run --buildpkg Ubuntu/intrepid 
```

all I get are the "..._amd64.deb" files, but I do not have a 64 bit computer. Thus, when i type in the next command:
```
sudo dpkg -i xorg-driver-fglrx_8.573-0ubuntu1_i386.deb fglrx-kernel-source_8.573-0ubuntu1_i386.deb fglrx-amdcccle_8.573-0ubuntu1_i386.deb 
```

I get:
```
dpkg: error processing xorg-driver-fglrx_8.573-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-kernel-source_8.573-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory
dpkg: error processing fglrx-amdcccle_8.573-0ubuntu1_i386.deb (--install):
 cannot access archive: No such file or directory

```

Any idea why my Ubuntu thinks I have a 64 bit computer?

Thanks
-Jason

EDIT: Turns out i have an Intel® Core™2 Duo Mobile Processor T8100, which IS a 64 bit processor. I've just been using Windows Vista 32-bit on this laptop for it's entire life. So, linux was smart enough (and free enough) to install it's 64-bit version. It has "4.3.2 (x86_64-linux-gnu)" listed.

I will go ahead with the 64 bit install, and let you know.

EDIT2: everything works fine now. When i type in
```
fglrxinfo 
```
i now get
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 3400 Series
OpenGL version string: 2.1.8395 Release

```

Which I believe is the latest version. Thanks for the help.

---

### Post by NitrOuS on 2009-02-16
I have the same version of radeon video card. I installed the driver using the instructions listed [here]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide") and info from executing ```
fglrxinfo
``` command is the ones expected. But I have problems with rendering. 
When I execute 
```

sudo atiode -P60 -H localhost:0; echo$;

```
,something I found in aticonfig I get code 2, which means that the test ended with problems in rendering. I have these rendering problems also in my desktop effects. When I grab the window with my mouse with wobbly windows enabled I can only see the entire window only when the wobbling is over. I also have this problem when watching a video.
Does anyone know which extra configuration should I do? 
I tried ```
sudo aticonfig --sync-video=on
``` which fixed video but messed up desktop effects. I had the same results with ```
 sudo aticonfig --xinerama=on
```
Thanks in advance

---

