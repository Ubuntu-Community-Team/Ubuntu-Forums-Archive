---
title: "flashplugin-nonfree trouble"
date: 2009-06-01
forum: New to Ubuntu
---

### Post by Roshni on 2009-06-01
hi
im running 8.10 on my system. i recently upgraded to it from 8.04.

everytime i try to update my system or install any package, it stops at this
Setting up flashplugin-nonfree (10.0.22.87ubuntu1~intrepid1) ...
Downloading...
--2009-06-01 13:51:10--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
Resolving fpdownload.macromedia.com... 60.254.166.70
Connecting to fpdownload.macromedia.com|60.254.166.70|:80... failed: Connection timed out.
Retrying.

--2009-06-01 13:54:20--  (try: 2)  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
Connecting to fpdownload.macromedia.com|60.254.166.70|:80... 



any idea what i can do to resolve this?

---

### Post by superprash2003 on 2009-06-01
try this** sudo apt-get remove flashplugin-nonfree** .. and then install flash again

---

### Post by wpshooter on 2009-06-01
> **superprash2003 said:**
> try this** sudo apt-get remove flashplugin-nonfree** .. and then install flash again

I would do this but when I got ready to install Flashplayer, I would go to the REAL Adobe website and download and install the latest full version of Adobe Flashplayer for Linux, I think you will find that that will give you a much better/fuller Flash experience than just trying to install Flashplugin-nonfree from Synaptic.

---

