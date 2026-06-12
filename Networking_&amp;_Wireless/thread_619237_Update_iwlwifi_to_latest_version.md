---
title: "Update iwlwifi to latest version"
date: 2007-11-21
forum: Networking &amp; Wireless
---

### Post by Kenknif on 2007-11-21
Hello, I am a really new person in the world of Linux.

I found out that my network card (intel 4965 AGN) isn't working with wpa_supplicant.
Now is there a new version of the driver (iwlwifis 1.2.0.) and it has some fixes for this problem.

I want to upgrade my existing driver. 

How do I do this?

I am using ubuntu 7.10 on a Dell Latitude D830.
My wireless card is working as is should at my partents home (just a WPE key).
At my university I need wpa_supplicant, which is not working.

Thanks for your help,

Kenneth.

---

### Post by Blutack on 2007-11-21
I would imagine you need to remove the old driver using Synaptic, install a package called build essentials which lets you build stuff from source, then head over to the intel site and download your driver.
Then read the section of this called Installing from source
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by kiloecho7 on 2007-11-22
Howdy there Keneth,

I've been toying around myself with the idea of updating the iwlwifi stack from intel's site, but I'm not quite sure that's what I'd do if I were you.  Your best bet is to use wicd instead of the network manager suite, which is pretty easy.  Many people who have trouble with encryption in NM seem to be happy with wicd as a wireless tool.  Here is the link for installing wicd in Ubuntu.

[http://wicd.sourceforge.net/download.php](http://wicd.sourceforge.net/download.php)

Once the wicd package appears in Synaptic and you install it, it will automatically remove network manager and everything else (but keep them in the cache just in case you have to reinstall without internet).

Hope that solves your problems, If not then here is how you should go about removing the current iwlwifi stack.  Note that I could not find instructions specifically on the net for this, it's just how I would do it.

# modprobe -r iwl4965
# modprobe -r iwlwifi_mac80211
# rmmod -w iwl4965
# rmmod -w iwlwifi_mac80211

Then follow the instructions on mac80211 from [http://www.intellinuxwireless.org/?p=mac80211&n=HOWTO-mac80211](http://www.intellinuxwireless.org/?p=mac80211&n=HOWTO-mac80211)
and then the iwlwifi instructions from [http://www.intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi](http://www.intellinuxwireless.org/?p=iwlwifi&n=HOWTO-iwlwifi).

Hope that helps.  Please post back if it does!

Matt

---

### Post by mcade on 2008-01-24
I have a 4965 card that works fine when I'm at home, on my less than super-secure wireless network.  But, at school, I can't get connected to the encrypted network.  I've messed around with wpa_supplicant and wicd a bunch, matching the config files of others who have success with the network there.   The post about iwlwifi got me interested and I tried to follow the directions at [http://www.intellinuxwireless.org/?p...=HOWTO-iwlwifi](http://www.intellinuxwireless.org/?p...=HOWTO-iwlwifi) to get it done but I get no mojo there either.  

I wanted to update mac80211 before updating iwlwifi.  So, I started there. I get all the way to 
%make modules modules_install

And I get:
make[1]: *** No rule to make target `arch/x86_64/kernel/asm-offsets.c', needed by `arch/x86_64/kernel/asm-offsets.s'.  Stop.
make: *** [prepare0] Error 2

What do I do?
I'm new to all this kernel building and whatnot, so take it easy on me.

thanks!

-m

---

