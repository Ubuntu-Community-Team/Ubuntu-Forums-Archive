---
title: "MadWifi"
date: 2008-01-09
forum: Networking &amp; Wireless
---

### Post by jezseaton on 2008-01-09
Hi guys, just trying to get some software working on Ubuntu, It patches madwifi to enable it to perform certain services, and the stage of the madwifi patching isnt working. The software is Karma, attack radioed machines automatically,
Its been suggested that the version of madwifi that comes with ubuntu 7.10 is a different version to that which would be installed should one download and install,
Obviously I am testing this to make progress past the patching process failing, and as such am trying to install the latest stable release of madwifi.
Am following their howto, noting the need to disable the ath_hal in etc/default/linux-restricted-modules-common- but am coming across the following problem... full print out below, problem at end :)

Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/jezseaton/Desktop/madwifi-0.9.3.3 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath/if_ath.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath/if_ath_pci.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath/ath_pci.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_hal/ah_os.o
  HOSTCC  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_hal/uudecode
  UUDECODE /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_hal/i386-elf.hal.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_hal/ath_hal.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_rate/amrr/amrr.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_rate/onoe/onoe.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_rate/sample/sample.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_rate/sample/ath_rate_sample.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/if_media.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_beacon.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_crypto.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_crypto_none.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_input.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_node.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_output.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_power.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_proto.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_scan.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_wireless.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_linux.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_monitor.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_rate.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_acl.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_crypto_ccmp.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_scan_ap.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_scan_sta.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_crypto_tkip.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_crypto_wep.o
  CC [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/ieee80211_xauth.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_wep.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_tkip.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_ccmp.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_acl.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_xauth.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_scan_sta.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_scan_ap.o
  Building modules, stage 2.
  MODPOST 13 modules
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/ath/ath_pci.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath/ath_pci.ko
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_hal/ath_hal.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_hal/ath_hal.ko
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_rate/amrr/ath_rate_amrr.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_rate/amrr/ath_rate_amrr.ko
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_rate/onoe/ath_rate_onoe.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_rate/onoe/ath_rate_onoe.ko
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_rate/sample/ath_rate_sample.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/ath_rate/sample/ath_rate_sample.ko
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan.ko
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_acl.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_acl.ko
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_ccmp.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_ccmp.ko
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_scan_ap.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_scan_ap.ko
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_scan_sta.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_scan_sta.ko
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_tkip.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_tkip.ko
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_wep.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_wep.ko
  CC      /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_xauth.mod.o
  LD [M]  /home/jezseaton/Desktop/madwifi-0.9.3.3/net80211/wlan_xauth.ko
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make -C ./tools  all || exit 1
make[1]: Entering directory `/home/jezseaton/Desktop/madwifi-0.9.3.3/tools'
gcc -o athstats -g -O2 -Wall -I. -I../hal -I.. -I../ath  athstats.c
gcc -o 80211stats -g -O2 -Wall -I. -I../hal -I..  80211stats.c
gcc -o athkey -g -O2 -Wall -I. -I../hal -I..  athkey.c
gcc -o athchans -g -O2 -Wall -I. -I../hal -I..  athchans.c
gcc -o athctrl -g -O2 -Wall -I. -I../hal -I..  athctrl.c
gcc -o athdebug -g -O2 -Wall -I. -I../hal -I..  athdebug.c
gcc -o 80211debug -g -O2 -Wall -I. -I../hal -I..  80211debug.c
gcc -o wlanconfig -g -O2 -Wall -I. -I../hal -I..  wlanconfig.c
make[1]: Leaving directory `/home/jezseaton/Desktop/madwifi-0.9.3.3/tools'
sh scripts/find-madwifi-modules.sh 2.6.22-14-generic 
for i in ./ath ./ath_hal ./ath_rate ./net80211; do \
                make -C $i install || exit 1; \
        done
[COLOR="Red"]make[1]: Entering directory `/home/jezseaton/Desktop/madwifi-0.9.3.3/ath'
test -d //lib/modules/2.6.22-14-generic/net || mkdir -p //lib/modules/2.6.22-14-generic/net
install ath_pci.ko //lib/modules/2.6.22-14-generic/net
install: cannot create regular file `//lib/modules/2.6.22-14-generic/net/ath_pci.ko': Permission denied
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/jezseaton/Desktop/madwifi-0.9.3.3/ath'
make: *** [install-modules] Error 1[/COLOR]

I fully recognise i am a n00b, but have put time and effort into searching for an answer off my own back, 3 hours later, i am turning to you guys, to benefit from your wisdom.

Thanks to all who read this, appreciate your time and skills.

Thankyou

Jez

---

### Post by jezseaton on 2008-01-09
It'll be alright in the morning.

After some sleep I decided to retrace steps and re-ran through [http://madwifi.org/wiki/UserDocs/FirstTimeHowTo](http://madwifi.org/wiki/UserDocs/FirstTimeHowTo)
and experienced no problems, at a guess i'm assuming I hadn't done the 1st step, ./madwifi-unload.bash
as i had assumed the installer would run this as part of its process.
Sigh.
Maybe someone will find this useful anyways.

---

### Post by kevdog on 2008-01-09
Its usually just

make 
sudo make install

Did you compile the svn sources?  You need root privileges to install the compiled binaries!  (You probably already know all this!)

---

### Post by CarrotRevelation on 2008-01-11
I've actually been working on this program on and off for the last 3 months. At first I started out using Pauldotcom.com's pdf instructions where they use the madwifi-old modules and I got the original patch working to where it would compile the module. I believe I was using the madwifi-old 1208 and 14?? revisions. The only thing was that I was doing it on Gutsy and with restricted modules and the new gcc there were some errors. I actually had gotten to the point of hand modifying the source code of the 80211_input.c and 80211_output.c files. Finally I began to wonder why in the heck I was using madwifi-old when it was just going to be deprecated.

I have found some patches for madwifi-ng 3.9 or something, so I started hand modifying them. Most of the differences are the change from IC to VAP. I actually have it now to where it would compile and I can modprobe it in. There are some links out there to modify the program source code too to use wlanconfig instead of iwconfig since madwifi-ng uses wlanconfig ath0 destroy and create. You will also need to ensure that ubuntu doesn't increment your vap interfaces because the program doesn't account for that now. Google: VAP + ath1 + ath2 + ath3. The program only works with ath1. It seems to be hard coded.

I've actually gotten the programs monitor-mode.sh to create the interface and put the modified madwifi-ng into rfmon. And then the program  begins to  run and sets the inteface into master mode. Reading through 80211_input and 80211_output source will help you.

So where am I at now? I'm using 80211_debug and ath_debug with some flags to see output and input. I have also set up a testlab. I have my atheros card on one system, another machine w/ wireshark running, and another machine sending out probe requests to populate it's list. 

The machine that sends out requests sends out some broadcasts first then sends out some specifically from it's saved list. At first it seemed the atheros card would send out the word Karma. Later on I got it to actually send out the requested network. It's still very finicky. I haven't set up the DHCP server yet but... one step at a time. The probing machine can actually join the network w/ a "link-local" I.P. (aka APIPA, aka 169.254.x.x) and I can ping it.

I just wanted to tell you all of this because I want you to know now what you are getting yourself into. It may require hand modifying source code and at least some understanding of ethernet and 802.11 protocols. You've got a journey ahead of you, but this is a good project if you want to force yourself to learn some Linux, networking, 802.11, and simple programming flow. Good luck...If you have problems I can help you but only incrementally. I never asked anybody to spoonfeed me or catch fish for me. I won't give anybody else a crutch. (I'm glad to see somebody else trying their hand at it) This is open source!

BTW- I don't know where you heard about this program, but you are correct in your assumption that you need to be tight-lipped about it. Asking the wrong people for help and having incorrect motives will jeopardize your existence in the community. Make sure you have something to bring to the table.

---

### Post by stone@bruti on 2008-02-05
Hi, just subcribed to try and help with a few links. I too have been trying to get this tool to work (for a security test at work). Unfortunatly I've gone and stuck a backtrack on my machine because I just couldn't be botherd to reinstall everything on my ubuntu. there again it's my first time with a slackware type distrib and I'm having a few probs so I might be back with some more ubuntu based info.

Anyway the main reason I'm posting is to try and give you guys a few links that i found intresting.

A guy that posted his install experiance on ubuntu
[http://jezseaton.blogspot.com/2008/01/idea.html]("http://jezseaton.blogspot.com/2008/01/idea.html")

some guys seem to think that launching airmon-ng puts your card in monitor mode whick makes Karma happy (didn't for me though)
[http://forums.remote-exploit.org/archive/index.php/t-6239.html]("http://forums.remote-exploit.org/archive/index.php/t-6239.html")

another important fact is putting some symbolic links for the iwconfig commands
[http://forums.remote-exploit.org/archive/index.php/t-6813.html]("http://forums.remote-exploit.org/archive/index.php/t-6813.html")

and finaly a link to a guy who made a madwifi patch for Karma
[http://digininja.org/]("http://digininja.org/")

and watch out coz Karma only seems to work on ath0 (you can modify it il the /etc/*.xml files)

if anybody's got some other links or docs, I'd be greatful, I 've still got a few errors but mostly seem to be dependancys and I'll probably spend half the night trying to find them (Ohh how I miss my aptitude install).

good luck :guitar:

Stone

PS here's a link to another prog with the same Idea
[http://www.remote-exploit.org/codes_hotspotter.html]("http://www.remote-exploit.org/codes_hotspotter.html")

---

