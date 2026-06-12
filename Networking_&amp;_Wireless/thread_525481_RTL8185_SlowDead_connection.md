---
title: "RTL8185 Slow/Dead connection"
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by scifi76 on 2007-08-14
The other day I bought a wireless network card. I wasn't sure what card would work best under ubuntu so I decided just to grab the first one with a Linux penguin on it :-) This card turned out to be a Safecom SWLPR-5400 using a Realtek 8185 chipset.

This card was shipped with native linux drivers but unfortunately they are outdated and don't seem to work on ubuntu. I finally got the card working with ndiswrapper and I thought my journey was done... I was wrong.

I am able to connect to my router and can browse the internet (barely), but regularly the connection will seem to drop or go idle. For example, I will navigate to a web page and the page will start to load but then my connection goes idle and the page will remain half loaded. Sometimes my connection will pick back up, but it will quickly drop off again. This cycle of connection/dropping happens very quickly and randomly causing the connection to appear to be going very slow. Other times the connection will not pick back up at all without a reboot. Speedtests report my connection being incredibly slow. I have used a wireless connection monitor tool to view the send/receive status during a speedtest and I will see that the connection sends/receieves fine for the first second or two, but then immediately becomes completely idle.

Finally, I am sure that this is an issue with the network card as, when the connection is idling, I am unable to access anything on the local network as well as the internet. Also I have been testing with the router next to my wireless card. Once I even managed to do a speedtest at just the right moment that the connection didn't drop and it reported ~6-7Mb which is the kind of speed I'm used to when using a wired connection. (Speedtests currently report speeds less than 256k or some speedtests freak out because my connection refuses to finish the download!)

Anyone have any ideas or has anyone got this same chipset and can offer advice? Even better I would love to hear from anyone who has bought the same safecom SWLPR-5400 card?

---

### Post by scifi76 on 2007-08-14
For anyone interested, I thought my problem may have been related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940]("https://bugs.launchpad.net/ubuntu/+source/avahi/+bug/94940")

so I edited /etc/nsswitch.conf as suggested, but I havn't noticed any change.

I also did another test. I pinged microsoft.com from my ubuntu machine and compared it to the ping results from my windows machine. Both machines return an average response time of about 200ms per request, however the windows machine carries out 4  ping requests in about 3.5 seconds while the ubuntu machine takes upwards of 30 seconds, or in some cases is unable to find the host at all.

I'm not an expert in networking, so can anyone explain what this could be? Some help would be much appreciated.

---

### Post by scott_evil on 2007-08-14
I believe the Realtek 818x drivers are built into the kernel and need to be blacklisted before using ndiswrapper.

edit the /etc/modprobe.d/blacklist file and add entries for 

blacklist rtl818x
blacklist rtl8185
blacklist r818x
blacklist r8185

I believe you need to restart for the kernel to ignore the drivers.

---

### Post by scifi76 on 2007-08-15
Ok I will try this when I get home and will post back the results. Would ubuntu's built in driver really be causing this problem though?

Just for good measure I will also remove and re-install the driver I'm using through ndiswrapper after blacklisting the built in one

cheers for the response

---

### Post by scifi76 on 2007-08-15
Just found a post that says the realtek 818x drivers are blacklisted by default on 7.04. Nevertheless I will check later.

---

### Post by scifi76 on 2007-08-15
An update and a bump because I could really use some help with this...

I checked my blacklist and rtl818x was already blacklisted, but just for good measure I also added rtl8185 and r8185. Also I removed the driver from ndiswrapper, removed network manager (i hear this causes problems sometimes) and re-installed the ndiswrapper driver. Still no cookie :-(

Has anyone had any luck using the native rtl818x drivers by un-blacklisting it?

Also could the following output from ndiswrapper -l be significant?

```
ndiswrapper -l

net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)

```

namely the "alternate driver: r818x" bit concerns me.

---

### Post by scifi76 on 2007-08-16
bump

---

### Post by macross3003 on 2007-08-26
Had you tried with this module? [http://rtl-wifi.sourceforge.net/wiki/Main_Page](http://rtl-wifi.sourceforge.net/wiki/Main_Page)

---

