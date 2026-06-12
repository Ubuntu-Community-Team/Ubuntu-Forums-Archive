---
title: "where to get flash for amd 64"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by orky7 on 2009-08-06
hi i just install google chrome and the flash is not working so i follow the link and install it but it says that its not for amd64 so where to get amd64 flash for the chrome.....i already uninstall flash just in case for some clash....

---

### Post by NagWolf on 2009-08-06
Hi,
In your Synaptic Package Manager, search for Flash, scroll down a bit and make sure both 'flashplugin-installer ' as well as 'flashplugin-nonfree' is selected. If they are, just Mark for Re-installation and Apply... should sort that for you

HtH

---

### Post by philinux on 2009-08-06
I think it's the same libflashplayer.so as I am using on my 64 bit install. It just needs to go in the chrome profile somewhere.

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by NagWolf on 2009-08-06
this could also maybe help...
[http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml](http://news.softpedia.com/news/How-to-Install-Adobe-Flash-Player-64-bit-on-Ubuntu-8-10-98076.shtml)

---

### Post by philinux on 2009-08-06
The .so file needs to be copied here.

/usr/lib/chromium-browser/plugins/flashplugin.so

---

### Post by orky7 on 2009-08-06
now i got a problem i was installing flash via synaptic and i accidentally hit the restart button so when i restart the system and went to synaptic again it says there is an error u have to do it manually and gives a command "sudo dpkg -configur -a" and by clicking ok or cancel whole of synaptic get closed. then i type the above command and happen nothing saying more parameter are needed so what to do now......

---

### Post by drs305 on 2009-08-06
> **orky7 said:**
> now i got a problem i was installing flash via synaptic and i accidentally hit the restart button so when i restart the system and went to synaptic again it says there is an error u have to do it manually and gives a command "sudo [COLOR="Red"]**dpkg -configur -a**[/COLOR]" and by clicking ok or cancel whole of synaptic get closed. then i type the above command and happen nothing saying more parameter are needed so what to do now......

If you typed it as above, there is a typo. Enter it as:
```
sudo dpkg --configure -a
```
It will ask for your password. Enter it. You won't see it as you type - it will look like nothing is happening. Press ENTER after you have typed it.

---

### Post by orky7 on 2009-08-06
thanks man it works.....i installed it but still chrome is saying i dont have a flash player so what to do next.......

---

### Post by orky7 on 2009-08-06
i just made a folder in /opt/google/chrome/plugins and put the libflashplugin.so file in it and also changed execution command but not working i just found that my firefox also now don't play flash. any help..

---

### Post by drs305 on 2009-08-06
> **orky7 said:**
> i just made a folder in /opt/google/chrome/plugins and put the libflashplugin.so file in it and also changed execution command but not working i just found that my firefox also now don't play flash. any help..

For firefox, do you have a current copy of libflashplayer.so in /usr/lib/mozilla/plugins/ ?

Depending on what you installed via synaptic, that may not be enough. The scripts I've used to install flash in firefox remove all other instances of flash before installing the new libflashplayer.so  So if you have installed any flash via synaptic it could be interfering with the previous Flash 10 Alpha setup for use in Firefox.

---

### Post by orky7 on 2009-08-06
problem SOLVED thanks to all of u......yup u people r right i need to put that under a plugins folder the .so file and it work for chrome also just create a folder "plugins" in /opt/google/chrome and put the .so file there and watch videos thanks......

---

### Post by Clorow on 2009-08-06
If nothing else works, try [Gnash]("apt:mozilla-plugin-gnash") if you just use it for watching YouTube.

---

### Post by marcio_mi on 2009-08-08
Hey Orky7,

can you tell me exactly what you did? because I am still not able to use flash with google chrome. I downloaded the flash player for x64, and put the file in the plugins directory for both firefox and chrome. It works fine in firefox, but when I try to enable the plugins with chrome it tells me that it is the wrong ELFclass.

thank you

---

