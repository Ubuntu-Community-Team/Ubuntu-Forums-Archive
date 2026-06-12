---
title: "final try with intel 3945"
date: 2007-12-10
forum: Networking &amp; Wireless
---

### Post by stlcoptony on 2007-12-10
Ok, I have searched all over and tried  quite a few solutions I found on here, but I have to get my Intel pro 3945 abg card working correctly with my laptop. I have tried a whole bunch of distros to see if they worked, but no luck (and I just like ubuntu better, once I get rid of the brown). I know there are other posts on this, but can someone help me with diagnosing and fixing this problem? I am considering getting another laptop for linux only, but all the ones I have found also seem to have this intel 3945 wifi card. Please help me get this running

thanks

---

### Post by eriksallstrom on 2007-12-10
For me the intel 3945 wireless works just fine... Exactly what is your problem? Have you checked System=>Administration=>Restricted Drivers Manager that the driver is loaded?

---

### Post by stlcoptony on 2007-12-10
yes. I have even tried to get the iwl3945 driver and the ndiswrapper to work with no luck (ndiswrapper seemed to work, but the system kept freezing and I've completely forgotten how I got it to work). When I install, it loads the restricted ipq3945 driver and I can connect to the internet, but at superslow speeds. Using synaptic, for example, the speed varies from some number of BITS/s up to a max of 25-30kb/s. I have yet to find a way to fix this.

thanks

---

### Post by mikewhatever on 2007-12-10
That wireless card should work out of the box and even running from the cd. You don't have to install anything. What exactly is the problem?

---

### Post by lincolnlad on 2007-12-10
You don't need to use ndiswrapper.  The restricted driver works fine on it's own.  It's a driver written by intel for their own card.

[http://intellinuxwireless.org/](http://intellinuxwireless.org/)

Does the restricted drivers manager show that it's enabled (with a tick) and in use?

---

### Post by stlcoptony on 2007-12-10
Yes, it is enabled and I have a connection with it. The problem is the speed. I get a max of about 25-30 kb/s. when I boot into windows on the laptop using the same router, I always get around 300-400kb/s

thanks, please help

---

### Post by crumja on 2007-12-10
Yah, I had several problems with ipw3945 (default driver in gutsy) for my 3945 card. A better choice is to use the iwlwifi driver cuz it's faster, has more features, and is a bit more stable.

First try these:

Open /etc/modprobe.d/blacklist and add 

blacklist ipw3945
blacklist ieee80211
blacklist ieee80211_crypt

to the end.

Then open /etc/modules and add
iwl3945
to the end.

Reboot and see results.

The bundled driver is a bit outdated, so if you want a more updated version, instruction on compiling this is at [http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html](http://kuscsik.blogspot.com/2007/06/how-to-install-intel-4965-wireless.html)
Just change the 4965 to 3945 and download the most recent sources.

Best of luck

---

### Post by stlcoptony on 2007-12-10
do I need to download the iwl3945 driver first? before adding it to /etc/modules, how do I install it?

thanks

---

### Post by stlcoptony on 2007-12-10
I followed the guide mentioned above for using the iwl driver. after blacklisting the old one and the ieee things, and adding iwl3945 to /etc/modules I restarted. now i can detect the wireless networks in range but I can't connect to any of them. The network manager just keeps "spinning" without any of the little green lights lighting up. Is there something else I should be doing?

thanks

---

### Post by eriksallstrom on 2007-12-10
I stopped using the network manager after the gutsy upgrade, since it seemed to cause some problems for me. If you run the command line tools instead, you will get some feedback about what's happening. 

You probably know the name of your router, but if you don't, you can run

sudo iwlist [wirelessdevice] scan

Then you can select the router to use with
sudo iwconfig [wirelessdevice] essid [name_of_router]

Or, if there are many people using the same router name like where I am
sudo iwconfig [wirelessdevice] essid off ap [XX:XX:XX:XX:XX:XX]

Where [XX:XX:XX:XX:XX:XX] is what you see after "Address:" when you run iwlist. When/if you succed to connect to the network, your wireless indicator will be lit up now. Then you can run:

sudo dhclient [wirelessdevice]

To get an IP from the DHCP server, assuming you're not using a static IP. I haven't used iwconfig with a password protected network, but if that's what you're using you should be able to find out how to use it in the manual.

If it doesn't work, now at least you should know what part it is that fails. Good luck!

---

### Post by MozartlovesUbun2 on 2007-12-10
try **WICD**

---

### Post by stlcoptony on 2007-12-10
> **eriksallstrom said:**
> I stopped using the network manager after the gutsy upgrade, since it seemed to cause some problems for me. If you run the command line tools instead, you will get some feedback about what's happening. 

You probably know the name of your router, but if you don't, you can run

sudo iwlist [wirelessdevice] scan

Then you can select the router to use with
sudo iwconfig [wirelessdevice] essid [name_of_router]

Or, if there are many people using the same router name like where I am
sudo iwconfig [wirelessdevice] essid off ap [XX:XX:XX:XX:XX:XX]

Where [XX:XX:XX:XX:XX:XX] is what you see after "Address:" when you run iwlist. When/if you succed to connect to the network, your wireless indicator will be lit up now. Then you can run:

sudo dhclient [wirelessdevice]

To get an IP from the DHCP server, assuming you're not using a static IP. I haven't used iwconfig with a password protected network, but if that's what you're using you should be able to find out how to use it in the manual.

If it doesn't work, now at least you should know what part it is that fails. Good luck!

where do I find the name of my wireless device? also is "name_of_router" the ssid?

thanks

---

