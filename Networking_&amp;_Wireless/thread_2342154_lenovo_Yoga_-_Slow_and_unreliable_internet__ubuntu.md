---
title: "lenovo Yoga - Slow and unreliable internet  ubuntu 16.04"
date: 2016-11-04
forum: Networking &amp; Wireless
---

### Post by danieledei on 2016-11-04
Help please !

I was almost sending my Lenovo laptop for repairing while I've seen a lot of threads for similar cases, so here I am.
For using the touch-screen I had to upgrade mu Ubuntu to the 16.04 and since then the wireless is totally unreliable.

The internal Dual-BandWirelessAC3160 is hopeless and an external Netgear WPN111  works better.
Initially I start finding the wireless auto setting itself on HotSpot and therefore disabling all wifi : I had to manually swith
Then according to the corrections and update of the Ubuntu 16.04 I have experienced all sort of behaviours .

Now the wireless keeps stopping&starting on its-own  opening endless wireless line on the manager ( see the png )
The telephone line provider is the Italian TIM and the ADSL comes through a router Tp-LINK AC 750 mod ArcherD2  


I'm going to send a test wired  then a test with :  wired (KO no file but png ) only the internal services, internal and external and finally the test with the external netgear only.
Please find attached  the png file and txt file  on *.tar.gz
Hope those will be enough for you to give me an idea on what to do.

Thank you for your help

[ATTACH]271957[/ATTACH][ATTACH]271958[/ATTACH][ATTACH]271959[/ATTACH][ATTACH=CONFIG]271960[/ATTACH][ATTACH=CONFIG]271961[/ATTACH].
Ciao from Tuscany
Danny De

---

### Post by Hadaka on 2016-11-04
Hi, you are running all three connection types most of the time.
wired...wireless internal...wireless external usb, this is causing a conflict
and errors. Let's start by removing the wireless usb and disconnecting the
wired connection and see if we can get the internal wireless working correctly.

After disconnecting the wired connection and removing the wireless usb
please open a terminal ..ctrl/alt/t... and do.
```
gksudo gedit /etc/network/if-up.d/off-power-manager
```
this will bring up the gedit editor..
Paste these commands in the editor.
```
#!/bin/sh
/sbin/iwconfig wlan0 power off
```
Save and close gedit editor.
back to terminal...ctrl/alt/t..then do..
```
sudo chmod +x /etc/network/if-up.d/off-power-manager
```
Boot the computer
*Do not reconnect the wired or insert the usb
open a terminal ...ctrl/alt/t... after you boot and enter..
```
iwconfig
```
one line should read..."Power Management-off"
please let us know if it does not.
if yes..it does = off ...then test by accessing the internet
and see if it is more stable...
please update us with your status.
thanks.

---

### Post by danieledei on 2016-11-05
Thank you so much for your quick reply and clear directions.

Initially it did not work but I've realised that I did not run the shell/command.
I did run it and it went OFF.

I'll see it it gets working
Right now the situation is attached

Thank you again
Have a nice week-end
Ciao from Italy

Danny
at [www.lamassa.tuscany.it](www.lamassa.tuscany.it) 

[ATTACH]271979[/ATTACH]

---

### Post by Hadaka on 2016-11-05
Hi, we are making progress , you are currently attaching to
or attempting to attach to , 2 differnt access points per your dmesg printout on the latest
wireless diagnostic.  you have your 5Ghz and your 2.4Ghz with the ssid
of "lamassa21" so it cycles between the two when looking for a connection.
Please access the configuration in your router for your 5Ghz settings and
change it something like lamassa21_5G. Don't forget to also click 'edit connections'
from your wifi signal icon and change to lamassa21_5G also.
then once that is complete, bring up a terminal ..crtrl/alt/t...and then copy and paste.
```
echo "options iwlwifi 11n_disable=8" | sudo tee -a /etc/modprobe.d/iwlwifi.conf
```
boot
and then Copy, paste and post the output of...
```
grep [[:alnum:]] /sys/module/iwlwifi/parameters/*
iwconfig | awk '/Power /{print$1,$2}'
```

again..do not attach the wired or insert the usb
thanks.

---

