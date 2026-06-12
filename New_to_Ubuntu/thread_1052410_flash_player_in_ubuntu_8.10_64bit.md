---
title: "flash player in ubuntu 8.10 64bit"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by capnthommo on 2009-01-27
hi everybody
can anyone help?  when i try to download and install the flash player from adobe i keep getting at the package installer stage
> 
Error:  Wrong architecture 'i386' 

i could use this before i upgraded to 64 bit and also after the upgrade for 2/3 days.  what is going wrong.
i don't think i have done anything major andi have also followed the advice in the multimedia sticky on the multimedia and video forum.
the sound settings are also odd on System - Preferences - Sound.
can anybody help.  it will be greatly appreciated
thanks in advance
nigel

---

### Post by mikewhatever on 2009-01-27
Until quite recently, Adobe only made flash for 32 bit systems. Things have changed, however, and there is an alpha of the 64 bit flash for linux. [http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)
You can still install the 32 bit version with nspluginwrapper and all that stuff, but save yourself the trouble and use Ubuntu repositories.

---

### Post by stchman on 2009-01-27
> **capnthommo said:**
> hi everybody
can anyone help?  when i try to download and install the flash player from adobe i keep getting at the package installer stage

i could use this before i upgraded to 64 bit and also after the upgrade for 2/3 days.  what is going wrong.
i don't think i have done anything major andi have also followed the advice in the multimedia sticky on the multimedia and video forum.
the sound settings are also odd on System - Preferences - Sound.
can anybody help.  it will be greatly appreciated
thanks in advance
nigel

Download the Flash 10 64 bit plugin and install it in your ~/.mozilla/plugins folder.

```

sudo apt-get autoremove flashplugin-nonfree
cd ~
wget http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.d21.1.linux-x86_64.so.tar.gz
sudo apt-get autoremove flashplugin-nonfree
tar -C ~/mozilla/plugins -xvzf ~/libfla*
rm -f ~/libfla*

```

Restart Firefox and all should work.

---

### Post by sir4taye on 2009-01-28
I can't figure out which flash plugin I installed? It is buggy and I'd like to use the one mentioned above, but I don't know how to uninstall the one I chose. Three choices are given after a fresh install to get flash working, Adobe, Gnash, and a swf.... something or other. I don't remember the one I chose, but it's not working well. Can you tell me how to figure what name to use in the apt-get autoremove line listed above?

Actually this fixed the whole issue: [http://ubuntuforums.org/showthread.php?t=1051950&highlight=flash](http://ubuntuforums.org/showthread.php?t=1051950&highlight=flash)

---

### Post by talsemgeest on 2009-01-28
Just open synaptic package manager, and run a search for "flash". That should show you which is installed, then allow you to uninstall it.

---

