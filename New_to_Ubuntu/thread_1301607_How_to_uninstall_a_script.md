---
title: "How to uninstall a script?"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by Treeh on 2009-10-26
Hello,

I attempted to install flash for my x64 9.04 installation using this script:

[http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888](http://www.cyberciti.biz/tips/install-flash-10-ubuntu-linux-64bit.html#comment-150888)

However, I have no audio (and according to PulseAudio, it isn't sending out a signal) so I want to uninstall and reinstall using a different method. How exactly do I go about uninstalling this script?

Thanks a ton. I have posted it below.

```
#!/bin/bash
# Script  created by
# Romeo-Adrian Cioaba [email]romeo.cioaba@spotonearth.com[/email]
# Super minor updates by jason.melton[at]gmail[dot]com
# Updates by Alejandro Cuervo 3[at]cuervo[dot]net
# more very minor updates by damien[at]groovey[dot]com
# Released under GPL

echo "Closing Firefox"
sudo killall -9 firefox

echo "Downloading and instaling Getlibs for required libraries"
wget [http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb](http://www.boundlesssupremacy.com/Cappy/getlibs/getlibs-all.deb)
sudo dpkg -i getlibs-all.deb

echo "Removing previous installs of flash:"
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

echo "Installing ia32-libs and nspluginwrapper"
sudo apt-get install ia32-libs nspluginwrapper

echo "Getting libs"
sudo getlibs -p libcurl3
sudo getlibs -p libnss3-1d
sudo getlibs -p libnspr4-0d

echo "Installing Flash Player 10"
cd ~
wget [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz)
tar zxvf install_flash_player_10_linux.tar.gz
sudo mv libflashplayer.so /usr/lib/mozilla/plugins/
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so

echo "Linking the libraries so that firefox can see them."
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

echo "Done :-)"
echo "You may re-start Firefox now"
```

P.S. How do I increase my scrolling rate?

---

### Post by TenPlus1 on 2009-10-26
Like in the actual script, execute these commands to remove any versions of flash on your system:

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

Then pop into Synaptic Packaga Manager and search for "Flash" and install "Flashplugin-installer" to install the latest version...

---

### Post by Treeh on 2009-10-26
> **TenPlus1 said:**
> Like in the actual script, execute these commands to remove any versions of flash on your system:

sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper

Then pop into Synaptic Packaga Manager and search for "Flash" and install "Flashplugin-installer" to install the latest version...

Great, it worked...but it didn't fix my initial problem...I still get no sound from flash videos, and they don't show up in PulseAudio as shown below (note, I'm using the ASUS Xonar STX card: [http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus):](http://www.alsa-project.org/main/index.php/Matrix:Vendor-Asus):)

[IMG]http://imgur.com/0QCY3.png[/IMG]

---

