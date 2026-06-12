---
title: "Gutsy~flash player is not installing"
date: 2009-02-06
forum: New to Ubuntu
---

### Post by KEE on 2009-02-06
problems with installing flash player 10 .( dam you mac4linux!) i had flash players problems after i installed mac4linux so i had reinstall :( mac4linux broke mt browser, audio on streams  on was really messed up. its really bad!, anyway it was fine before so i reinstalled but im haveing problems getting ```
/usr/lib/firefox-3.0
``` to work, keep saying thats its invalid lol please help

these are steps i took 

 ```
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
```
```
 tar -xvzf install_flash_player_10_linux.tar.gz
```
```
cd install_flash_player_10_linux/
```

```
sudo ./flashplayer-installer
```

```
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/firefox-3.0

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/firefox-3.0.1
```

---

### Post by spcwingo on 2009-02-07
Have you tried manually placing libflashplayer.so in /usr/lib/firefox-addons/plugins?  I'm not sure about Gutsy, but this will work in Hardy.

---

### Post by Swiekvor on 2009-02-07
you can't place libflashplayer.so in /usr/lib/firefox-addons/plugins in ubuntu

---

### Post by Binny88 on 2009-02-07
Use adobeflash player 9, I had a few issues with flashplayer 10

---

### Post by gandaran on 2009-02-07
> **KEE said:**
> problems with installing flash player 10 .( dam you mac4linux!) i had flash players problems after i installed mac4linux so i had reinstall :( mac4linux broke mt browser, audio on streams  on was really messed up. its really bad!, anyway it was fine before so i reinstalled but im haveing problems getting ```
/usr/lib/firefox-3.0
``` to work, keep saying thats its invalid lol please help

these are steps i took 

 ```
wget -c http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.tar.gz
```
```
 tar -xvzf install_flash_player_10_linux.tar.gz
```
```
cd install_flash_player_10_linux/
```

```
sudo ./flashplayer-installer
```

```
Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/firefox-3.0

WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): /usr/lib/firefox-3.0.1
```

do it the easy way! no need to run the installer, just move the libflashplayer.so file to /home/'user'/.mozilla/plugins (make the plugins folder) or if you have more than one user account move it to /usr/lib/mozilla/plugins.
you can also install flash in gutsy directly from adobe.com using firefox, to do that disable the ubufox addon close and restart firefox now go to any webpage with flash content and click install on that missing plugin message.

---

### Post by KEE on 2009-02-07
> **Binny88 said:**
> Use adobeflash player 9, I had a few issues with flashplayer 10

well i didnt have problems before. i had adobeflash player 10 working great until I installed mac4linux. it broke some plugins now i need to redo them. still need help please

---

### Post by sqrooup on 2009-02-07
Try the following:

System>Administration>Synaptic Package manager
(Input your password) 
Search; flash
find within list, both Gnash and Swfdec, if these are marked as installed, mark them for un-installing.
find either adobe-flashplugin or flashplugin-nonfree (they are both identical), mark for instillation and install

---

### Post by KEE on 2009-02-07
> **sqrooup said:**
> Try the following:

System>Administration>Synaptic Package manager
(Input your password) 
Search; flash
find within list, both Gnash and Swfdec, if these are marked as installed, mark them for un-installing.
find either adobe-flashplugin or flashplugin-nonfree (they are both identical), mark for instillation and install

i dont think that plugin works :/ i already had that installed and i still wasnt able to watch and videos. still need help with finishing off the installation for abobe flashplayer 10 please

---

### Post by spcwingo on 2009-02-07
> **Swiekvor said:**
> you can't place libflashplayer.so in /usr/lib/firefox-addons/plugins in ubuntu

Why can you not?

---

