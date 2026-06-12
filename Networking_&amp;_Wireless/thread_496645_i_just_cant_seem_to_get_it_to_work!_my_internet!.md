---
title: "i just cant seem to get it to work! my internet!"
date: 2007-07-09
forum: Networking &amp; Wireless
---

### Post by Lunatrix on 2007-07-09
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list_b/)

#27 is mine. i have a network key with it. i downloaded that link but its a .exe so ugh i knew it wouldent work because linux does not run .exe


any help? if so AIM me.

---

### Post by jpl80 on 2007-07-09
you're right. A windows .exe won't run on linux. You've got to extract it. Try using cabextract. If you don't have it, get it like this:

sudo aptitude install cabextract

then make a directory in /home/yourname called whatever and put the .exe inside. Then run cabextract on your .exe file like this:

cabextract yourdriver.exe

then go into your the directory you created and run ndiswrapper like this:

sudo ndiswrapper -i yourdriver.inf

you might have to load the driver:

sudo depmod -a
sudo modprobe ndiswrapper

this set of instructions is probably incomplete but should send you in the right direction... just keep reading and ask questions...

---

### Post by jpl80 on 2007-07-09
your card is actually the same chipset as mine. [I used these instructions and I have had success]("http://ubuntuforums.org/showthread.php?t=340689&highlight=inspiron+8500").

---

### Post by Lunatrix on 2007-07-09
JPL im stuck on number 7. is it possible for that not to work for me because i have ubuntu?

---

