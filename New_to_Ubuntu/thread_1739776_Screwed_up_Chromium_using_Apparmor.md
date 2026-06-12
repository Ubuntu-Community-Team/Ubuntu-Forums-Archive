---
title: "Screwed up Chromium using Apparmor"
date: 2011-04-26
forum: New to Ubuntu
---

### Post by DGINSD on 2011-04-26
I used 
```
 sudo aa-enforce /etc/apparmor.d/usr.bin.chromium-browser
```
to activate the chromium apparmor profile and also 
```
sudo aa-enforce /etc/apparmor.d/usr.bin.firefox-3.5
```
to activate the Firefox profile, Firefox seems to still work OK but chromium (the browser I regularly use) returns nothing but errors how do I deactivate the profile?

I guess its what I get for using things before really understand them, Duh!

---

### Post by Spyderkid on 2011-04-26
to fix just go to synaptic package manager under administration, find chromium, right click and choose re-install and remove apparmor

---

### Post by oldos2er on 2011-04-26
Directions here on disabling profiles: [http://wiki.apparmor.net/index.php/AppArmor_Failures#Disabling_the_profile](http://wiki.apparmor.net/index.php/AppArmor_Failures#Disabling_the_profile)

---

### Post by DGINSD on 2011-04-26
> **oldos2er said:**
> Directions here on disabling profiles: [http://wiki.apparmor.net/index.php/AppArmor_Failures#Disabling_the_profile](http://wiki.apparmor.net/index.php/AppArmor_Failures#Disabling_the_profile)
 
Excelent thank you for the link.

In the interest of learning on my part, on the instructions in the link sudo didn't work I had to actually open a root terminal any idea why that is?

Also the Chromium profile was just there ( I'd assume since install) as I sure didn't write it LOL!  All I did was activate it. What would cause it to not work or deny connection? The Firefox profile seemed to work just fine.

---

### Post by oldos2er on 2011-04-26
I'm afraid I'm not at all knowledgeable about apparmor, but it sounds as though the chromium-browser profile you have (from the package apparmor-profiles, I'm guessing) needs some heavy tweaking. I think the Firefox one has been tested more.

There is some more info here: [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

---

### Post by DGINSD on 2011-04-27
> **oldos2er said:**
> I'm afraid I'm not at all knowledgeable about apparmor, but it sounds as though the chromium-browser profile you have (from the package apparmor-profiles, I'm guessing) needs some heavy tweaking. I think the Firefox one has been tested more.

There is some more info here: [http://ubuntuforums.org/showthread.php?t=1008906](http://ubuntuforums.org/showthread.php?t=1008906)

Fantastic, looks like I have yet another project to study and learn. :)

---

