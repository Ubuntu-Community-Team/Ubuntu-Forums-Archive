---
title: "Updating intel 4965 driver to use injection"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by ztrange on 2008-10-09
Hi, I was reading the [guide for using iwl4965 for intel 4965 agn WIFI card]("http://ubuntuforums.org/showthread.php?t=493095&highlight=driver+update+4965")

I was planning to update my 4965 driver in hardy to the last version and then patch it to be able to use the patch for injection mentioned here:

[http://airdump.net/packet-injection-wifi-intel-4965/](http://airdump.net/packet-injection-wifi-intel-4965/)

While doing it I got stucked at updating the mac80211 to the newest version, after getting

mac80211-8.0.x.tgz
iwlwifi-4965-ucode-4.44.xx.tgz
iwlwifi-0.0.xx.tgz

from [http://intellinuxwireless.org/?n=Downloads](http://intellinuxwireless.org/?n=Downloads)

then

sudo ln -s /usr/src/linux-headers-$(uname -r) /lib/modules/$(uname -r)/source

and then

tar zxvf mac80211-8.0.x.tgz
tar zxvf iwlwifi-4965-ucode-4.44.xx.tgz
tar zxvf iwlwifi-0.0.xx.tgz

cd mac80211-8.0.x
sudo make patch_kernel

but whe I did that, if told me the following:

NOTE:  As of mac80211-2.0.0, kernel built-ins for the wireless extension 
handlers have been replaced with built-ins provided by mac80211.  This 
requires you to rebuild your main kernel image and reboot to that 
kernel in order to use the mac80211 subsystem.  We are looking for ways 
to correct this in the future.

So, Im wondering if I will have to compile kernel to replace the mac80211 original module. If so, I would like to know if I wont get stuck at some non-reverse point before i successfully replace the module. Would you recommend me to rebuild the kernel?

Also, maybe you know if the intrepid final will have the last mac80211 and iwlwifi for intel 4965, maybe I can wait 20 days to avoid all this problems

---

### Post by ztrange on 2008-10-13
bump!

---

### Post by ztrange on 2008-10-16
Well, I just finished following this guide and I think it will be just fine, havent made but simple tests.

[http://jptips.blogspot.com/2008/07/ubuntu-804-ipw4965-aircrack-v2.html](http://jptips.blogspot.com/2008/07/ubuntu-804-ipw4965-aircrack-v2.html)

---

### Post by yakkeh on 2008-12-28
Pretty cool that you post the solution to your problem but I have no clue what is written in Spanish on this last webpage.

Would you be even cooler and post the stuff that was missing from the other guides in English?
I'm sure it will be appreciated by many :)

---

