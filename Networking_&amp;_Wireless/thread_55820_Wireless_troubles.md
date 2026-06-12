---
title: "Wireless troubles"
date: 2005-08-10
forum: Networking &amp; Wireless
---

### Post by Fed on 2005-08-10
Hi,
Im quite new to the world of Linux and Ubuntu, but so far have gotten through a number of initials hurdles with success. However, I cant seem to figure out what is going wrong with my wireless. The Ubuntu is installed on an IBM T21 laptop, with a Netgear WG511v1 (Made in Taiwan - Prism chipset) PCMCIA card, which according to what Ive read so far is completely compatible with Ubuntu and should run out-of-the-box so to speak. So here is where I run into a problem, Ive installed the OS and it found and installed drivers for my Netgear card as it was supposed to and everything was going great. Ubuntu started but I didnt have net access straight off to my surprise. I looked at the settings for the network, and everything looks right, IP, gateway, DNS, WEP key, everything. However, the card just doesnt connect to my router for some reason (a Netgear WGR614). The details say its sent so many kB out, but has gotten nothing at all in. My router's security is just a 128bit WEP key and MAC filtering. Considering that, I tried re-typing in the WEP key but that didnt help, and I even looked at the MAC and it was naturally the same. Tell me what other info you need and Ill put it up ASAP.
Thanks a lot.

Edit - I forgot to say that its not a hardware issue, this setup works fine in XP.

Also note Im trying to get a fixed IP for the laptop, not DHCP.

---

### Post by odin on 2005-08-12
Could you post your /etc/network/interfaces?

Have yo tried to do it manually first via dhcp?

try:
iwconfig network_interface essid "your essid"
iwconfig (and see if your interface is associated to your accesspoint/router)
dhclient network_interface

if it works like this then at least you have something and i'll try to help with the static IP.

---

### Post by Toddy on 2005-08-12
I found that I had to change my authentication from "shared" to "open" on the router.  Then things worked fine.

---

### Post by Fed on 2005-08-13
Hey,
Firstly thank you for the help. Secondly I now have it working, but to fix it I ran into another problem which I avoided but will run into again in the future, so would love your help on.

When I tried setting things like iwconfig eth1 essid myid, it told me that I wasnt allowed to. Nor could I edit the "interfaces" file, it was read only and that was the end of it. A friend of mine told me I needed to be root to do it, but there is no root account is there? I avoided the problem by reinstalling Ubuntu, and inserted my WEP key as the full thing rather than the passphrase during install, which I think was the problem. Something I looked out for however was whether I had somehow missed the setting up of the root account on install. But I didnt... It didnt ask me for the password or anything, just to create the main computer user and set its password. Can you tell me whether there is such a thing as a root account installed without telling you? In that case, whats the default password thats set to it?

Thank you.

Edit - I read in another thread, previous to reading your reply, about the whole Open System rather than the Shared Key setting. I tried that, but it didnt help the first time while the WEP key was still in passphrase form.

---

### Post by ssck on 2005-08-14
[QUOTE=Fed]Hey,
Firstly thank you for the help. Secondly I now have it working, but to fix it I ran into another problem which I avoided but will run into again in the future, so would love your help on.

When I tried setting things like iwconfig eth1 essid myid, it told me that I wasnt allowed to. Nor could I edit the "interfaces" file, it was read only and that was the end of it. A friend of mine told me I needed to be root to do it, but there is no root account is there? I avoided the problem by reinstalling Ubuntu, and inserted my WEP key as the full thing rather than the passphrase during install, which I think was the problem. Something I looked out for however was whether I had somehow missed the setting up of the root account on install. But I didnt... It didnt ask me for the password or anything, just to create the main computer user and set its password. Can you tell me whether there is such a thing as a root account installed without telling you? In that case, whats the default password thats set to it?

Thank you.

Edit - I read in another thread, previous to reading your reply, about the whole Open System rather than the Shared Key setting. I tried that, but it didnt help the first time while the WEP key was still in passphrase form.[/QUOTE]

root account is not enabled by default.in its place, you can use sudo

you could also use gtkwifi tool for all your wireless needs ....

[http://ubuntuforums.org/showthread.php?t=49148](http://ubuntuforums.org/showthread.php?t=49148)

---

### Post by Fed on 2005-08-14
Thanks, I tried the gtkwifi thing but before I uninstalled I couldnt get it to help me and after I reinstalled I didnt need it anyways.

As for sudo, thats confusing, I read something about the root account being disabled but couldnt believe it. So what would I do to say, edit the interfaces file?

sudo gedit interfaces?

---

### Post by ssck on 2005-08-14
[QUOTE=Fed]Thanks, I tried the gtkwifi thing but before I uninstalled I couldnt get it to help me and after I reinstalled I didnt need it anyways.

As for sudo, thats confusing, I read something about the root account being disabled but couldnt believe it. So what would I do to say, edit the interfaces file?

sudo gedit interfaces?[/QUOTE]

yes

---

### Post by Fed on 2005-08-14
Thanks, good to know. To me personally the idea of having a superuser root account makes more sense, but Im sure Ill get used to the sudo. Sorry for my newbie questions, but we all have to start somewhere.

Wireless is working now and working well so far.
Thank You.

---

### Post by ssck on 2005-08-14
[QUOTE=Fed]Thanks, good to know. To me personally the idea of having a superuser root account makes more sense, but Im sure Ill get used to the sudo. Sorry for my newbie questions, but we all have to start somewhere.

Wireless is working now and working well so far.
Thank You.[/QUOTE]

no problem.glad to be of help ...  :)

---

### Post by numberexhaust on 2005-08-14
[QUOTE=ssck]no problem.glad to be of help ...  :)[/QUOTE]
 That's awesome, Fed... if anyone here could help me out with my problems, I started a thread called Big wireless headache - need asprin.  Thanks a lot guys.

---

