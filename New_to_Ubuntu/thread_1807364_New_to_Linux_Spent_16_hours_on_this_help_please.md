---
title: "New to Linux Spent 16 hours on this help please"
date: 2011-07-19
forum: New to Ubuntu
---

### Post by kornleash on 2011-07-19
hello i am attepting to install flash on my girlfriends mothers system and i can not get it, i am fairly new to linux so i do not know alot of commands ect. but i do know alot about computers in general, before they asked me to do it they tried for a few days and there are 50+ different flash player downloads on the system, when i tried to go into the package manager to install flash it will not let me install it and it gives me this error message "E: flashplugin-nonfree: Package is in a very bad inconsistent state - you should  reinstall it before attempting a removal." ive been reading posts and trying different things for 16+ hours now and i am at wits end. i tried the command "sudo apt-get remove flashplugin-nonfree" and was given the answer "Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  flashplugin-nonfree
0 upgraded, 0 newly installed, 1 to remove and 24 not upgraded.
1 not fully installed or removed.
E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the download directory"

im not sure what this means but any help is very much appreciated. thank you in advance, Curtis

---

### Post by bodhi.zazen on 2011-07-19
First, run these commands as root (best to simply sudo -i)

Second, make sure no other package manager is running (synaptic, add/remove programs, etc).

Then try

[http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/](http://blog.bodhizazen.net/linux/apt-get-how-to-fix-very-broken-packages/)

---

### Post by kornleash on 2011-07-19
ok thank you so much for the reply, i am currently trying this and will update you after i have tried,

---

### Post by beew on 2011-07-19
The easiest way is to install the flash-aid addon for Firefox and then run the script. It will automatically update flash, remove conflicting versions and optimize it for your system.

---

### Post by kornleash on 2011-07-19
ok i tried this and everything was going along with the post but when i got to this part.

"
To fix the problem I needed to manually remove the package.
 

"cd /var/lib/dpkg/info
sudo rm flashplugin-nonfree.*"


and entered that into terminal i was given this reply


"mintbox2 info # cd /var/lib/dpkg/info
mintbox2 info # sudo rm flashplugin-nonfree
rm: cannot remove `flashplugin-nonfree': No such file or directory"

it says there is no such directory and when i go into 
computer>usr>lib>flashplugin-nonfree, it says there are 0 files. 
im not sure what i am doing wrong.

---

### Post by kornleash on 2011-07-19
> **beew said:**
> The easiest way is to install the flash-aid addon for Firefox and then run the script. It will automatically update flash, remove conflicting versions and optimize it for your system.



how do i do this? sorry new to linux, i personally am a windows user but i enjoy the linux OS and would like to switch for myself but if i cant even figure out flash there is something wrong. lol any help is appreciated

---

### Post by beew on 2011-07-19
> **kornleash said:**
> how do i do this? sorry new to linux, i personally am a windows user but i enjoy the linux OS and would like to switch for myself but if i cant even figure out flash there is something wrong. lol any help is appreciated

Install flash-aid from here
[https://addons.mozilla.org/en-US/firefox/addon/flash-aid/](https://addons.mozilla.org/en-US/firefox/addon/flash-aid/)

Then restart Firefox, run Flash-aid in Wizard mode.

BTW, make sure you have closed all instances of package managers when you run the script (i.e update manager, Synaptic and the Software Centre. As a general rule, at any time at most one of these can be activated)

---

### Post by kornleash on 2011-07-19
> **beew said:**
> The easiest way is to install the flash-aid addon for Firefox and then run the script. It will automatically update flash, remove conflicting versions and optimize it for your system.


thank you so much!!!!!!!!!!!!!!! it worked!!!!!!!!!!!!

---

### Post by beew on 2011-07-19
> **kornleash said:**
> thank you so much!!!!!!!!!!!!!!! it worked!!!!!!!!!!!!
You are welcome. Please mark the thread as solved (go to thread tools and choose mark as solved in drop down)

---

### Post by kornleash on 2011-07-19
ok, you sir are a genius (:

---

### Post by kornleash on 2011-07-19
> **beew said:**
> You are welcome. Please mark the thread as solved (go to thread tools and choose mark as solved in drop down)



how do i mark it solved i seen it when i first posted the thread but idk how to get back to it, sorry nooby question

---

### Post by beew on 2011-07-19
> **kornleash said:**
> ok, you sir are a genius (:

Not me, thanks to Lovinglinux who created the addon, he is a frequent member on this forum and a really helpful guy. :)

---

### Post by bodhi.zazen on 2011-07-19
As long as apt-get is working you are good to go, but if apt-get is still broken you may have some clean up to do.

---

### Post by pjd99 on 2011-07-19
> **beew said:**
> The easiest way is to install the flash-aid addon for Firefox and then run the script. It will automatically update flash, remove conflicting versions and optimize it for your system.

+1 used flash-aid for the first time about 30 minutes ago. Worked like a charm.

---

### Post by psycho5 on 2011-07-19
>  how do i mark it solved i seen it when i first posted the thread but idk how to get back to it, sorry nooby question  

on the top bar right above where the thread starts there are drop down options, select thread tools > mark this thread as solved

---

### Post by lovinglinux on 2011-07-19
> **kornleash said:**
> thank you so much!!!!!!!!!!!!!!! it worked!!!!!!!!!!!!

> **kornleash said:**
> ok, you sir are a genius (:

> **beew said:**
> Not me, thanks to Lovinglinux who created the addon, he is a frequent member on this forum and a really helpful guy. :)

Thanks :D

> **bodhi.zazen said:**
> As long as apt-get is working you are good to go, but if apt-get is still broken you may have some clean up to do.

Indeed. Flash-Aid solves the flash problem, but it doesn't use the package manager by default. You might still need to fix the main underlying issue with the package manager.

---

