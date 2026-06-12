---
title: "losing wep password on shutdown"
date: 2008-10-24
forum: Networking &amp; Wireless
---

### Post by patanjali on 2008-10-24
I am running ubuntu gutsy fully updated on a Toshiba A30 Satellite.  I have one problem (minor but annoying).  Whenever I shut down my laptop I lose my WEP password for my wireless router and have to re-input it on startup.

The router is a Siemens Gigaset SE587.

Has anyone else had this problem, and does anyone know of a fix?

Thanks in advance

patanjali:rolleyes:

---

### Post by sisimonsen on 2008-10-24
I have the same problem on my Fujitsu Siemens Lifebook S6120. My network is set up with WPA personal encryption, and at every start-up i have to insert the WPA key manually.  Sometimes I have to do this several times before the key eventually is accepted and the LapTop connected to the router.

Router: 3com Office Connect 11g (some years old but still...)

Haven't found a way to fix this.  Help and hints are very welcome !

Currently I run the beta 8.10 version.  Same problem on 8.04.

---

### Post by iwc5893 on 2008-10-24
I had the same problem until I installed WICD and use it as my wifi card manager.

---

### Post by azakarea on 2008-10-25
sorry but what is the WICD i have search it on the add / remove programs it is not there 

thanks

---

### Post by sethvath on 2008-10-25
[http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Its a wifi-tool to replace network manager - the default wifibar on the gnome panel in ubuntu. Benefits it has over network-manager is that it stores your wep/wpa passphrase so you do not need to re-enter every boot up.

Installation instructions here:

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

---

### Post by patanjali on 2008-10-25
Thanks sethvath.  Downloading wicd solved it.

patanjali :-)

---

