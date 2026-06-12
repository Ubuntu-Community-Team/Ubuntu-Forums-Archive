---
title: "flash plugins !!"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Dileeshvar on 2009-04-18
When I go to site like [http://www.miniclip.com/games/en/](http://www.miniclip.com/games/en/) in firefox.

I want to play those games but it says flash plugins are missing !!
still I could go to youtube and other websites where everything works well
while here I donno what is the missing plugin and cant find it anywhere ..

Help me sort this !

---

### Post by skintythe1andonly on 2009-04-18
The site works fine for me. What exactly are you using, hardy, intrepid or Jaunty? 32 or 64 bit? How did you install the flash plugins?

---

### Post by atomizer on 2009-04-18
site works good when I try it.


Do you use the adobe flash plugin? (flashplugin-nonfree)

---

### Post by Dileeshvar on 2009-04-18
few games works fine where as others dont
I use Ubuntu 8.04 32 bit and I did install 
the flash plugin when it asked for me to install
when I visited youtube

---

### Post by Crandom on 2009-04-18
Which plugin did you install? The one from Adobe or "Gnash"? You really want the one from Adobe. To get it paste this into a terminal (Application > Accessories > Terminal):
```
sudo apt-get install flashplugin-nonfree
```

---

### Post by Dileeshvar on 2009-04-18
Thanks started installing let you know what happens after completion.

Meanwhile can you tell me if this game works for you ??
[http://www.miniclip.com/games/age-of-speed-2/en/](http://www.miniclip.com/games/age-of-speed-2/en/)

---

### Post by Dileeshvar on 2009-04-18
sorry it sin work !!
The site is asking for adobe shockwave player !!

does anyone know how we can install it ??

---

### Post by Crandom on 2009-04-18
> Platform support

Unlike Flash, the Shockwave browser plugin is not available for Linux or Solaris despite vocal lobbying efforts. However, the Shockwave Player can be installed on Linux with CrossOver or by running a Windows version of a supported browser in Wine (with varying degrees of success)
From [http://en.wikipedia.org/wiki/Adobe_Shockwave](http://en.wikipedia.org/wiki/Adobe_Shockwave)

Basically no (or at least badly with huge difficulty).

---

### Post by Dileeshvar on 2009-04-18
so is there any way other than wine I could install it ??

---

### Post by billgoldberg on 2009-04-18
No.

Adobe doesn't have a Linux shockwave player.

---

### Post by Crandom on 2009-04-18
No, you would have to install wine, then install the WINDOWS version of firefox in wine, then install shockwave for your windows/wine version of firefox and use that.

Firefox wine appdb page: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=14874](http://appdb.winehq.org/objectManager.php?sClass=version&iId=14874)

Instructions for what I said above: [http://anurag.granularproject.org/2008/10/install-shockwave-in-linux-using-wine/](http://anurag.granularproject.org/2008/10/install-shockwave-in-linux-using-wine/)

Alternate instructions: [http://www.ubuntux.org/shockwave-player-ubuntu-linux](http://www.ubuntux.org/shockwave-player-ubuntu-linux)

---

### Post by Dileeshvar on 2009-04-18
So there is no way I play that game eh ??

Thats really bad !! :(

---

### Post by iamleaf on 2009-04-18
I have the same problem. Tried installing it from terminal as well but it says I have the latest one already. But when I visit web pages the damn thing still asks me to install missing plugins. When I let it download and install for me automatically, I always get "failed" manual install? so I click yes. but still the same thing happens over and over. Any help?

---

### Post by gandaran on 2009-04-18
> **iamleaf said:**
> I have the same problem. Tried installing it from terminal as well but it says I have the latest one already. But when I visit web pages the damn thing still asks me to install missing plugins. When I let it download and install for me automatically, I always get "failed" manual install? so I click yes. but still the same thing happens over and over. Any help?
which page asks to install plugins? post the link!
which flash did you install? adobe, gnash or swfdec or all?

---

### Post by iamleaf on 2009-04-18
install_flash_player_10_linux.deb

thats the name of the package that I installed. I installed it from the official Adobe page.[ http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb)]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb)")

When I tried re-installing it manually, it says "re install package?" so I've obviously installed it correctly, but the browsers (both firefox and flock) seem to not recognize it.

---

### Post by gandaran on 2009-04-18
> **iamleaf said:**
> install_flash_player_10_linux.deb

thats the name of the package that I installed. I installed it from the official Adobe page.[ http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb)]("http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_(.deb)")

When I tried re-installing it manually, it says "re install package?" so I've obviously installed it correctly, but the browsers (both firefox and flock) seem to not recognize it.
are you sure you don't have any other flash package installed be it adobe, gnash or swfdec? and flashblock addon?
which ubuntu do you have 8.04 or 8.10? 32-bits or 64-bits?
all updates installed?

---

### Post by iamleaf on 2009-04-18
All updates installed. No I don't have another flash package installed. I have Ubuntu 8.04 and I don't know whether I have 32-bits or 64-bits... How do you find that out?

---

### Post by gandaran on 2009-04-18
> **iamleaf said:**
> All updates installed. No I don't have another flash package installed. I have Ubuntu 8.04 and I don't know whether I have 32-bits or 64-bits... How do you find that out?
type in terminal **uname -a** post the output
also the output of **locate libflash**

---

### Post by iamleaf on 2009-04-18
output of uname -a:
```
Linux leaf-y 2.6.24-23-generic #1 SMP Wed Apr 1 21:47:28 UTC 2009 i686 GNU/Linux

```

output of locate libflash:
```
/usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so
/usr/lib/openoffice/program/libflash680li.so

```

What now?

---

### Post by gandaran on 2009-04-18
> /usr/lib/adobe-flashplugin/libflashplayer.so
/usr/lib/flashplugin-nonfree/libflashplayer.so

you have two adobe flash packages installed! adobe-flashplugin and flashplugin-nonfree, choose one and remove the other, you don't need both, they may even conflict.
now lets see if the flash plugin shows up in firefox
type this code in firefox url bar
```
about:plugins
```
post the full output here.

---

### Post by iamleaf on 2009-04-19
How do I remove one?

Out put of the about:plugins page

```
MIME Type 	         Description 	       Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	        Yes
application/futuresplash 	FutureSplash Player 	spl 	        Yes
```

The other plugins include VLC, TOTEM, Windows Media, etc etc etc.

---

### Post by gandaran on 2009-04-19
> **iamleaf said:**
> How do I remove one?

Out put of the about:plugins page

```
MIME Type 	         Description 	       Suffixes 	Enabled
application/x-shockwave-flash 	Shockwave Flash 	swf 	        Yes
application/futuresplash 	FutureSplash Player 	spl 	        Yes
```

The other plugins include VLC, TOTEM, Windows Media, etc etc etc.
please post the full output, this does not show if firefox has picked up the flash plugin!
to remove any plugin or application open synaptic package manager and scroll down to flashplugin-nonfree or adobe-flashplugin (these packages install exactly the same adobe flash if you are in ubuntu 8.10 it doesn't matter which one you choose) mark for complete removal and click the apply button.
mark for reinstall the one you choose to have installed and apply.

edit:
for ubuntu 8.04 keep the adobe-flashplugin, flashplugin-nonfree in ubuntu 8.04 installs adobe flash 9.

---

### Post by iamleaf on 2009-04-19
This is the full output:
[Plugins]("http://www.freewebtown.com/staticart/AboutPlugins.html")

What now?

---

### Post by gandaran on 2009-04-19
> **iamleaf said:**
> This is the full output:
[Plugins]("http://www.freewebtown.com/staticart/AboutPlugins.html")

What now?
nope, firefox hasn't detected the flash plugin, was this taken after you removed the recommended flash package? which one did you remove? did you reinstall the remaining flash package?
this problem about firefox not being able to pick up the flash plugin is mostly due to a lot of system changes since the first ubuntu 8.04 release, you have to install all updates for it to work, the flash plugin packages installers target flash installation directories that don't exist if you don't update first and then reinstall flash.
try to fix this, use synaptic package manager, click the reload button, install all updates if it shows any and then reinstall the adobe-flashplugin from [adobe.com]("http://get.adobe.com/flashplayer/") it'll work if you do it right.
if you still can't get flash to work this way I will show you later how to install flash manually for firefox but I would prefer you try to get it working the correct way.

---

### Post by iamleaf on 2009-04-19
Still can't get it to wrok. Did all what you instructed, but I still get the "Install missing plugins?" message.

---

### Post by gandaran on 2009-04-19
> **iamleaf said:**
> Still can't get it to wrok. Did all what you instructed, but I still get the "Install missing plugins?" message.
okay, look I don't know and cont guess what you have done so far, so I cant be of any help has you haven't described any details.
installing flash is easy in ubuntu 8.04, all updates installed and just install one adobe flash plugin be it flashplugin-nonfree or adobe-flashplugin, it works! installing a lot of things to make flash work only messes up the system.
well, lets try another way, important, first remove every flash installed, now download the tar.gz package from [adobe.com]("http://get.adobe.com/flashplayer/") to desktop, extract/unpack the package, move the libflashplayer.so file to /home/'user'/.mozilla/plugins (make the plugins folder) thats all you have to do to install flash, restart firefox and check the about: plugins thing if it shows up, go to youtube, try playing the video. 
if it works later you can move the libflashplayer.so file to /usr/lib/mozilla/plugins so all user accounts can have access to it but try the home installation first.
and it would help if you post the link where you get the missing plugins message!

---

### Post by iamleaf on 2009-04-19
Sorry for the lack of info >_<

Its finally worked. Godamn donno why I complicated things. Well Thank you SO MUCH! xD :D

---

