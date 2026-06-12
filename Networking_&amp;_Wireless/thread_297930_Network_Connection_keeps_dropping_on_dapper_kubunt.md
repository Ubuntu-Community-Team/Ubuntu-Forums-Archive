---
title: "Network Connection keeps dropping on dapper kubuntu"
date: 2006-11-11
forum: Networking &amp; Wireless
---

### Post by elyse on 2006-11-11
Last weekend I migrated from SUSE 10.0 (which I have been using since February) to Kubuntu 6.06. I have several years experience with Red Hat/Fedora installed systems from before that. (And many years of UNIX admin experience before that.)

A couple of weeks ago, the apartment building where I am staying switched to Comcast Digital Cable, and the connections to the network were occasionally flakey after that.

The behavior I am seeing now is worse than flakey. I am finding it necessary to do a

sudo /etc/init.d/networking restart

every few minutes keep things connected. The connection seems to drop or hang (I'm not sure which) at any time, even when I am actively doing things in FTP sessions, so I don't think the problem is an inactivity timeout.

The admin tools provided by default inn Kubuntu seem... sparse. Are there packages that I should download that would help me figure out whether the problem is the Kubuntu installation or Comcast? (Adept seems to be able to handle the frequent reconnects, fortunately.)

Is this by any chance a known problem?

The laptop I am using has both a wireless and a wired network connection, and I have VMWare installed which complicates the network environment (though I don't think that things have gotten worse since I installed VMWare).

I tried disabling the wireless channel through the gui, but it appears to still be scanned and activated by the networking restart. Is there a config file I can hack to turn it off, in case it is interferingsomehow with the wired connection?

Thanks

Elyse

---

### Post by wieman01 on 2006-11-11
What chipset (wireless adapter) & router are you using? Please provide a few more details.

---

### Post by elyse on 2006-11-12
I'm Not using a router at all. I'm trying to use a cat 6 cable plugged directly into the Comcast cablemodem. 

And I'm trying to disable the wireless on the theory that it may be interfering with the wired connection. One of my neighbors may have a strong wirelss router.

I'm leaning more and more to that theory, actually... I went into system settings and fed ath0 bogus ESSID and WEP settings, as well as disabling it, and things have been fairly stable. Or it could just be that it is now late at night and the Comcasr Cable modem is not very busy.

It would help if KInfo center would allow copying of the data it displays.

eth0 seems be SiS900 PCI Fast Internet (rev 91) and 
ath0 (the wireless connection) seems to be 
Atheros Communications AR5212 802.11abg NIC Rev (01)

This is a LinuxCertified laptop that never had Windows on it except as a VMWare guest, so the chipsets are well supported except for the modem, which I've never tried to use.

---

### Post by wieman01 on 2006-11-12
Mmm... I have never heard of wired connections being unstable... Yes, perhaps disabling the Atheros wireless adapter helps. As far as I know it creates problems on the wireless end(!) if you have both interfaces enabled at the same time. I can imagine the same holds true the other way around as well.

Sorry I cannot be of more help.

---

### Post by elyse on 2006-11-12
It looks like stopping the atheros interface did work. But just disabling it in the GUI is not enough (on a laptop that is not left on all the time) because it comes back on reboot. Configuring it to look for non-existent ESSID and WEP values seems to keep it from coming up, however.

Now I need to check my backups from before the upgrade...the real ESSID and WEP for my home network were what was probably preventing problems in the SuSE configuration. And since I'm going home in a couple of weeks, it would help to know what they are.

Thanks for the help.

---

