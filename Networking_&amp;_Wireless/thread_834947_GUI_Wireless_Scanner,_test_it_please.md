---
title: "GUI Wireless Scanner, test it please"
date: 2008-06-20
forum: Networking &amp; Wireless
---

### Post by kuthulu on 2008-06-20
Hi, i wrote a little app using python and glade to create a simple wireless scanner like netstumbler, you can download the .deb package from here:

[http://kuthulu.com/iwscanner/index.php?module=download](http://kuthulu.com/iwscanner/index.php?module=download)

Home of iwscanner
[http://www.kuthulu.com/iwscanner](http://www.kuthulu.com/iwscanner)

if you have time please give it a try and post here your results

thanks

---

### Post by dmizer on 2008-06-20
please post the source as well, thank you.

---

### Post by mavi_yelkenler on 2008-06-20
hey kuthulu,

i tried the app and it is working. i ve been searching such an netstumbler like app in linux. thanks a lot.i hope the gui will be nicer..

regards

---

### Post by kuthulu on 2008-06-20
> **dmizer said:**
> please post the source as well, thank you.

it's written in python, the sources are included in the package, when installed you can view them in /usr/share/iwscanner/iwscanner.py

---

### Post by kuthulu on 2008-06-20
> **mavi_yelkenler said:**
> hey kuthulu,

i tried the app and it is working. i ve been searching such an netstumbler like app in linux. thanks a lot.i hope the gui will be nicer..

regards

thanks for testing... 
what would you change in the gui???

suggestions are welcome

---

### Post by mavi_yelkenler on 2008-06-20
> **kuthulu said:**
> thanks for testing... 
what would you change in the gui???

suggestions are welcome

in fact it is not bad,
by the way, look at the channel part in the picture, it shows all zero?

anyway i am happy with the app

---

### Post by kuthulu on 2008-06-20
> **mavi_yelkenler said:**
> in fact it is not bad,
by the way, look at the channel part in the picture, it shows all zero?

anyway i am happy with the app

post the output of the "iwlist ath0 scan" command to see where the problem is.

---

### Post by mavi_yelkenler on 2008-06-20
iwlist ath0 scan

> ath0      Scan completed :
          Cell 01 - Address: 00:1A:2A:02:CA:44
                    ESSID:"........"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 02 - Address: 00:1A:2A:60:19:B3
                    ESSID:"......"
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=5/70  Signal level=-90 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
          Cell 03 - Address: 00:1D:19:11:24:CE
                    ESSID:"........."
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality=4/70  Signal level=-91 dBm  Noise level=-95 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                              6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Extra:bcn_int=200
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

---

### Post by Vadi on 2008-06-20
I loved netstumbler on windows.

Some tips: upgrade to debian package maker 0.4, and for architecture change to "all" - because I can't install on 64bit ubuntu when it's set to i386.

---

### Post by Vadi on 2008-06-20
You can get 0.4 from here: [http://code.google.com/p/debianpackagemaker/downloads/list](http://code.google.com/p/debianpackagemaker/downloads/list)

I'll comment on the gui and tweak it with glade if needed after you fix the package :)

---

### Post by kuthulu on 2008-06-20
dpm 0.4 crashes in my box (ubuntu 7.10)
i updated the link in the first post to the new package v0.1.1 with architecture set to "all" and fixed the "channel" issue.

---

### Post by mavi_yelkenler on 2008-06-21
thanks kuthulu, now it shows the channels

---

### Post by Vadi on 2008-06-21
I think categories in .desktop should be "Categories=System;Application;", so that it ends up in System Tools and not in Accessories.

Another thing, the label besides "speed" should change as you drag the bar, not after you release the button. Could you also add a tooltip saying "Scanning speed", so it's more clear what the speed does?

---

### Post by kuthulu on 2008-07-04
i added a .tgz file so you can run it in other linux environment.
[http://www.kuthulu.com/iwscanner](http://www.kuthulu.com/iwscanner)

---

### Post by Vadi on 2008-07-04
You should have it be packaged into ubuntu :)

Edit: btw, your server reports the mime type wrong for the .deb, which confuses firefox and makes it want to save the .deb when I told it to install all .debs :(

---

### Post by kuthulu on 2008-07-04
i fixed the mime type, i set it to "application/x-deb"

---

### Post by Vadi on 2008-07-04
Sorry but it should be "application/x-debian-package", thanks :)

---

### Post by kuthulu on 2008-07-09
yes, you're right
i updated it, thanks

---

### Post by kuthulu on 2008-09-06
new version
i added support for opening and saving NetStumbler (.ns1) and NetDetect (.ndd) file format.

get it here:
[http://kuthulu.com/iwscanner/iwscanner-0.2.0.deb](http://kuthulu.com/iwscanner/iwscanner-0.2.0.deb)

---

### Post by Vadi on 2008-09-06
Looks good. Have you filed a report on launchpad to have it added to ubuntu repositories?

---

### Post by kuthulu on 2008-09-07
not yet... but it's good idea
i'll wait to see how it works and if it's ok then i'll try to get it added to the repos.

---

### Post by Vadi on 2008-09-07
It's working great when I test it :)

---

### Post by mocha on 2008-11-03
Wow!  This is so nice!  I was just thinking about netstumbler the other day while planning to experiment with some new antenna designs.  I was thinking, gee, running iwlist all the time is going to be a pain, it would be nice to have a netstumbler for linux!  Your prog addresses this need.  Thanks!  ):P

---

### Post by Spenzer4Hire on 2008-11-06
Nice work.  I was looking for something quick and simple.  Thanks!

---

### Post by jim87410 on 2009-06-07
I just installed it on my Acer Aspire One running 9.04 Remix and it looks like it is working fine.  This is just what I was looking for.  Thank you.

Jim
[http://bloggajim.com]("http://bloggajim.com")

---

### Post by Zill on 2009-06-24
iwScanner v0.2.3 runs fine on my ancient 450MHz PC running Xubuntu Hardy.  A very useful utility.  Many thanks.

---

### Post by Phreaker on 2009-06-24
Runs perfectly on Ubuntu 9.04 32-bit
My wireless card is Linksys WUSB54GR (rt73 chipset) 

OUT OF THE BOX

---

### Post by andersja on 2009-12-09
> **Vadi said:**
> Looks good. Have you filed a report on launchpad to have it added to ubuntu repositories?

I took the liberty to file the below bug in Launchpad for inclusion of iwscanner in the Ubuntu repositories:

[https://bugs.launchpad.net/ubuntu/+bug/494580](https://bugs.launchpad.net/ubuntu/+bug/494580)

---

