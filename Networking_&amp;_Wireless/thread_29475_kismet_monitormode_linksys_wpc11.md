---
title: "kismet monitormode linksys wpc11"
date: 2005-04-24
forum: Networking &amp; Wireless
---

### Post by nothreat33 on 2005-04-24
i've been trying to get kismet to work for 2years. this is how far i've gotten.
im using a linksys WPC11 card which worked right out of the box with ubuntu 5.04 and before.

i've installed the linux-wlan-ng-0.1.9.7 driver i thought i needed. and i edited kismet.conf so that my card type and drivers look like this:

source=hostap,eth1,prism2source

and i run kismet and i get this:

FATAL: Failed to set monitor mode: Invalid argument. This usually means your drivers either do not support monitor mode, or use a different mechanism for getting to it. Make sure you have a version of your dirvers that support monitor mode, and consult the troubleshooting section of the README.

i have no idea how to get my card into monitor mode, though i've tryed iwconfig eth1mode monitor and that did not work. i dont know if i need a driver or if something is wrong with my kismet.conf or what. 

just now, after getting that "FATAL" stuff, i looked at my network configuration and i noticed eth1 (my wireless interface) was active. so i deactivated it hoping this would fix the problem HOWEVER. when i tryed to run kismet again i got FATAL: channel get ioctl failed 16:Device or resource busy. How is it busy when i just turned it off? and how did  i NOT get that error when it was active?

this is ridiculous i need some help.

---

### Post by jshein on 2005-04-24
Try this ( substituting wlan0 for the apropriate interface )

source=hostap,wlan0,newprism2source 

You MUST deactivate your card before starting kismet or it WILL crash.

example:    #sudo ifdown eth1

You also might get farther by installing the latest kismet if you have not already


# wget [http://mirror.aarnet.edu.au/debian/pool/main/k/kismet/kismet_2005.01.R1-2_i386.deb](http://mirror.aarnet.edu.au/debian/pool/main/k/kismet/kismet_2005.01.R1-2_i386.deb)
# apt-get install ethereal-common
# dpkg -i kismet_2005.01.R1-2_i386.deb

---

### Post by nothreat33 on 2005-04-25
eth1 is the correct interface and when everything is turned off i still get the error that says it cannot get the card into monitor mode. is there a specific driver i neeD? or somethign i need to do to the kernel?

---

### Post by jshein on 2005-04-25
See my post here

[http://ubuntuforums.org/showthread.php?t=23596&highlight=kismet+orinoco](http://ubuntuforums.org/showthread.php?t=23596&highlight=kismet+orinoco)

---

### Post by Jet2k5 on 2005-04-25
I have the exact same wireless card, but ever after the update my internet on Linux has been extremely slow.

When I boot up windows my speed is great.  Takes almost 1 second to get irc.feenode.net running and connecting to aim.

On Linux these both take ages, like it's having trouble finding out if it is/not connected to the internet.  Browsing webpages is like following a turtle, very very slow.  Anyhow I noticed that this is not pertain to the topic.

But my card didn't need any drivers, I set it up from the beginnning and it worked great.  Just the thing that is pissing me off the most is that the internet is taking so long to like get up and running.  Web pages are slow, connecting to gaim or freenode are painfully slow.  But for some reason I still get my full speed when downloading stuff.

Hopefully someone will reply to my post since I see that no one has yet  :-?

---

### Post by nothreat33 on 2005-04-25
why did you post that here? it has nothign to do with my subject....
anyway, do i need that orinico patch if my card is a linksys with a prism2 chipset? or does it not matteR?
if thats all i need thats great. i downloaded the patch, when i run the commands in your HOWTO, actualy when im patching the kernel it asks for the file to patch. i don't know where this is. does it depend on the card? or is there a universal file path that needs to be patched. where is it?

---

### Post by jshein on 2005-04-25
My apologies. Not enough sleep, thought I was answering a different post. :)

insert your card and type

#iwpriv eth1

see if monitor mode is listed. If it is then your driver is monitor mode capable.

If not....  Let me know

---

### Post by ranf on 2005-04-25
[QUOTE=nothreat33]
i've installed the linux-wlan-ng-0.1.9.7 driver i thought i needed. and i edited kismet.conf so that my card type and drivers look like this:

source=hostap,eth1,prism2source
[/QUOTE]

So you have linux-wlan-ng drivers? Why is there "hostap" in kismet.conf line?

Shouldn't that be something like this:

source=wlanng_avs,wlan0,newprism2source

---

### Post by nothreat33 on 2005-04-26
it does not this is what i got: (to be precise)

mike@osiris:~$ iwpriv eth1
eth1      Available private ioctl :
          force_reset      (8BE0) : set   0       & get   0
          card_reset       (8BE1) : set   0       & get   0
          set_port3        (8BE2) : set   1 int   & get   0
          get_port3        (8BE3) : set   0       & get   1 int
          set_preamble     (8BE4) : set   1 int   & get   0
          get_preamble     (8BE5) : set   0       & get   1 int
          set_ibssport     (8BE6) : set   1 int   & get   0
          get_ibssport     (8BE7) : set   0       & get   1 int
          dump_recs        (8BFF) : set   0       & get   0

mike@osiris:~$

---

### Post by nothreat33 on 2005-04-30
i changed my kismet.conf to wlanng_avs instead of hostap. and installed 0.2.0  of the driver. after saving the conf file i ran kismet and got this:

