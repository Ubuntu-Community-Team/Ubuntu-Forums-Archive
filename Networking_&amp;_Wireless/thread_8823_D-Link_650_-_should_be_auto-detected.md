---
title: "D-Link 650 - should be auto-detected"
date: 2004-12-21
forum: Networking &amp; Wireless
---

### Post by steffen on 2004-12-21
Hi,

Probably a newbie question:

- I have a D-Link 650 wireless card. From the Ubuntu official Wiki, this card should be auto-detected, and even ask for the Wep key when inserted. I suspect there might be something wrong with my hotplugging somewhere, because this does not happen.

- When I insert the card, the light starts blinking. Nothing happens. I then go to Network config under system config, and select to 'Add new'. I go through all the steps, clicking 'Wireless connection and 'Eth1', and adding my wep key.

- When I then try to activate the connection, nothing happens. The little blocks simply gets unchecked after 5 seconds or so, and no connection is detect - I suspect not even the card gets detected.

I have also tried restarting the machine. I have a couple of modprobe errors when booting Ubuntu - could this be the problem?

---

### Post by steffen on 2004-12-22
The error I get when starting the laptop is when Ubuntu attempts to load the hotplugging stuff. I get error 

modprobe: Fatal error inserting pciehp (path to pciehp.ko)

and also

modprobe: Fatal error inserting shpchp (path to shpchp.ko)

Anyone know what this could be?

I actually managed to solve some of the problem by searching for 'prism' with apt-get, and installing all I could find that related to wireless. Now the LED on the card is not blinking anymore - the light is constant. I presume that is because it is now connected somewhat to the computer.

However, no wireless device is detected, and the only networking hardware I can find in my Network config is eth0, which is my ethernet cable. This is also the only one my wireless applet is able to find.

---

### Post by torque2k on 2004-12-29
Hi!

I'm new to Ubuntu, but have been using various Linux distros for quite some time. Just thought I'd say that upfront.  :)

I've also got a DWL-650, which I had plugged in while doing the installation of Ubuntu. It picked up my card perfectly. I will say, though, that historically I've had issues getting Linux wireless of any type to work with WEP enabled! Dunno what I do wrong, but it never works for me.

Currently, I have a Belkin 11g access point, and no WEP enabled (I live way out in the country), and the D-Link card works perfectly. 

Try disabling WEP on your router for testing purposes. If it works, that's your issue, and hopefully you can then move on to asking "Why can't I get WEP working?". 

Also, if memory serves me correctly, D-Link had multiple versions of the DWL-650 which were released. Even under Windows, it was a problematic card. Mine is the original type, with the plastic antenna pod shaped like a wedge and not squared off with the rest of the card. This particular card won't work on my wife's HP Omnibook XE3, but works fine in my Compaq Evo N610c. YMMV...

Good luck, hope this points you in the right direction!

EDIT: Also, forgot to mention, I had the same issues with the "pciehp, etc." errors, and found this to be helpful in eradicating them: [http://ubuntuguide.org/#modprobefatalerror](http://ubuntuguide.org/#modprobefatalerror)

---

### Post by clsdaniel on 2004-12-31
Try updating you linux-wlan-ng package, i did on mine and it worked flawlessly when inserted the card (i have the same card).

Also you can compile the package yourself.

Also, your access point support 802.11b?, because my card only support b not g.

Good Luck.

---

### Post by cllow on 2005-01-02
Hi, I'm also new to Ubuntu, and Linux as well for that matter.

Anyway, I'm using D-Link 650+ wireless card. I had the same issue during installation via the default mode. The installation is not able to detect the card. What I did was to install via the expert mode; and the card is detected every time, and after that, u will be prompted to enter SSID, WEP key, IP addresses, etc. Btw, I have WEP enabled as well.

I have tried SUSE, ASPLinux, Mandrake and Yoper and Ubuntu is the only distribution that have no problem, well maybe a little, detecting the D-Link 650+.

Hope that helps. Good luck.

---

### Post by torque2k on 2005-01-04
[QUOTE=clsdaniel]Also, your access point support 802.11b?, because my card only support b not g.[/QUOTE]
802.11g access points / routers are backward-compatible with 802.11b devices (NICs). That said, if you have 11g devices connecting to an 11g AP, you'll get 54MBit-ish speeds, but once you introduce an 11b device, the AP (and all client devices running on 11g) will fall back to 11b speeds (that's the main problem with 11g). 802.11a, though NOT compatible with 11b/g, will not fall back to 11MBit speeds if an 11b device is connected. An AP with both the 11a and 11g chipsets is great, because 11a devices can still cruise at full speed, while 11b devices can connect with 11g ones for max compatibility.

Or something like that.  8-)

---

### Post by plichodz on 2005-01-18
I installed Ubuntu using the default option and my DWL-650+ (acx100 I think) card was detected. However, it wasn't set up automatcally and it never asked me for any details when I inserted it.

I was able to get around this by editing /etc/network/interfaces and adding the appropriate settings there. For more info have a look at /usr/share/doc/wireless-tools/README.Debian where several examples are given. In 
my particular case, I set the essid, mode, keymode, and WEP key.

Of course, this is only if you want to connect to the same access point all the time, which is great for me as I only use the wireless network at home.

---

### Post by Davepet on 2005-01-28
Ah, yes, the DWL-650. Even though they all have the same model # there are at least 4 & maybe as many as 6 versions of this card. Go to the dlink support site  to get some idea of which one you have.

Plugging the fcc # in at the fcc site enabled me to identify mine as having the ADMTek 8211 chipset. There are now open source drivers available here:
[http://aluminum.sourmilk.net/adm8211/](http://aluminum.sourmilk.net/adm8211/)

I've got it working in Ubuntu as i write this. Those folks with DWL650g cards need not apply, your card has nothing in common with the dwl-650b cards except for the DWL-650 name.

Dlink needs to be dragged over the coals for not providing obvious model designations when they make major changes in their product.What they have done should be illegal

Dave

---

### Post by NewbieNik on 2005-01-29
I have to jump in on this...Steffan, you have mentioned setting up the network manually using ETH1...The D-Link card should show as ATH0. Could be a source of the issue.
I have also had issues with Ubuntu and wireless and as a newbie to Linux I think these forums are amazingly helpful (Bill, if you're listening..take note!!) and one thing I have discovered is that setting the WEP key through the networking GUI sometimes doesn't work.
Try using the terminals and entering "sudo iwconfig ath0 key xxxxxxxxxx" The x's being your WEP key. I found this out by an experimental install on a laptop with an Intel On-Board Wireless card!

Hope this is of some use...

---

### Post by Jaxilian on 2007-05-02
I have a DWL-650+ card that I use for my Evo N610C laptop and it detected it automatically in Ubuntu 7.04. Just clicked which wlan I wanted to use and it worked.

---

