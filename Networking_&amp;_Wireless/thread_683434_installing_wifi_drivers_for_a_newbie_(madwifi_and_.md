---
title: "installing wifi drivers for a newbie (madwifi and ndiswrapper a no go?)"
date: 2008-01-31
forum: Networking &amp; Wireless
---

### Post by shimojimatto on 2008-01-31
I have an IBM Thinkpad x40 that all sources seemed to report works great with previous versions of Ubuntu ([http://www.leopold.dk/~martin/IBMx40UbuntuInstall.html]("http://www.leopold.dk/~martin/IBMx40UbuntuInstall.html") and [http://www.noapparentmotive.org/topics/ubuntuX40.html]("http://www.noapparentmotive.org/topics/ubuntuX40.html"))

unfortunately things didn't go so smoothly with 7.10. 

One of the things not working on install was the wireless card. 

I'm fairly new to linux in general, but I tried to read up and solve this problem myself before resorting to bothering people on these forums.

First of all. When Ubuntu first booted up, I noticed that the "wifi is turned on" light on my display was not on. Not sure if this is controlled through the OS or directly tied to the powered on/off status of the wifi card. Pressing Fn+f5 (the shortcut for turing on and off wifi and bluetooth) does nothing. All other built in function key shortcuts work fine...(as above referenced sites commented).

When I checked System>Administration>Network Tools I would get "Unknown Interface (wifi0)" and "Unknown Interface (ath0)" under the Devices tab (note: wired ethernet seems to be ok... although I haven't had a chance to hook it up and I can't use the same connection I'm using now to test it)

I saw those "Unknown Interface" messages and figured that maybe drivers were not installed for my card (I've heard theres lots of problems with wifi in linux in general... figured a 4 year old mini-PCI card in a uber-popular well linux supported laptop would be supported fine under Ubunto tho...)
So I gave "madwifi" a try. Downloaded it, followed directions in the "install" file... didn't work... got some errors. Tried the instructions on the [madwifi.org]("http://madwifi.org/wiki/UserDocs/FirstTimeHowTo") page... same...

took the interfaces down with:
 ifconfig ath0 down
ifconfig wifi0 down

removed old modules as per directions...

then got some errors on the make command:

~/Desktop/madwifi$ sudo make
[sudo] password for shimojimatto:
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/shimojimatto/Desktop/madwifi modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  CC [M]  /home/shimojimatto/Desktop/madwifi/ath/if_ath_pci.o
cc1: warnings being treated as errors
/home/shimojimatto/Desktop/madwifi/ath/if_ath_pci.c: In function 'ath_pci_probe':
/home/shimojimatto/Desktop/madwifi/ath/if_ath_pci.c:210: warning: 'deprecated_irq_flag' is deprecated (declared at include/linux/interrupt.h:66)
make[3]: *** [/home/shimojimatto/Desktop/madwifi/ath/if_ath_pci.o] [COLOR="Red"]Error 1[/COLOR]
make[2]: *** [/home/shimojimatto/Desktop/madwifi/ath] [COLOR="Red"]Error 2[/COLOR]
make[1]: *** [_module_/home/shimojimatto/Desktop/madwifi] [COLOR="Red"]Error 2[/COLOR]
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
make: *** [modules] [COLOR="Red"]Error 2[/COLOR]
shimojimatto@shimojimatto-laptop:~/Desktop/madwifi$ 

and of course more errors on the following make install command...

so that didn't work... both interfaces dissappeared under the "Devices - Network Tools" dialogue box.

so i tried ndiswrapper (installed from the synaptic package manager ... speaking of which... why is this and the build-essential not installed by default? how are new users supposed to know this stuff?)

but it only seemed to get the ath0 interface back under the "Devices - Network Tools" box... where did wifi0 go? and still nothing works... 

any clues how to get wifi0 back... and make it work? is there a step I'm missing? I know this post is a total mess... sorry...

EDIT:
using an Atheros chip based card 5211 chipset... so I know that I can use madwifi or ndswrapper... what driver and what software to use is not the problem... how to install drivers... how to turn on and off devices... and how to know they are working properly are the problems.

---

### Post by Whiffle on 2008-01-31
I'd get rid of ndiswrapper and the madwifi files you downloaded and try:

```

sudo apt-get install linux-restricted-modules-`uname -r`

```

It should include the madwifi drivers, which are really a much better solution than ndiswrapper.

---

### Post by shimojimatto on 2008-01-31
I'll try that when I can get to a wired internet connection.... but how do I get the other interface back online? And is there something I should do to clear out the ndiswrapper and the other madwifi drivers that I futzed with?

---

