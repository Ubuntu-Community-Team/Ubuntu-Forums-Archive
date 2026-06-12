---
title: "Firefox Bricked"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by sama_j on 2009-03-06
```
E: xulrunner-1.9: subprocess post-installation script returned error exit status 127
E: firefox-3.0: dependency problems - leaving unconfigured
E: firefox-3.0-branding: dependency problems - leaving unconfigured
E: firefox: dependency problems - leaving unconfigured
E: xulrunner-1.9-gnome-support: dependency problems - leaving unconfigured
E: firefox-3.0-gnome-support: dependency problems - leaving unconfigured
E: system-tools-backends: subprocess post-installation script returned error exit status 1


```

^ There is the output from the pac-man when I applied the update this morning. I got the tar.gz from the web and have Firefox running again, I also have Flock. There is no flash for me, and the install from the Adobe site does not help me, I installed flash non-free but it has not helped.
If you can help that would be great. Thanks, Sama.

---

### Post by Rallg on 2009-03-06
Earlier today, some users reported problems in today's update, FF 3.0.7. Are you using 3.0.7 ?

---

### Post by SuperSonic4 on 2009-03-06
pacman? Are you using **arch**? If so try ```
sudo pacman -Syy
``` which will refresh your repositories and then ```
sudo pacman -Syu
``` which is system upgrade.

If you're in **ubuntu** use ```
sudo apt-get update
``` or ```
sudo apt-get install -f
``` which forcibly installs dependencies

---

### Post by sports fan Matt on 2009-03-06
Rall, my system earlier today had issues with 3.0.7..Im not sure what happened though

---

### Post by sama_j on 2009-03-06
Yep 3.0.7

I have the browser working again but flash is dead. I dont think it is 3.0.7 that I got going d/l'd firefox through lynx at the moz site, extracted and ran from the directory.

---

### Post by sama_j on 2009-03-06
> **SuperSonic4 said:**
> pacman? Are you using **arch**? If so try ```
sudo pacman -Syy
``` which will refresh your repositories and then ```
sudo pacman -Syu
``` which is system upgrade.

If you're in **ubuntu** use ```
sudo apt-get update
``` or ```
sudo apt-get install -f
``` which forcibly installs dependencies

Sorry not arch. Synaptic pac-man sorry for the confusion. I get the same error message with **install -f**

---

### Post by neu2buntu on 2009-03-06
since i have done todays firefox update (running 8.10) it is crashing steady.... i have just about been able to run "top" and it is showing a high % in "wa" whatever that is i dont know!!!!    i hate updates sometimes ,especially when i had my system running brilliant!!! also noticed "master" showing up briefly in top and have never seen it since ive been on ubuntu!!!!  i havnt needed to reinstall in about @least a year and dont want to now as i have fine tuned my os the way i like it...wha* th* fu** !!! also when the crashes happen the hard disk is working overtime and i have had to do the dreaded hardkill switch(which will probably kill my harddrive someday!!)...is any1 else experiencing this since the upgrade of firefox or am i just DOOMED!!!!    thanks in advance for helping

---

### Post by sama_j on 2009-03-06
**neu2buntu**

That happened to me a couple of times before this update.
Probably doesn't help to know that!

---

### Post by neu2buntu on 2009-03-06
now firefox is behaving itself and also running rhythmbox radio too,but something was still amiss earlier............hopefully all will be ok now!!!  my system was running at about 10% so it wasnt an issue with memory ,just when you see your harddrive light and hear hardrive working overtime you start worrying!!! ....i checked system log but couldnt see anything out of the ordinary there.....hopefully it was just a glitch in the matrix....lol....prob the next time i bootup the same thing will happen awww well!!!   i will stay posted to see how every1 else is getting on with the latest update of firefox!!!!

---

### Post by crunchfighter on 2009-03-06
I'm running 3.0.7 and having trouble with speed dial not loading the thumbnails.  The add-on window in firefox shows I need a restart, but the restart doesn't take.  It continuously says "restart firefox to complete your changes".

I just did a clean install after swapping hard-drives.  It was so much smoother yesterday!  Rats.

---

### Post by neu2buntu on 2009-03-06
reply to sama_j ... every bit of feedback does help,r u still having issues with firefox or is all ok,....?...your web browser is prob 1 of the most important apps that u use and when it fails your in trouble!!!!....i have changed my bottom panel to avant window navigator yesterday and thought that was part of the problem,but did this ages ago and had no bother..........i run ubuntu on 3 systems and never have any trouble .... as i said in last post ,now everything ok,just wory about next reboot!!!(

---

### Post by sama_j on 2009-03-06
I have Firefox back and installed Flock as a backup so I don't need to use Lynx if one breaks. The only prob now is flash wont work. I have tried the adobe one and the non-free one but there is no Flash.

---

### Post by crunchfighter on 2009-03-06
I got mine working again by using the firefox profilemanager to construct a new profile.  One of my add-ons were apparently causing a hang-up.

---

