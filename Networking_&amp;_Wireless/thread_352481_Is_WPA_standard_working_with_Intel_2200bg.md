---
title: "Is WPA standard working with Intel 2200bg ?"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by charlieMOGUL on 2007-02-03
Hi,

First off, I searched the forums and read *a lot* about the various issues regarding the Intel 2200bg wireless network card, Ubuntu 6.10 and WPA. After unsuccesful trying to get my Toshiba laptop with an Intel 2200bg wireles network card to work using WPA (unencrypted works perfectly) I have some questions regarding the details.
Secondly, I'm new to Ubuntu (hi everybody!), so please bear with me..

I installed Ubuntu 6.10 on a Toshiba laptop with an Intel 2200bg wireles network card.
* Is WPA enabled/installed standard (= 'out-of-the-box'), or do you have to install/upgrade a package (wpa_supplicant ? network manager ? ) to support this option ?

* Does the (standard) Network Manager supports WPA settings, or do you have to edit the network configuration file (/etc/network/interfaces  ?) manually ?

* Does the standard ipw2200 drivers support WPA ?

Thanks in advance for your time,

charlieMOGUL

---

### Post by bernied on 2007-02-03
I installed Dapper Kubuntu on a Dell D610 with that interface and it worked using knetworkmanager, including WPA. I don't remember needing to manually edit any configuration files - I was very impressed. 

So yes, network manager supports WPA without any manual editing.
And yes the standard ipw2200 drivers support WPA.

I would expect it to work well with network manager. knetworkmanager was very easy to use, but perhaps neither are installed by default. I suggest you install the package called network-manager-gnome (that is if you use gnome, else network-manager-kde if you use kde).

---

