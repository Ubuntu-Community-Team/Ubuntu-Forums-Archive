---
title: "Asus WL-103 PCMCIA Card using Prism2_cs driver"
date: 2005-05-09
forum: Networking &amp; Wireless
---

### Post by Rutnut on 2005-05-09
Hello all.

I have been going mad at trying to get my PCMCIA card working.

I downloaded the drivers and installed into the folders that were in the instructions and this is what I got.

/usr/src/linux-wlan-ng-0.2.0 #make config

Then I am asked questions which requires yes or no.
For Yes I choose PCMCIA Card Services

For the rest I choose No.

Linux source directory [/usr/src/linux]:make install

Then I get the message below


find . -name .depend -exec rm {} \;
set -e; for d in src doc man etc; do make -C $d install ; done
make[1]: Entering directory `/usr/src/linux-wlan-ng-0.2.0/src'
set -e; for d in p80211 prism2 shared wlanctl wland nwepgen mkmeta wlancfg; do make -C $d install ; done
make[2]: Entering directory `/usr/src/linux-wlan-ng-0.2.0/src/p80211'
cc -c   -I../include   -DEXPORT_SYMTAB p80211mod.c -o p80211mod.o
make[2]: cc: Command not found
make[2]: *** [p80211mod.o] Error 127
make[2]: Leaving directory `/usr/src/linux-wlan-ng-0.2.0/src/p80211'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/usr/src/linux-wlan-ng-0.2.0/src'
make: *** [install] Error 2

I know it's probably me,  but can I be doing wrong? I did have an error message about missing linux headers so I looked on the Synaptics and installed them, now I get the message at the top.

I am using an Asus L4 laptop. 2.4 Celeron, 256 MB RAM and a 30Gig HD with Win 2000. It is being used as a duel boot machine - for now.

Hope you can help.

Regards

---