root@osiris:/etc/kismet/linux-wlan-ng-0.2.0 # kismet
Server options:  none
Client options:  none
Starting server...
Waiting for server to start before startuing UI...
Suid priv-dropping disabled.  This may not be secure.
No specific sources given to be enabled, all will be enabled.
Enabling channel hopping.
Enabling channel splitting.
Source 0 (prism2source): Enabling monitor mode for wlanng_avs source interface eth1 channel 6...
FATAL: command 'wlanctl-ng eth1 lnxreq_ifstate ifstate=enable >/dev/null 2>/dev/null' failed.

---

### Post by jshein on 2005-04-30
What do you get back if you type

***#iwpriv eth1 monitor***

( If this errors out then monitor mode is not compiled into your drivers )

---

### Post by nothreat33 on 2005-05-01
# iwpriv eth1 monitor
Invalid command : monitor

i didnt' fully install the drivers. i need to run make all and make install. such a silly mistake.
i ran make config to reconfigure the drivers then 'make all' but i get errors and it aborts.

here it is when it started going wrong:

 80211wext.c p80211wep.c p80211netdev.c p80211mod.c > .depend
In file included from /usr/src/linux-2.6.10/include/linux/irq.h:21,
                 from /usr/src/linux-2.6.10/include/asm/hardirq.h:6,
                 from /usr/src/linux-2.6.10/include/linux/hardirq.h:6,
                 from /usr/src/linux-2.6.10/include/linux/interrupt.h:11,
                 from /usr/src/linux-2.6.10/include/linux/netdevice.h:518,
                 from p80211conv.c:69:
/usr/src/linux-2.6.10/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/src/linux-2.6.10/include/linux/irq.h:21,
                 from /usr/src/linux-2.6.10/include/asm/hardirq.h:6,
                 from /usr/src/linux-2.6.10/include/linux/hardirq.h:6,
                 from /usr/src/linux-2.6.10/include/linux/interrupt.h:11,
                 from /usr/src/linux-2.6.10/include/linux/netdevice.h:518,
                 from p80211req.c:68:
/usr/src/linux-2.6.10/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/src/linux-2.6.10/include/linux/irq.h:21,
                 from /usr/src/linux-2.6.10/include/asm/hardirq.h:6,
                 from /usr/src/linux-2.6.10/include/linux/hardirq.h:6,
                 from /usr/src/linux-2.6.10/include/linux/interrupt.h:11,
                 from /usr/src/linux-2.6.10/include/linux/netdevice.h:518,
                 from p80211wext.c:47:
/usr/src/linux-2.6.10/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/src/linux-2.6.10/include/linux/irq.h:21,
                 from /usr/src/linux-2.6.10/include/asm/hardirq.h:6,
                 from /usr/src/linux-2.6.10/include/linux/hardirq.h:6,
                 from /usr/src/linux-2.6.10/include/linux/interrupt.h:11,
                 from /usr/src/linux-2.6.10/include/linux/netdevice.h:518,
                 from p80211wep.c:54:
/usr/src/linux-2.6.10/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/src/linux-2.6.10/include/linux/irq.h:21,
                 from /usr/src/linux-2.6.10/include/asm/hardirq.h:6,
                 from /usr/src/linux-2.6.10/include/linux/hardirq.h:6,
                 from /usr/src/linux-2.6.10/include/linux/interrupt.h:11,
                 from p80211netdev.c:68:
/usr/src/linux-2.6.10/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
In file included from /usr/src/linux-2.6.10/include/linux/irq.h:21,
                 from /usr/src/linux-2.6.10/include/asm/hardirq.h:6,
                 from /usr/src/linux-2.6.10/include/linux/hardirq.h:6,
                 from /usr/src/linux-2.6.10/include/linux/interrupt.h:11,
                 from /usr/src/linux-2.6.10/include/linux/netdevice.h:518,
                 from p80211mod.c:67:
/usr/src/linux-2.6.10/include/asm/irq.h:16:25: irq_vectors.h: No such file or directory
make[2]: *** [.depend] Error 1
make[2]: Leaving directory `/etc/kismet/linux-wlan-ng-0.2.0/src/p80211'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/etc/kismet/linux-wlan-ng-0.2.0/src'
make: *** [all] Error 2

it looks like something in my kernel sources is incomplete or missing. but /usr/src/linux-2.6.10 is where my kernel source is! [and 2.6.10 is what im running] i don't understand. but im getting so close!

---

### Post by nothreat33 on 2005-05-03
does kismet not work with 2.6.10 kernels or something?

---

### Post by jshein on 2005-05-03
What version of kismet are you running?

---

### Post by nothreat33 on 2005-05-03
i am running 2004.03.devel.a

---

### Post by jshein on 2005-05-03
try the version I listed earlier in this thread.

# wget http://mirror.aarnet.edu.au/debian/pool/main/k/kismet/kismet_2005.01.R1-2_i386.deb
# apt-get install ethereal-common
# dpkg -i kismet_2005.01.R1-2_i386.deb

---

### Post by nothreat33 on 2005-05-04
I dont' think the version matters, im just having trouble installing the wlann-ng driver to make it support monitor mode. in my 3rd post before this i have what the errors were while trying to install the driver. do i have an incomplete kernel source? or what

---

