---
title: "New Working MadwiFi driver for Amilo AR507EG Chipset"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by roadrash on 2008-01-31
At last there is a working solution to the Atheros AR5007EG Wireless chipset.

This chipset has been used in the Acer aspire 3050, Fujitsu amilo Li1715 and some Toshiba Laptops & probably a lot of others as well.

For the Acer & Toshiba laptops, try the instructions here:-
[http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html#more-394](http://www.ubuntugeek.com/atheros-5007eg-with-madwifi-on-i386-platform.html#more-394)

or to install the drivers on the Fujitsu Li1718 
Download the install script at the link below to your home folder: 
[http://homepage.ntlworld.com/roadrash/laptop/fsca16xx.sh](http://homepage.ntlworld.com/roadrash/laptop/fsca16xx.sh)

1.  Now open a shell

2. type: **chmod 755 fsca16xx.sh**

3. type: **sudo ./fsca16xx.sh setup**

Thats it everything is automated and you just have to wait for it to finish.
When it has finished you will need to reboot to activate everything.
In the Mint KDE version click the Knetwork manager then select the network you wish to connect to and enter ant security details.  These will then be stored in KDE wallet.
I'm not to sure what you do in Gnome or XFCE desktops but the drivers will work on both.
This script was primarily written for the Fujitsu Amilo Li1718 Laptop but should work on any other that uses the Atheros AR5007EG WiFI chipset.

This script will work on all versions of Ubuntu & Mint

If this doesn't work then try this guide:-

---

### Post by gammakrikit on 2008-02-19
I used the first option for Toshiba's (I have a Satellite A135-S7404 w/Atheros AR5007EG - UbuntuStudio Gutsy) - this is as far as I got... to the tail end of step five:  
```

E: Some index files failed to download, they have been ignored, or old ones used instead.
me@myputer:~/madwifi-ng-r2756+ar5007$ sudo make install
cd: 1: can't cd to /lib/modules/2.6.22-14-rt/build
Makefile.inc:66: *** /lib/modules/2.6.22-14-rt/build is missing, please set KERNELPATH.  Stop.
```

I left a comment on that article, but it said it had been identified as spam, so the admin would have to deal with it, or something like that :-s

thanks to you & everyone for sharing all the insight - I'm so close to wifi on this thing, I can taste it... :biggrin:

p.s. - how would I set the kernel path anyways?

---

### Post by McTree on 2008-03-05
Hi,

make sure You have the Linux headers for the RT kernel installed. Go to Synaptic and search for Linux Headers, select both versions  that say RT (real time), and install....

The KERNELPATH is OK after this. 
Good luck
McT

---

