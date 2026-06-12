---
title: "adobe flash player"
date: 2009-08-24
forum: New to Ubuntu
---

### Post by killersla on 2009-08-24
hi im trying to install adobe flash player so i can watch youtube videos but everytime i download a version nothing seems to happen i have no idea what to do any help please

---

### Post by Katalog on 2009-08-24
When you type "about:plugins" into Firefox does it show that the plugin is active?

---

### Post by SteveNorman on 2009-08-24
Not sure of your experience level, but start at step 5 of this tutorial. Sorry I cant be more helpful as I am in a hurry.

[http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04](http://www.howtoforge.com/the-perfect-desktop-ubuntu-9.04)

---

### Post by killersla on 2009-08-24
my experience level in ubuntu is nil you mention a tutorial where is it?  do know if ive installed any flash plugin

---

### Post by sc00ut on 2009-08-24
Start gnome-terminal and there type:

 sudo apt-get install flashplugin-nonfree

insert sudo password when asked and wait for installation to complete. 
restart web browser go to [http://www.youtube.com](http://www.youtube.com) and enjoy :)

---

### Post by killersla on 2009-08-24
ok just done as you stated but when i go to you tube it says Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/").

---

### Post by Perfect Storm on 2009-08-24
Close the browser and start it up again. 
If it doesn't work , any chance you're using 64-bit?

---

### Post by killersla on 2009-08-24
closed and reopened my browser and still the same.  I am running windows vista ultimate 64bit and ubuntu in a dual boot but i dont know wether ubuntu is running 64 bit

---

### Post by SteveNorman on 2009-08-24
edited my previous to include the tutorial sorry told you I was in a hurry!:KS

---

### Post by killersla on 2009-08-24
sorry im a bit confused that tutorial seems to be how to install ubuntu.  I already have ubuntu installed just cant get a flash player to work to watch youtube videos.

---

### Post by sc00ut on 2009-08-24
I use 9.04 64-bit and it worked with flahsplugin-nonfree, but you can try also with 

sudo apt-get install ubuntu-restricted-extras

this way you get all plugins installed (java, extra fonts, flash, sound and video codecs ...)

---

### Post by Perfect Storm on 2009-08-24
> **killersla said:**
> closed and reopened my browser and still the same.  I am running windows vista ultimate 64bit and ubuntu in a dual boot but i dont know wether ubuntu is running 64 bit

```
uname -a
```

---

### Post by SteveNorman on 2009-08-24
from step 5 it goes into adding new repros which do not by default come with linux distros. so what you will do is add or enable your software sources so you can install the flash plugin and player.

Learning linux is frustrating, sometimes these base tutorials have to much info and sometimes they have to little. the tutorial is 4 pages over all, step 5 is where you want to start from.

---

### Post by keastes on 2009-08-24
ok step by step:

1. download: [flashplayer 10 for ubuntu 8.04+]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_10_linux.deb") [COLOR=Red](warning: direct link!!!)[/COLOR]
2. double click on the file in your download history to run it 
3. package manager opens, click install package (general rule: know what you are installing first)
4. restart firefox 
5. enjoy youtube.

if i missed anything let me know 

kthxbai

edit: added DL link and corrected grammar for clarity

---

### Post by killersla on 2009-08-24
i just installed all the extras from the restricted files in the terminal and still doesnt work.  I typed in uname -a and was given this Linux ubuntu 2.6.27-7-generic #1 SMP Fri Oct 24 06:42:44 UTC 2008 i686 GNU/Linux

---

### Post by SteveNorman on 2009-08-24
he still has to have his restricted repos enabled though right?

---

### Post by killersla on 2009-08-24
im running ubuntu 8.10 everytime i installed 9 after about 5 mins it always froze

---

### Post by killersla on 2009-08-24
i have followed all the steps in the tutorial from 5 but im still getting the same message from youtube 

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. [Get the latest Flash player]("http://www.adobe.com/go/getflashplayer/").

---

### Post by killersla on 2009-08-24
this is getting qwite frustrating now i seem to have installed every flash player and nothing seems to work

---

### Post by Perfect Storm on 2009-08-24
Can you attach your ```
about:plugins
```
It may be the Open Source flash that are teasing.

Also uninstall gnash, if its installed.

---

### Post by argos3016 on 2009-08-24
Try:(in a terminal)

firefox -ProfileManager
and make new profile

---

### Post by argos3016 on 2009-08-24
Works?

---

### Post by killersla on 2009-08-24
im sorry dont know what to do there

Can you attach your  	Code:
 	about:plugins 
It may be the Open Source flash that are teasing.

Also uninstall gnash, if its installed.

---

### Post by killersla on 2009-08-24
> **argos3016 said:**
> Try:(in a terminal)

firefox -ProfileManager
and make new profile



WHHOOO   great work argos3016 works a treat now.    I would like to understand this a bit better so anyone could explqain why making a new profile in firfox worked for me?

---

### Post by sc00ut on 2009-08-24
//sudo apt-get remove gnash

//try that to remove gnash if its installed

great job argos3016

---

### Post by argos3016 on 2009-08-24
I recommend this , because my firefox fails sometimes and I add a new firefox profile.
Maybe flash will be work. 
firefox -ProfileManager
Create Profile
Please, try it!!

---

### Post by argos3016 on 2009-08-24
I don't know , but works!

---

### Post by argos3016 on 2009-08-24
If you have bookmarks , make an a backup copy and delete the previous profile

---

### Post by killersla on 2009-08-24
now the problem i have everytime i open firfox it doesnt work on youtube so evertyime i have to open it with a new profile is there anyway to set my new profile as default so it works every time.

Thanks for all the help so far

---

### Post by killersla on 2009-08-24
ok now everytime i try to open firefox i get this message

Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.
although i can open it in the terminal i tried to bookmark it and i deleted the old profile but it seems to have messed things up a bit

---

### Post by SteveNorman on 2009-08-24
at a terminal```
killall firefox
```

then reopen it.

I wonder if you need to reinstall firefox as it seems to be where the problem lies. Also that tutorial was for 9, didnt realize you where running 8.10

you may have to redo the tutorial changing all instances of repro sources to read 8.10 instead of 9.04

---

### Post by argos3016 on 2009-08-24
Strange Firefox!
If you love MUCH firefox , try the trick of SteveNorman and ProfileManager.
If you don't love firefox try Google Chrome

---

### Post by SteveNorman on 2009-08-24
this appears to be directed at 8.10

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by killersla on 2009-08-24
just done killall firefox but still got same message Firefox is already running, but is not responding. To open a new window, you must first close the existing Firefox process, or restart your system.

might try google chrome.

is there a command line in terminal to get and install chrome?

---

### Post by argos3016 on 2009-08-24
Is already unstable but in my ubuntu works well
[www.ubuntugeek.com/install-chromium-google-chrome-web-browser-in-ubuntu.htm](www.ubuntugeek.com/install-chromium-google-chrome-web-browser-in-ubuntu.htm)

---

### Post by argos3016 on 2009-08-24
Sometimes it kills itself , the firsts times , but after this it surfs with more speed
Sorry for english

---

### Post by argos3016 on 2009-08-24
I think that chrome is not in repo if you want an stable version.
There is on unstable

---

### Post by argos3016 on 2009-08-24
[www.ubuntugeek.com/install-chromium-google-chrome-web-browser-in-ubuntu.htm](www.ubuntugeek.com/install-chromium-google-chrome-web-browser-in-ubuntu.htm)

---

### Post by argos3016 on 2009-08-24
Sorry:
[http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb](http://www.google.com/chrome/intl/en/eula_dev.html?dl=unstable_i386_deb)

---

### Post by SteveNorman on 2009-08-24
in a terminal get the process id number
, then use the number to kill firefox by replacing process_id_number below with that number

```
ps aux |grep fire
sudo kill -9 process_id_number
```

---

