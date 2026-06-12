---
title: "NdisWrapper + Broadcom BCM4306"
date: 2005-05-28
forum: Networking &amp; Wireless
---

### Post by turni on 2005-05-28
Okay, it is my first day using Ubuntu and I have had a couple of things which are not perfect out of the box (though I expected as much... yet to find a distro which is perfect ;-) ). 

I would like to try using my Wireless Lan again (shown in Ubuntu device manager as Broadcom BCM4306), and as far as I can tell using NdisWrapper is the way. I have followed the instructions on [http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto) and installed it, got to the second section and seem to need a windows driver. I found the correct driver, as refered to by the NdisWrapper list, but being a windows driver it is an *.exe, and I seem to need a *.inf. 

Is there a way to extract it, or am I just going about this in all the wrong way?

Thanks.

---

### Post by Staesys on 2005-05-28
If you have the unzip utility installed, you can use:

```
unzip filename.exe
``` 

...to decompress the file.

Wine will also let you run this file. The .exe is a self extracting archive. I have a PCMCIA network card with the same chipset and I used wine to exctract the .inf and .sys files to my desktop.

Wine and Unzip are available under apt or Synaptic. If you go with wine, I would recomend wine tools as well.

---

