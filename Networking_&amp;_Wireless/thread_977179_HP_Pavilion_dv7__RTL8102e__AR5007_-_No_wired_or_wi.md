---
title: "HP Pavilion dv7 / RTL8102e / AR5007 - No wired or wireless network"
date: 2008-11-10
forum: Networking &amp; Wireless
---

### Post by kn1gh7h4wk on 2008-11-10
Hello, I have a new HP Pavilion dv7-1135nr laptop. The wired network adapter is a Realtek RTL8102e and the wireless adapter is a Atheros AR5007. I installed Ubuntu Intrepid Ibex and I immediately noticed that both network adapters are INOP. I then removed Intrepid and installed Hardy Heron and have the same exact problem. I have Hardy Heron on a another HP Pavilion dv9008nr laptop with no problems. I have read several forums with similar problems, none that has fixed my problem. I have downloaded the latest Realtek linux drivers that I could locate (r8101-1.010.00), and still have the same problems.

It seems the default drivers for this adapter for both Hardy and Intrepid was a model r8169. I removed it as part of Realtek's instructions for installing the r8101. But this did not work. Prior to this, the wired adapter appeared in the Network Configuration, but with the new installation, nothing appears. Manually adding the device yielded the same results.

The only way for me to connect to the internet in Linux is by using my Linux WiFi USB adapter (Edimax EW-7318Ug). I would really like to get my wired network up and running. I want to xfer my boxee from my old laptop to this one and seriously need my wired connection for fastest xfers. I am considering ExpressCards, but prefer to use my internal hardware. I do not mind using Hardy or Intrepid. Just want it working. I welcome any suggestions.

Thanks for your help.

---

### Post by K3N8 on 2008-12-01
Hi,

I have exactly the same wireless card. I got the wireless card working: ```
apt-get install linux-backports-modules-intrepid-generic
```

Deactivate the standard Atheros driver and activate the new one in the hardware section.

Gr. Alexander

HP Pavilion DV7 1120

---

### Post by kn1gh7h4wk on 2008-12-25
Awesome!! Thanks a lot. It worked perfectly!

---

### Post by rjmacki on 2009-01-10
I'm also having no network connectivity, on a HP DV7-1135nr. Wired and wireless are both missing. Looking around, it appears that Ubuntu doesn't recognize either one. I'd be delighted to know how apt-get install that backports thing worked for you if there was no network at all, since the system can't go out to download anything.

Anyone? I'm a bit embarrassed since my significant other's dad bought $600 worth of hp based on my assurance that it would "just work." I thought Atheros chips were supported in Ubuntu (Intrepid), and it's an even bigger mystery why the wired interface doesn't appear either. Thanks to anyone who can help.

rjmacki

---

### Post by kn1gh7h4wk on 2009-01-10
My initial Intrepid install had same problem. Strangely, when I wiped it and reinstalled, my wired connection was recognize, but no wireless. The tip K3N8 posted above fixed my wireless problem.

---

