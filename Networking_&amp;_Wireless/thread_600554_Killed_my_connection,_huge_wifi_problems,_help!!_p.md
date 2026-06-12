---
title: "Killed my connection, huge wifi problems, help!! please!!"
date: 2007-11-02
forum: Networking &amp; Wireless
---

### Post by jonah1980 on 2007-11-02
hi i've made a huge mess.

ok so my rt61 wireless card was working, but not great. sometimes the connection would drop and i'd have no internet.

i've had trouble with my card before on other distros that ship rt61 drivers, in the past i simple removed the rt61/rt2x00 driver shipped with the distro and installed the rt61cvs legacy driver from Serialmonkey.

this previously worked on fedora and elive etc.

ok so now i'm on gutsy my internet wasn't working good so i thought, it'l be the same issue, i need that legacy driver installing from serialmonkey. great, only it wasn't great at all. i couldn't find any rt drivers to remove in synaptic so i just did a make and make install of this driver from serialmonkey.

i rebooted and now i have no internet connection at all. the little swirly thing near clock just goes round and round and the green lights don't come on, if i click manual configuration nothing happens and network manager won't load up. i can't load up a terminal either, i click accessories/terminal and nothing happens, other apps will load up though...

and i can't even drop to alt-ctrl-f1 - this seems to be another issue with resolution or something as i just get a flashing cursor in top corner of screen - this was like this before the wifi driver install. cos it's the wrong resolution out of gdm it doesn't show you the usual login or terminal prompt....

i'm really in a big mess so anyone that can please help me out, thanks...

---

### Post by Dr. Nick on 2007-11-02
Boot into rescue mode from grub. Then I would try and remove all the new drivers installed from that command line. I dont have your card, but i wouldnt be surprised if the drivers were now integrated in the kernel, hence no packages to remove. 

Are you familiar with modprobe, and lsmod? I would lsmod and see which drivers are loaded for the card and possible blocklist the one that doesnt work

---

### Post by jonah1980 on 2007-11-02
ok after much stress in irc, and no ubuntu users being able to help i tried in the debian irc and didn't tell them i was on ubuntu. someone in there explained how to rm the .ko file out of lib/modules/ and now my system is back up and running ok


although i would really like to install this driver so internet doesnt keep dropping, how should i go about this without killing it again? is it conflicting with some other wifi driver that ubuntu uses...???

