---
title: "Firefox update gone bad"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2008-12-26
After an update for firefox it has been acting quite strange. When trying to go to many normal websites ive been going to(xanga, myspace etc) it crashes. So I went to the terminal and booted it from there. It told me 
Segmentation Fault. I then proceeded to try gksu firefox. Worked. So I went to my home directory. Deleted the .mozilla/firefox. When to run it. No go still the same problems. I've tried reinstalling flash. Reinstalling firefox by doing the following
```
sudo apt-get autoremove firefox
```
and
```
sudo apt-get purge firefox
```
obviously after each unistall I reinstalled it by
```
sudo apt-get install firefox
```
So im not sure what im doing wrong here
I tried kazehaki(sp?) and had the same problems

---

### Post by sayems on 2008-12-26
1. Make sure you don't have any other flash plugin installed on your system:
sudo apt-get remove -y --purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla libflashsupport nspluginwrapper

1.1 To be sure we don't have any other old flash libs let's cleanup the folders where it usually resides:
sudo rm -f /usr/lib/mozilla/plugins/*flash*
sudo rm -f ~/.mozilla/plugins/*flash*
sudo rm -f /usr/lib/firefox/plugins/*flash*
sudo rm -rfd /usr/lib/nspluginwrapper


2. Install ia32-libs and latest nspluginwrapper
sudo apt-get install ia32-libs nspluginwrapper


3. Download the latest flash player from Adobe Labs and extract it:
cd ~
wget [http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/flashplayer10_install_linux_051508.tar.gz)
tar zxvf flashplayer10_install_linux_051508.tar.gz
sudo cp install_flash_player_10_linux/libflashplayer.so /usr/lib/mozilla/plugins/
rm -rf ~/install_flash_player_10_linux/

4. Use nspluginwrapper to install the plugin and link it to firefox
sudo nspluginwrapper -i /usr/lib/mozilla/plugins/libflashplayer.so
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/mozilla/plugins/
sudo ln -sf /usr/lib/nspluginwrapper/plugins/npwrapper.libflashplayer.so /usr/lib/firefox-addons/plugins/

---

### Post by twinaxel on 2008-12-26
Many  thanks certainly cured my Firefox problem.

---

