---
title: "Was are all flash movies a black screen?"
date: 2009-11-11
forum: New to Ubuntu
---

### Post by listerdl on 2009-11-11
(Sorry for the bad spelling in the title)

Hi I simply cant get my flash to work. Is there a way to remove all flash programs and re-install.

All commands would be appreciated - thanks!

---

### Post by ManiacDan on 2009-11-11
I assume you're using firefox.

Go to tools->add-ons.  
Go to the "plugins" tab.  
Click "disable" on all "shockwave flash" entries.  
Go try to view a youtube video.
Click on the "get flash" option
Get the new version of flash (which is a downloadable .deb file you can double-click to install).
Profit!

---

### Post by listerdl on 2009-11-11
Thanks but it didnt work....the .deb seemed to install fine but even after a re-boot - youtube still tells me that i must download the latest flash player.....

Im at a loss here - am tempted to re-install the OS....bit extreme but....

---

### Post by ManiacDan on 2009-11-11
You never have to re-install the OS, you can try to re-install firefox if you want.

Have you gone back into the plugins screen to see if the new one was re-enabled?

---

### Post by coronacolada on 2009-11-11
I had this problem on my computer at work. I never got it to work in Firefox after days of trying, but I did get it to work on Chromium (the chrome clone) - give it an install and see if it works there. I use that for Flash stuff now, and Firefox for all the rest:

```
sudo gedit /etc/apt/sources.list
```

Add the following lines:

deb [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu) karmic main

```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 0xfbef0d696de1c72ba5a835fe5a9bf3bb4e5e17b5
```

```
sudo apt-get update
```

```
sudo apt-get install chromium-browser
```

Note that I haven't used this install method after upgrading to karmic, so it may have changed. If it doesn't work change the "karmic" to "jaunty" in the above lines. 

Let us know if it works in that browser (or any other, I suppose!)

I know it took some tweaking for me to even get it to run on Chromium, but eventually it worked out.

-tom

sic luceat lux

---

### Post by sandyd on 2009-11-11
> **listerdl said:**
> Thanks but it didnt work....the .deb seemed to install fine but even after a re-boot - youtube still tells me that i must download the latest flash player.....

Im at a loss here - am tempted to re-install the OS....bit extreme but....
run this after installing deb
```

nspluginwrapper -i /usr/lib/adobe-flashplugin/libflashplayer.so
```

p.s. can you do 
```

cat /usr/lib/firefox/plugins
```?
i had the same problem... but that was when i had the x64 beta flash plugin.

---

### Post by listerdl on 2009-11-12
p.s. can you do 
```

cat /usr/lib/firefox/plugins
```

yes and this happened:

henry@TOSHIBA-laptop:~$ cat /usr/lib/firefox/plugins
cat: /usr/lib/firefox/plugins: Is a directory

---

### Post by laidback on 2009-11-12
You may find that removing:-

swfdec-mozilla
gnash

using synaptic could help.

---

