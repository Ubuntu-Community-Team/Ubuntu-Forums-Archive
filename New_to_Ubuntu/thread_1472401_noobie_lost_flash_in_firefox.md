---
title: "noobie lost flash in firefox"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by maja_z on 2010-05-04
OK, so I'm on Karmic Koala running Firefox 3.5.9. 
As far as I know  everything is up to date (as in I always click yes to anything update manager says :)

I have always had problems with flash videos playing - essentially they only work after vigorous clicking on the buttons. Apparenty this is to do with some sort of incompatibility with Compiz. 

So I was looking for a fix, googling around, and tried following various work arounds that involved uninstalling and reinstalling the flash installer etc. and have now managed to make it even worse. 

Now I just want a clean start, so:
1. I go to synaptic package manager and select flashplugin-installer and flashplugin-nonfree for complete removal. 
2. I also do 
sudo rm -f /usr/lib/mozilla/plugins/*flash*
and
sudo rm -f /usr/lib/firefox-addons/plugins/*flash*
3. then I open ff and find e.g. a BBC video, which says "you do not have the right something installed" and follow the link to adobe, where i download the file install_flash_player_10_linux.tar.gz
4. adobes instructions are complete bollocks, but i do
tar xf install_flash_player_10_linux.tar.gz
and
cp libflashplayer.so /usr/lib/mozilla/plugins/
cp libflashplayer.so /usr/lib/firefox-addons/plugins/
5. Now I open ff and ... flash doesn't work. Most websites say "you need to upgrade your flash player" and send me to adobe again.

6. on some websites ff pops up a little message saying "additional plugins are required to display all the media on this page" and when I click Install missing plugins it suggests "adobe flash player (installer)" and when I select it it then gives a warning "package flashplugin-installer is already installed"..

Please help! I don't care if I have to click the play button 29 times, I just want it back!!

thanks!

m.

---

### Post by maja_z on 2010-05-04
Also, I've just noticed that some threads say the libflashplayer.so file should go into the ~/.mozilla/plugins/folder.

But I do not have such a folder! My root .mozilla folder has two folders (extensions and firefox) and a FILE plugins!?

---

### Post by xumuk37 on 2010-05-04
libflashplayer.so has to go to /usr/lib/mozilla/plugins... then just restart the browser

---

### Post by nitstorm on 2010-05-04
ubuntuforums.orgubuntuforums.org/newreply.php
Maybe [this]("http://ubuntuforums.org/showthread.php?t=1193567") could help?

---

### Post by maja_z on 2010-05-04
nitstorm, you're a star! 
this [Get64bitFlash ]("http://ubuntuforums.org/showthread.php?t=1358591")link worked like a charm! even no more vigorous clicking required!

Thank you soooo much!

---

### Post by nitstorm on 2010-05-04
ubuntuforums.orgubuntuforums.org/newreply.php
No problemo maja_z. The real star here is lovinglinux for his awesome post on firefox optimization and troubleshooting :) Thanks lovinglinux for helping us all out . 

Cheers!

---

### Post by lovinglinux on 2010-05-05
> **nitstorm said:**
> ubuntuforums.orgubuntuforums.org/newreply.php
No problemo maja_z. The real star here is lovinglinux for his awesome post on firefox optimization and troubleshooting :) Thanks lovinglinux for helping us all out . 

Cheers!

Thanks a lot, but the real star on this case is michael37, since I only provide the link to his thread/tool  :) Get64bitFlash works like a charm.

Glad it worked anyway ;)

---

