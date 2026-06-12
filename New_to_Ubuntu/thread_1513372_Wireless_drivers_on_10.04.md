---
title: "Wireless drivers on 10.04"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by Sandy.1 on 2010-06-19
I'm wanting to try out 10.04 from a live CD

I appear to have a choice between Broadcom B43 and Broadcom STA wireless drivers

But I don't know anything about either of them.

And I can't get either of them to 'activate'

Help

Sandy

---

### Post by ieee488 on 2010-06-19
If you don't have a Broadcom chipset then neither is going to work for you.

[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by cariboo on 2010-06-19
You can install the STA driver from the Live CD, make sure it is selected in System->Administration->Software Sources. 

I personally just connect a network cable and download the restricted driver and install it that way.

You may have to add the b43 driver to the blacklist. To do so, press Alt-F2 and type:

```
gksu gedit /etc/modprobe.d/blacklist.conf
```

this will open the blacklist.conf file as root so you can edit it. At the bottom of the file add the following:

```
blacklist b43
```

save the file then reboot. You should now be able to use wireless.

---

### Post by Sandy.1 on 2010-06-23
Well I think I followed your advice. Not sure that I knew what I was doing but it appears to have worked and I now have my wireless connection working.#

Didn't persist with blacklisting the other driver, far too complicated for me yet.

Thanks   Sandy

---

### Post by bwallum on 2010-06-23
As a point of interest, if I install Ubuntu without a wireless card (so that it doesn't load the appropriate driver), then install a wireless card and run the liveCD; does the driver reside in the liveCD 'temporary' environment (and subsequently get removed when closing down the liveCD) or does it copy over to the previously installed system?

---

### Post by mörgæs on 2010-06-23
> **bwallum said:**
> As a point of interest, if I install Ubuntu without a wireless card (so that it doesn't load the appropriate driver), then install a wireless card and run the liveCD; does the driver reside in the liveCD 'temporary' environment (and subsequently get removed when closing down the liveCD) or does it copy over to the previously installed system?

If booted with the live CD, only the temporary environment is active. It will not make changes to the system on the hard drive unless you actively decide to do so (if you open a config file on the hard drive and edit it, for example).

---

