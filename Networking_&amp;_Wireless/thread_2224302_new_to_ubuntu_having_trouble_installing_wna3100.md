---
title: "new to ubuntu having trouble installing wna3100"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by salvador3 on 2014-05-15
Hello I'm trying to help a niece of mine to set up her wireless connection on a pc given to her by her school,I am used to work in a windows environment and  this is totally new to me after doing some reading and watching a few videos.i installed wine went to the mfg website and downloaded the drivers,used wine to open the downloaded files,after that  i installed ndiswrapper and try to install drivers from there but i keep getting the following error "module could not be loaded. error was fatal module ndiswrapper not found. is the ndiswrapper module installed"

maybe someone here could point me in the right direction? by the way she is using a netgear WNA3100 usb adapter.

Thanks in advance.

---

### Post by smss on 2014-05-16
Hi, welcome to UF.
Do you want a network between two local computer(windows and linux)? ok, you can do it with samba easily. And you don't need the others wine or etc ...
just install it and go to nautilus and select the Network to see your windows group.

Else, Do you want to install a driver to can see the network? ok, you have to see for your technical information and google it.
get the ```
 $ lspci | grep Network 
``` output and search for your convenient driver ( which provided from your manufacturer )


Good Luck

---

### Post by varunendra on 2014-05-17
Wine is a 'Windows Compatibility Layer' software that is meant to install and run Windows software, while 'Ndiswrapper' is a Linux software. You don't need wine to install or run it, and any attempt to install it via 'wine' would obviously fail.

Ndiswrapper itself is a 'Windows Network Environment Emulator' that allows us to install and use windows wireless drivers on Linux (with no guaranty of success!). Usually it is our last resort (when there is no native Linux driver available for a device), but in your case it is indeed the 'Only' option (other than buying a better supported USB adapter).

So.. forget about wine, and simply follow posts **#4** and **#8** in this thread (courtesy praseodym) to install ndiswrapper and windows driver on top of it : [http://ubuntuforums.org/showthread.php?t=2221251](http://ubuntuforums.org/showthread.php?t=2221251)

I am not much familiar with ndiswrapper myself, so may not be able to help beyond searching and referring you to other experts' posts, which you can do yourself. :)

---

