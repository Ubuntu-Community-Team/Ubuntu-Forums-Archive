---
title: "DNS settings not correct on boot-up with DSL?"
date: 2007-03-05
forum: Networking &amp; Wireless
---

### Post by jamyskis on 2007-03-05
Hi everybody,

Until recently my DSL connection was working fine with Ubuntu. Now recently, every time I boot up, I get a swathe of error messages complaining that the domain names could not be resolved. I can access a number of pages through IP addresses, and Skype logs in fine. The only way I've been able to resolve this is to enter a terminal and type:

```

sudo poff -a
pon dsl-provider

```

Which I assume is refinding the DNS servers from my provider instead of a couple of predefined ones that I had stored somewhere to be called at boot-up. Is this a correct assumption? Does anyone have any suggestions as to what to do here?

Thanks!
J

---

### Post by zvacet on 2007-03-05
Did you put your DNS in networks ettings>DNS?If you did and still no luck try this
> [http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29]("http://easylinux.info/wiki/Ubuntu_Edgy#How_to_install_Broadband_ADSL.2FPPPoE_Client_.28RP-PPPoE.29")
Replace Exec=gksudo /opt/rp-pppoe-3.8/go-gui with  Exec=gksudo tkpppoe
Restart.Programs>internet>rp-ppoe
First time may take some time before you see GUI.If you don´t get GUI do this
```
sudo -i
```
```
cd /opt/rp-pppoe
```
```
root@localhost rp-pppoe#./go
```[/QUOTE]
P.S.maybe corect name is rp-pppoe3.8

---

### Post by jamyskis on 2007-03-07
For whatever reason it's fixed itself. I think my ISP might have been having some probs with its DNS servers, I had been having a few problems connecting under both WIndows and Linux for a couple of days there. Thanks for the advice anyway :mrgreen:

---

### Post by Mr. C. on 2007-03-07
If the problem with your ISPs DNS servers continues, you can install your own local DNS server for your private network.  It will be a caching server, just looking up results for your net's use.

MrC

---

