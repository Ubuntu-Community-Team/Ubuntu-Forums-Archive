---
title: "[SOLVED] How can I connect to signal on Channel 13 with Netgear WG511T?"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by williamek on 2007-10-03
Hi all,

I recently purchased a Netgear WG511T wireless card (Atheros chipset) because I read on these forums that it works out of the box with Ubuntu - except in my case it doesnt. 

After doing some research I'm fairly sure the problem is that my router is broadcasting on channel 13, which is illegal in the States (Channels 1-11 only there), but used elsewhere (I'm in the UK). I know the card itself works because it runs fine on my windows partition. 

I've tried connecting both with and without the restricted drivers that Feisty uses for the card, and I've tried uninstalling network manager and using wicd instead but to no avail, neither can find the broadcast SSID.  

'iwconfig' finds the card under ath0 but

'sudo iwconfig ath0 channel 13' returns:
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device ath0 ; Invalid argument.


Presumably there's a file somewhere with the country settings for networking that I can edit, but I cannot find it. (I know the easiest thing would be to change the router settings but I cannot do that for various reasons).

All help appreciated.
Thanks!

---

### Post by noob12 on 2007-10-03
It sounds like you are using the ath_pci driver.  This applies to that.

Use 
```

sudo sysctl -a | grep country

```

to determine your country code (or use [http://en.wikipedia.org/wiki/ISO_3166-1_numeric](http://en.wikipedia.org/wiki/ISO_3166-1_numeric))

The UK is 826

Use that code to set the option "countrycode" on the ath_pci driver when loading it.  This adds a line that to do that to the file /etc/modprobe.d/options.

```

echo "options ath_pci countrycode=826" | sudo tee -a /etc/modprobe.d/options.

```

Reboot.

Ref:   [http://madwifi.org/wiki/UserDocs/CountryCode](http://madwifi.org/wiki/UserDocs/CountryCode)

Note:  The ath_pci driver shipped in Ubuntu 7.04 is dated.  You may do better to download the latest drivers from source and build them yourself.

---

### Post by williamek on 2007-10-05
Thanks!  That worked!

---