### Post by smeck on 2009-01-11
rjmacki, try this: download a .deb from [http://packages.ubuntu.com/sv/intrepid/linux-backports-modules-intrepid-generic](http://packages.ubuntu.com/sv/intrepid/linux-backports-modules-intrepid-generic) and save it to a USB flash memory, take it to the other computer and doubleclick it to install.

If you don't know it ou have amd64 or i386 you most likely have i386

---

### Post by rjmacki on 2009-01-12
Ok, I've done this:

"apt-get install blah-the backports package" (got the wired ethernet working) and it seemed to install just fine,

and now I need to do this:
"Deactivate the standard Atheros driver and activate the new one in the hardware section."

I hate to seem such a newbie, since I've been using Linux for years, but I am new to Ubuntu, and I just don't know where the tools are. What is/where is this "hardware section" or, more specifically, how do I do this "deactivate ... and activate" that seems so obvious to those who know where it is? Sorry for the angst, but I have today and tomorrow to get this working and then the computer and its owner go flying off to the other side of the country. It needs to be working by then.

Thanks for any help anyone can offer.

Ah, never mind; I figured that out. Another chance to feel foolish, I suppose. But I've been absolutely unable to get wireless to work, and wired enet keeps dropping off a cliff, too. I'm going to try another distribution. Thanks anyway ...

---

### Post by TrikeKid on 2009-01-13
System->Administration->Hardware Drivers.

---

### Post by jms1989 on 2009-01-15
I have the exact same laptop but I can't seem to get a connection under Interped (8.10). No link, no data. The wireless is unreconised. I downloaded the package for the wireless and the drivers for the realtek wired device but I am unsure if it'll work. I'm on windows but I just want to run a backup over the lan to my server of this laptop using linux with dd.

Laptop: HP Pavilion dv7-1135nr
Exact hardware as first poster.

Update: Used drivers from RealTek's site and compiled them for the laptop. After installing the modules and running (route add default gw "the IP address of gateway") it was able to connect. The wireless is still not working, perhaps I should go to the Atheros website to download the linux drivers for it too. :)

Update 2: Tried compiling madwifi-0.9.4 for the laptop but I ran into an error.
```

ubuntu@ubuntu:/mnt/src/madwifi-0.9.4$ sudo make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.27-7-generic/build SUBDIRS=/mnt/src/madwifi-0.9.4 modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.27-7-generic'
  CC [M]  /mnt/src/madwifi-0.9.4/ath/if_ath.o
  CC [M]  /mnt/src/madwifi-0.9.4/ath/if_ath_pci.o
  LD [M]  /mnt/src/madwifi-0.9.4/ath/ath_pci.o
  CC [M]  /mnt/src/madwifi-0.9.4/ath_hal/ah_os.o
  HOSTCC  /mnt/src/madwifi-0.9.4/ath_hal/uudecode
  UUDECODE /mnt/src/madwifi-0.9.4/ath_hal/i386-elf.hal.o
  LD [M]  /mnt/src/madwifi-0.9.4/ath_hal/ath_hal.o
  CC [M]  /mnt/src/madwifi-0.9.4/ath_rate/amrr/amrr.o
  LD [M]  /mnt/src/madwifi-0.9.4/ath_rate/amrr/ath_rate_amrr.o
  CC [M]  /mnt/src/madwifi-0.9.4/ath_rate/minstrel/minstrel.o
  LD [M]  /mnt/src/madwifi-0.9.4/ath_rate/minstrel/ath_rate_minstrel.o
  CC [M]  /mnt/src/madwifi-0.9.4/ath_rate/onoe/onoe.o
  LD [M]  /mnt/src/madwifi-0.9.4/ath_rate/onoe/ath_rate_onoe.o
  CC [M]  /mnt/src/madwifi-0.9.4/ath_rate/sample/sample.o
  LD [M]  /mnt/src/madwifi-0.9.4/ath_rate/sample/ath_rate_sample.o
  CC [M]  /mnt/src/madwifi-0.9.4/net80211/if_media.o
  CC [M]  /mnt/src/madwifi-0.9.4/net80211/ieee80211.o
  CC [M]  /mnt/src/madwifi-0.9.4/net80211/ieee80211_beacon.o
  CC [M]  /mnt/src/madwifi-0.9.4/net80211/ieee80211_crypto.o
  CC [M]  /mnt/src/madwifi-0.9.4/net80211/ieee80211_crypto_none.o
  CC [M]  /mnt/src/madwifi-0.9.4/net80211/ieee80211_input.o
  CC [M]  /mnt/src/madwifi-0.9.4/net80211/ieee80211_node.o
  CC [M]  /mnt/src/madwifi-0.9.4/net80211/ieee80211_output.o
  CC [M]  /mnt/src/madwifi-0.9.4/net80211/ieee80211_power.o
/mnt/src/madwifi-0.9.4/net80211/ieee80211_power.c: In function 'ieee80211_pwrsave':
/mnt/src/madwifi-0.9.4/net80211/ieee80211_power.c:240: error: implicit declaration of function '__skb_append'
make[3]: *** [/mnt/src/madwifi-0.9.4/net80211/ieee80211_power.o] Error 1
make[2]: *** [/mnt/src/madwifi-0.9.4/net80211] Error 2
make[1]: *** [_module_/mnt/src/madwifi-0.9.4] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.27-7-generic'
make: *** [modules] Error 2

```

I even tried installing it from the repos but nothing changed, no wireless. Unfortunately, I ran out of time to try some more but at least the wired is working.

---

### Post by josef613 on 2009-05-11
I tried what K3N8 said, and nothing worked. when it is installed, I go to the hardware drivers page, and nothing changes. the old atheros wireless driver still appeared, along with my graphics support.

Help!!

---

### Post by Oglon3r on 2009-06-30
hm i was expecting to accomplish this without asking questions but i keep failing miserably every single time. sorry << another student here
Heres my current situation im running Backtrack 4 a Linux distro built on the latest Kubuntu.
I own a hp dv7-1135nr as many of you already our wireless card on windows and im guessing your ubuntu distro shows as AR5007, on my side it shows as atheros ar242x after much googling ive come to the conclusion that theyre are the same. but it is wrongly detected. (plz feel free to correct me if im wrong)

currently im following smeck's advice 

> rjmacki, try this: download a .deb from [http://packages.ubuntu.com/sv/intrep...trepid-generic]("http://packages.ubuntu.com/sv/intrepid/linux-backports-modules-intrepid-generic") and save it to a USB flash memory, take it to the other computer and doubleclick it to install.

If you don't know it ou have amd64 or i386 you most likely have i386im switching back and forth both partitions trying to make it work and im using usb
i downloaded the deb file extracted and automatically created 2 folders for the 
control.tar.gx and the data.tar.gz
  tomorrow morning i shall try and see if the ethernet port works has anybody with this laptop resolved this problem?
I dont need a straightforward answer im a noob if you can just point me to the right direction i wish to learn thank you in advance have a great day

---

### Post by Oglon3r on 2009-06-30
damn failed once again here's what i got

log
```
root@Backtrack4pf-Oglon3r:~# apt-get install linux-backports-modules-intrepid-generic

Reading package lists... Done

Building dependency tree
Reading state information... Done

Some packages could not be installed. This may mean that you have

requested an impossible situation or if you are using the unstable

distribution that some required packages have not yet been created

or been moved out of Incoming.


Since you only requested a single operation it is extremely likely that

the package is simply not installable and a bug report against

that package should be filed.

The following information may help to resolve the situation:


The following packages have unmet dependencies:
  
linux-backports-modules-intrepid-generic: Depends: linux-backports-modules-2.6.27-11-generic but it is not going to be installed

E: Broken packages
```
any ideas?

---

