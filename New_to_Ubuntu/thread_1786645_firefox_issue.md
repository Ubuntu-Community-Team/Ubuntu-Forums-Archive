---
title: "firefox issue"
date: 2011-06-19
forum: New to Ubuntu
---

### Post by scorpious on 2011-06-19
When trying to watch online moves or games( such as [http://www.kongregate.com/games/ArmorGames/one-step-back](http://www.kongregate.com/games/ArmorGames/one-step-back)) on I just get a blank screen. I downloaded chrome to see if it worked on there and it did.

I assume there's some sort of add-on or upgrade but I can't find anything.

---

### Post by silex89 on 2011-06-19
I clicked the link you posted, and everything went fine, you need the Flash Player plug in to run that page. I installed it from the Ubuntu Software Center with Firefox being closed :P


Best Luck :D

---

### Post by scorpious on 2011-06-20
You mean the adobe-flashplugin? I installed that and it but still not having any luck. :(

---

### Post by jtarin on 2011-06-20
Then in the browser address bar type.....```
about:plugins
```
to see if its listed.

---

### Post by donny.davis on 2011-06-20
in firefox go to Tools->Add-ons
inside search area type shockwave flash

good luck

---

### Post by shibu_sawyer on 2011-06-20
whats your Firefox version.. ?

---

### Post by inameiname on 2011-06-20
The flash video works for me on Firefox as well. I'm using Firefox 5 (5.0+build1+nobinonly-0ubuntu0.11.04.1).

Below is a screenshot of my installed video plugins, if curious.

---

### Post by slooksterpsv on 2011-06-20
Weird that you mention this, cause I've had issues with some things not loading right, and it's not until I run a few fixes for flash on my system until it works e.g.:

```


mkdir ~/.config/xserver-xgl
touch ~/.config/xserver-xgl/disable
sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" | sudo tee /etc/adobe/mms.cfg

echo "export MOZ_DISABLE_PANGO=1" | tee -a ~/.bashrc

echo "Section \"DRI\"" | sudo tee -a /etc/X11/xorg.conf
echo " Mode 0666" | sudo tee -a /etc/X11/xorg.conf
echo "EndSection" | sudo tee -a /etc/X11/xorg.conf
echo "" | sudo tee -a /etc/X11/xorg.conf
echo "Section \"Extensions\"" | sudo tee -a /etc/X11/xorg.conf
echo " Option \"Composite\" \"Enable\"" | sudo tee -a /etc/X11/xorg.conf
echo "EndSection" | sudo tee -a /etc/X11/xorg.conf

```

Not sure if any of that will help you, but that's my fix for my system.

EDIT: Oh yeah I reboot after I do all that hehe =P

---

### Post by gandaran on 2011-06-20
> **scorpious said:**
> You mean the adobe-flashplugin? I installed that and it but still not having any luck. :(
adobe-flashplugin should work but you should install instead the flashplugin-installer which is the official ubuntu adobe flash package (remove the adobe) and remove that flashplugin-nonfree-extrasound package too, you don't need it unless or you have some flash sound problem or it may cause conflict.
also if you happen to run ubuntu 64-bits don't install any of these flash packages, get 64-bits flash instead.

---

### Post by nrundy on 2011-06-20
> **scorpious said:**
> When trying to watch online moves or games( such as [http://www.kongregate.com/games/ArmorGames/one-step-back](http://www.kongregate.com/games/ArmorGames/one-step-back)) on I just get a blank screen. I downloaded chrome to see if it worked on there and it did.

I assume there's some sort of add-on or upgrade but I can't find anything.

Hey, install the extension "Flash-Aid"

It fixes almost all Flash related issues in Firefox. It will also automatically update Flash when new versions are released.

---

### Post by lovinglinux on 2011-06-20
> **nrundy said:**
> Hey, install the extension "Flash-Aid"

It fixes almost all Flash related issues in Firefox. It will also automatically update Flash when new versions are released.

Just for the record, it checks for new versions and triggers an alert, but you need to run the Wizard again to install the new version. The Wizard is pretty easy tho.

---

