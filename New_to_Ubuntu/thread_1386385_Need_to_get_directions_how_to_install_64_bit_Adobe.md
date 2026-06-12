---
title: "Need to get directions how to install 64 bit Adobe flashplayer 9.10 Karmic"
date: 2010-01-20
forum: New to Ubuntu
---

### Post by Throbbing Gristle on 2010-01-20
I need to try to install this from source because of choppy Video in full screen on hulu. I have a Amd 64 bit Compaq Presario pc3200 Model # SR1750NX . I am running 9.10 64 bit Karmic. I am a new be Would like to know where to get instructions on this sort of thing. I am not familiar with tar biz and such. Thanks

The restricted Extras version of Adobe I currently have is in question.

---

### Post by Throbbing Gristle on 2010-01-20
[http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

The instructions here The very fist step is not working?

---

### Post by plucky on 2010-01-20
> **Throbbing Gristle said:**
> [http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/](http://nxadm.wordpress.com/2009/04/26/install-64-bit-adobe-flash-player-on-ubuntu-904/)

The instructions here The very fist step is not working?

What is not working?

Use the [(now here).](http://labs.adobe.com/downloads/flashplayer10_64bit.html) link

---

### Post by Throbbing Gristle on 2010-01-20
cd Desktop
tar xvzf    So its on my desktop I enter this command I gettar: Old option `f' requires an argument.

---

### Post by 73ckn797 on 2010-01-20
> **Throbbing Gristle said:**
> I need to try to install this from source because of choppy Video in full screen on hulu. I have a Amd 64 bit Compaq Presario pc3200 Model # SR1750NX . I am running 9.10 64 bit Karmic. I am a new be Would like to know where to get instructions on this sort of thing. I am not familiar with tar biz and such. Thanks

The restricted Extras version of Adobe I currently have is in question.

This might be what you need: [http://get.adobe.com/flashplayer/?promoid=BUIGP](http://get.adobe.com/flashplayer/?promoid=BUIGP)

Select the 64 bit download.

It will need to be the "deb" extension and can be easily installed by right clicking the file and installing with the "Gdebi Package Installer".

---

### Post by howefield on 2010-01-20
Go to Places and select Home.

Press the ctrl + H keys to reveal the hidden folders and copy the new file from our desktop to .mozilla/plugins

If there isn't a plugins folder there, create it.

---

### Post by tom.swartz07 on 2010-01-20
> **Throbbing Gristle said:**
> I need to try to install this from source because of choppy Video in full screen on hulu. I have a Amd 64 bit Compaq Presario pc3200 Model # SR1750NX . I am running 9.10 64 bit Karmic. I am a new be Would like to know where to get instructions on this sort of thing. I am not familiar with tar biz and such. Thanks

The restricted Extras version of Adobe I currently have is in question.

Rather than paste links, ill tell you straight up.

This is by far the easiest way- it allows you to install the Official flash for Linux x64 systems.

Before you start, remove all of the third-party flash packages from synaptic, in particular- swfdec and gnash players.

Download the new flash plug-in @ [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Extract the archive from the download link above.
Close all browsers.
Hit ALT+F2 and type
```
gksu nautilus /usr/lib/flashplugin-installer
```
This will open up a new window.
Copy and paste the extracted libflashplayer.so file into this folder, overwriting the current version.
If you have Firefox installed you will also need to install the plugin to the following folder. 
Hit Alt+F2 and type
```
gksu nautilus /usr/lib/mozilla/plugins
```
Paste the same file into this folder, again agreeing to overwrite the current version 

Theres a PPA if you want to use it to keep your flash updated (if youre using karmic)
```
sudo add-apt-repository ppa:sevenmachines/flash
```
If you are still having problems, update it with 
```
sudo apt-get update && sudo apt-get install flashplugin64-installer

```

---

### Post by Throbbing Gristle on 2010-01-21
> **tom.swartz07 said:**
> Rather than paste links, ill tell you straight up.

This is by far the easiest way- it allows you to install the Official flash for Linux x64 systems.

Before you start, remove all of the third-party flash packages from synaptic, in particular- swfdec and gnash players.

Download the new flash plug-in @ [http://labs.adobe.com/downloads/flashplayer10_64bit.html](http://labs.adobe.com/downloads/flashplayer10_64bit.html)

Extract the archive from the download link above.
Close all browsers.
Hit ALT+F2 and type
```
gksu nautilus /usr/lib/flashplugin-installer
```This will open up a new window.
Copy and paste the extracted libflashplayer.so file into this folder, overwriting the current version.
If you have Firefox installed you will also need to install the plugin to the following folder. 
Hit Alt+F2 and type
```
gksu nautilus /usr/lib/mozilla/plugins
```Paste the same file into this folder, again agreeing to overwrite the current version 

Theres a PPA if you want to use it to keep your flash updated (if youre using karmic)
```
sudo add-apt-repository ppa:sevenmachines/flash
```If you are still having problems, update it with 
```
sudo apt-get update && sudo apt-get install flashplugin64-installer

```


 Thanks the bottom part worked I could not get the command for ]gksu nautilus /usr/lib/flashplugin-installer to work . The hulu thing looks like a on going prob. The shame of it all is using a 52 inch LCD in a itty bitty pict..........because full screen is useless.

---