this is the driver i would prefer to use: [http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz](http://rt2x00.serialmonkey.com/rt61-cvs-daily.tar.gz)

---

### Post by Dr. Nick on 2007-11-02
If you back in a gui and have a terminal then open it up and run 

**lsmod**

Look for the network card and see what driver it is using.

Find the name of the kernel module and then load up this file in a text editor as root

/etc/modprobe.d/blacklist

add the alias to the built in module then save it and restart. On reboot check lsmod again and make sure it didnt load, you also shouldnt have any wireless internet. Then I would install the driver you want to use and just follow its instructions.

I dont have that card so I cant be more specific, but I had to do similar with my old wireless card.

---

### Post by jonah1980 on 2007-11-02
hey thanks yeah i'm back with the built in module, but already after 5mins my internet went off for a bit with the shipped driver. but my other machine internet is fine, so it's defo this driver from ubuntu.

anyway i did the lsmod as you said and got a few entries to do with wifi:

rt61pci                28288  0 
rt2x00pci              13184  1 rt61pci 
rt2x00lib              21760  2 rt61pci,rt2x00pci

it's really annoying that they build things in the kernel like this that can cause issues, cos now i don't know how to install the working driver without making another mess, and i don't know whether to blacklist any of the above or not!

---

### Post by Dr. Nick on 2007-11-02
> **jonah1980 said:**
> hey thanks yeah i'm back with the built in module, but already after 5mins my internet went off for a bit with the shipped driver. but my other machine internet is fine, so it's defo this driver from ubuntu.

anyway i did the lsmod as you said and got a few entries to do with wifi:

rt61pci                28288  0 
rt2x00pci              13184  1 rt61pci 
rt2x00lib              21760  2 rt61pci,rt2x00pci

it's really annoying that they build things in the kernel like this that can cause issues, cos now i don't know how to install the working driver without making another mess, and i don't know whether to blacklist any of the above or not!

Is the driver you want still installed at all? It looks like its loading 2 modules up
Not being familiar with that card i cant say, but if it were me i would blacklist 
rt61pci and rt2x00pci and see how it goes. You can also just delete those 2 files, or better yet just move them out of the modules directory just to be safe.

Just search for those modules files and move then to a different directory and it will keep them from loading, without having to mess with blacklist. The drawback to that approach is you will have to do it after every kernel upgrade cause they will be recreated.

Good luck, ill be gone for several hours so i wont be able to reply

---

### Post by jonah1980 on 2007-11-02
ah well it's maybe still trying to load up that other driver i installed, see the guy in debian irc told me how to rm delete the module but he didn't tell me how to clean up the system so it didn't try loading the driver again. so it's not there but maybe my ubuntu looks for it? maybe you can help me clean it up also before i try again? i've also submitted a bug report if you can be any help there also...

[https://bugs.launchpad.net/ubuntu/+bug/159566](https://bugs.launchpad.net/ubuntu/+bug/159566)

would be great if ubuntu could fix this so didn't have to blacklist and mess with things too much, i don't want to break anything...

---

### Post by Dr. Nick on 2007-11-03
Ill try to help. If you removed all the modules in the kernel folder with rm then it shouldnt try to load it I believe. 

I would open your blacklist and remove everything for now just so we dont accidentally blacklist the driver you want to install.

I would try this link too
[http://ubuntuforums.org/showthread.php?t=400236&highlight=rt61](http://ubuntuforums.org/showthread.php?t=400236&highlight=rt61)

seems to be a good howto for your rt61 chipset

---

### Post by jonah1980 on 2007-11-04
ok i blacklisted those 3 modules and then installed the legacy rt61 module. it did give me the size warning, saying it was a big driver, but i just ignored it as my internet was off and i didnt have a reference for that strip command.

anyway i had to set up my network config manually as the swirly light thing didn't pick up a signal and wouldn't connect. on manual config it all appears to be working great, and the signal is stronger than it was on on old driver percentage wise. also it's much better as internet is on from the off and i don't have to put gnome keyring password in on boot up.

hopefully that's it all sorted. although it feels a bit messy with the driver size warning, the connection manager not working without manual config and stuff blacklisted, but hey at least it works. thanks for all your help.

---

### Post by Dr. Nick on 2007-11-04
> **jonah1980 said:**
> ok i blacklisted those 3 modules and then installed the legacy rt61 module. it did give me the size warning, saying it was a big driver, but i just ignored it as my internet was off and i didnt have a reference for that strip command.

anyway i had to set up my network config manually as the swirly light thing didn't pick up a signal and wouldn't connect. on manual config it all appears to be working great, and the signal is stronger than it was on on old driver percentage wise. also it's much better as internet is on from the off and i don't have to put gnome keyring password in on boot up.

hopefully that's it all sorted. although it feels a bit messy with the driver size warning, the connection manager not working without manual config and stuff blacklisted, but hey at least it works. thanks for all your help.

Glad its sorta sorted out, my network manager is funky at times, It will stay swirly trying to connect to my neighbors wifi at 5% signal and ignore my wifi at 85% lol

---

### Post by Ferrat on 2007-11-04
> **jonah1980 said:**
> ok i blacklisted those 3 modules and then installed the legacy rt61 module. it did give me the size warning, saying it was a big driver, but i just ignored it as my internet was off and i didnt have a reference for that strip command.

anyway i had to set up my network config manually as the swirly light thing didn't pick up a signal and wouldn't connect. on manual config it all appears to be working great, and the signal is stronger than it was on on old driver percentage wise. also it's much better as internet is on from the off and i don't have to put gnome keyring password in on boot up.

hopefully that's it all sorted. although it feels a bit messy with the driver size warning, the connection manager not working without manual config and stuff blacklisted, but hey at least it works. thanks for all your help.

You need to slim the driver 
just open the readme that comes with the serialmonkey driver, there you get a easy step by step on how to get it working. 

My wifi connection (with rt61 driver) was working but very unstable with gutsy drivers, but removed network manager and installed the serialmonkey driver instead and now I've been online 3days without one drop.

---

