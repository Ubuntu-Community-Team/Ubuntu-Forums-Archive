---
title: "hulu"
date: 2011-04-29
forum: New to Ubuntu
---

### Post by ornothaloapq on 2011-04-29
i was wondering if hulu was watchable on ubuntu 11.04

---

### Post by gandaran on 2011-04-29
> **ornothaloapq said:**
> i was wondering if hulu was watchable on ubuntu 11.04
yes, on any Ubuntu version if you have adobe flash installed and reside in USA.

---

### Post by bford16 on 2011-05-15
I was unable to watch video on hulu.com, or using the Huludesktop application.  In Firefox, hulu.com was asking me to install the latest flash plugin.  Huludesktop was complaining that it "...could not stream this video."

This problem was caused by replacing the 32-bit flash player with the 64-bit "Square" preview release from Adobe.  This plugin works, but it must be installed properly.

For this experiment to work, you must use the latest version of the "preview" 64-bit plugin.  The 64-bit preview release plugin can be downloaded from the following link:
[http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz]("http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_2_p3_64bit_linux_111710.tar.gz")

Extract the contents of the archive to a folder.

The 'libflashplayer.so' file must be installed in two places.

/usr/lib/firefox-addons/plugins/libflashplayer.so
/var/lib/flashplugin-installer/libflashplayer.so (the huludesktop player seems to expect to find the plugin in this location)

It may be necessary to create the /var/lib/flashplugin-installer folder yourself.

In Terminal, do:```
sudo mkdir /var/lib/flashplugin-installer
```

Then copy the plugin there.

Note: It may be possible to install the plugin in just one place, and use a symbolic link in the other; I did not try this.

---

