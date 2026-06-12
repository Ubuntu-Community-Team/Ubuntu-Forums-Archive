---
title: "No longer able to access internet"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by Strman on 2007-12-10
Hello, I just started dual-booting Ubuntu on my Vista machine, so I am completely new to Linux.  After I first installed the OS, the internet was working well.  I downloaded the Compiz customization thing, and everything was still going smoothly.   I then went to download "Moblock", as it seemed to be the recommended alternative to Peer Guardian.  After numerous failed attempts at installing it, I tried to find some support online, but I was not able to access any website.  Firefox wouldn't load any of the pages.

I am by no means an expert with computer software, so all I knew was to try some of the basic stuff.  I turned my modem off and on and restarted the computer, I went through the help file's steps on setting up an internet connection, etc.  Does anyone here have an idea as to what I did wrong? In case you need to know some basic system information, I am dual booting Ubuntu 7.10 with Vista Ultimate 64bit. I'll be glad to let you know of any other info if you need it.

Thanks
-Max

---

### Post by HermanAB on 2007-12-10
Hmm, I recommend that you re-install.  It only takes about 30 minutes - much less time than to debug the problem.

Then, once you have it working again, install VMware server and install a copy of Ubuntu inside that.  Then you can experiment to your heart's content, without fear of screwing up your base system again.

Cheers,

Herman

---

### Post by kajillin on 2007-12-11
I had the same issue with moblock, after i installed it it locked my computer out of my network. Because of their lack of docs and help i just uninstalled it, and got my internet back. Also after the install it would just load the loopback on startup instesd of my ethernet card, so try this.


```
sudo gedit /etc/network/interfaces
```

and comment these out, 

The loopback network interface
auto lo
iface lo inet loopback


stopped the loopback from loading.

Also type "ifconfig" and see if your network card is listed cuz it could be a driver issue?

---

### Post by goodtimetribe on 2007-12-17
> **kajillin said:**
> I had the same issue with moblock, after i installed it it locked my computer out of my network. Because of their lack of docs and help i just uninstalled it, and got my internet back. Also after the install it would just load the loopback on startup instesd of my ethernet card, so try this.


```
sudo gedit /etc/network/interfaces
```

and comment these out, 

The loopback network interface
auto lo
iface lo inet loopback


stopped the loopback from loading.

Also type "ifconfig" and see if your network card is listed cuz it could be a driver issue?

No, my loopback still loads. I'd been using moblock for awhile, and now that I've upgraded moblock today, and said yes to using their moblock.conf file, i'm now unable to access the internet when moblock has been started. I'm able to access it again by running

```
sudo moblock-config stop
```

Of course this causes me to not be able to access the internet when moblock is running :(

---

### Post by goodtimetribe on 2007-12-17
> **Strman said:**
> Hello, I just started dual-booting Ubuntu on my Vista machine, so I am completely new to Linux.  After I first installed the OS, the internet was working well.  I downloaded the Compiz customization thing, and everything was still going smoothly.   I then went to download "Moblock", as it seemed to be the recommended alternative to Peer Guardian.  After numerous failed attempts at installing it, I tried to find some support online, but I was not able to access any website.  Firefox wouldn't load any of the pages.

I am by no means an expert with computer software, so all I knew was to try some of the basic stuff.  I turned my modem off and on and restarted the computer, I went through the help file's steps on setting up an internet connection, etc.  Does anyone here have an idea as to what I did wrong? In case you need to know some basic system information, I am dual booting Ubuntu 7.10 with Vista Ultimate 64bit. I'll be glad to let you know of any other info if you need it.

Thanks
-Max

I think I fixed it. I noticed that I was able to access things by IP but not by FQDN, so I checked Wikipedia for the ports used by DNS and mDNS. I added those to my whitelist and I'm now able to browse the internet and keep moblock running.

nice.

---

### Post by jre on 2007-12-21
> **goodtimetribe said:**
> I think I fixed it. I noticed that I was able to access things by IP but not by FQDN, so I checked Wikipedia for the ports used by DNS and mDNS. I added those to my whitelist and I'm now able to browse the internet and keep moblock running.

nice. Absolutely correct. It´s THE feature of MoBlock to block certain IPs. If it blocks too much (this happens often) you can whitelist IPs and/or ports in /etc/moblock/moblock.conf

greets
jre

---

