---
title: "Network Manager PPTP Disappeared"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by jaie on 2008-10-09
I used to use the network manager PPTP to connect to my VPN. Recently the network manager has decided the only option it will display is Manual Configuration when it is clicked.

I have uninstalled and reinstalled network-manager-pptp and network-manager but the PPTP VPN options do not come back.

Can anybody help me get these options back?

---

### Post by jaie on 2008-10-09
bump

---

### Post by jaie on 2008-10-10
bump again

---

### Post by jaie on 2008-10-10
bumpity bump

---

### Post by nvram867 on 2008-10-11
wonder if anyone else have same thing. mine network manager has also only manual network config, all other options are gone. i would suspect one of the recent updates, i guess you do the update and don't even realize what happened. i did try to remove and reinstall but that didn't fix the issue since it pulls the most recent ver. well there is also possibility that other piece of soft do funky thing.. anyone know how to go around this ?

net manag installed ...
Unpacking network-manager (from .../network-manager_0.6.6-0ubuntu5_i386.deb)

---

### Post by jaie on 2008-10-11
I have had the same thing happen to a computer at work, reinstalling Ubuntu it fixed it. 

There must be a config file setting somewhere that can be reset to get network manager back to a working order.

---

### Post by jaie on 2008-10-13
Surely more people have had this problem...

---

### Post by Gokudan on 2008-10-15
I am not quite sure, but i think this is a thing that happens with network manager 0.7, but i might be wrong...

---

### Post by jaie on 2008-10-16
The offending computer is constantly updated, so whatever the latest version of network manager is (I think is 6.6) is what version it should be on.

---

### Post by OO7TDD on 2008-10-16
Have you tried purging the current install and reinstalling after?

---

### Post by jaie on 2008-10-16
I just tried the following:

sudo apt-get purge network-manager
sudo apt-get purge network-manager-gnome
sudo apt-get purge network-manager-pptp

Then I reinstalled them, logged out and logged in. Its still the same.

---

### Post by torrente on 2008-10-17
I have the same problem, please help

---

### Post by torrente on 2008-10-17
I found it! There is a bug, the roaming mode must be enabled in the network interface config.

---

### Post by jaie on 2008-10-20
This fixed the problem on my work PC. Thanks Torrente, now to try it at home.

---

### Post by Merovius on 2008-10-20
Sounds like a problem i'm having. How do you enable the roaming?

---

### Post by jaie on 2008-10-21
This also fixed my PC at home, Thnx Torrente! Here are the steps:

1) Click on the Icon where the VPN should be and choose Manual Configuration.

2) Press Unlock in the bottom right and enter password.

3) Select Wired Connection.

4) Press Properties.

5) Select the "Enable Roaming Mode" button. (WARNING this will disable any Static IP you may have set).

---

