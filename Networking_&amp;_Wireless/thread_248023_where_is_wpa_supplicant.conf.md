---
title: "where is wpa_supplicant.conf"
date: 2006-08-31
forum: Networking &amp; Wireless
---

### Post by Beliar on 2006-08-31
Hi,
I'm looking for the wpa_supplicant.conf, but there seems to be none!
I managed to get my WLAN working with the gnome network manager applet, but the WLAN in my school is much more complecated and I wont be able to configure it with that applet.

Under gentoo Linux, I got it working. Now I wanted to add a section for that WLAN to my wpa_supplicant.conf, but there is none x(
It should be under /etc/wpa_supplicant.conf. 
I had a look at the wpa_supplicant daemon. Under gentoo, you could see the parameter -c where the config file is, but it doesnt run with that parameter.
I also cant find it with locate...

Does anyone know where to look for it?

greets, 
Ben

---

### Post by UrbenLegend on 2006-08-31
I am having the same problem. I can't find /etc/wpa_supplicant.conf, nor /etc/default/wpa_supplicant.conf nor /etc/init.d/wpa_supplicant. A person on the IRC told me that I had to create them myself, but so far I have had no success.

Seriously, Ubuntu needs to take a page out of SUSE's book and provide an easy wpa configuration tool.

---

### Post by Beliar on 2006-08-31
The network manager tool is nice and I dont think Ubuntu should become more like SuSe.
I think there should be a GUI for stuff, but also the old configuration file way to configure stuff.
For simple WLANs with pre shared key is the network manager really great. 
But I want a WLAN with cerificate and stuff.
Well its also simple with Windows, so its possible with a GUI...

---

### Post by phubai on 2006-08-31
Well, on mine:

```
whereis wpa_supplicant.conf
```

resulted in:

```
wpa_supplicant: /sbin/wpa_supplicant /etc/wpa_supplicant /usr/share/man/man8/wpa_supplicant.8.gz

```
So, when I looked in /etc/wpa_supplicant, I found ifupdown.sh and I think you may find what you're looking for there.

g'luck!

---

### Post by Beliar on 2006-09-01
Hi,
thanks, I found that too.
But it seems to be some kinf of script and I dont think its what i'm looking for.

---

### Post by UrbenLegend on 2006-09-01
> The network manager tool is nice and I dont think Ubuntu should become more like SuSe.

I didn't say Ubuntu should be more like Suse. I meant that Ubuntu should provide some decent GUI configuration tools like Suse, tools that regular people can use. After all, doesn't Ubuntu mean humanity? I think somebody should add WPA functionality into the network manager. Shouldn't be that hard.

> So, when I looked in /etc/wpa_supplicant, I found ifupdown.sh and I think you may find what you're looking for there.

Yeah it looks like some kind of start up script. /etc/wpa_supplicant.conf is supposed to be a file where you can put your pre-shared keys in. I think you can create your own file and put the output of 'wpa_passphrase *ssid* *password*' into that file. However that's not the only problem you'll be having. Even if that file exists, wpa_supplicant won't start up on boot under dapper drake because other files are missing, like /etc/init.d/wpa_supplicant. You always have to launch it yourself using the wpa_supplicant command in the terminal. Anyone know how to fix this?

---

### Post by Zed on 2006-09-01
[WPA Howto](https://help.ubuntu.com/community/WifiDocs/WPAHowTo/wpa)

You create your own wpa_supplicant.conf. Looks like you need to add an /etc/default/wpasupplicant file, too, but not an /etc/init.d/wpasupplicant.

---

### Post by domib on 2006-09-03
> **UrbenLegend said:**
>  /etc/wpa_supplicant.conf is supposed to be a file where you can put your pre-shared keys in. I think you can create your own file and put the output of 'wpa_passphrase *ssid* *password*' into that file. However that's not the only problem you'll be having. Even if that file exists, wpa_supplicant won't start up on boot under dapper drake because other files are missing, like /etc/init.d/wpa_supplicant. You always have to launch it yourself using the wpa_supplicant command in the terminal. Anyone know how to fix this?

In my Dapper install, wpa_supplicant is running on boot. I haven't done anything to make this happen, it's just happening:

```
$ ps -efl | grep wpa
5 S root      3337     1  0  74  -2 -   834 -      12:37 ?        00:00:00 /sbin/wpa_supplicant -B -P /var/run/wpa_supplicant.eth1.pid -i eth1 -C /var/run/wpa_supplicant -D wext

```

Which means wpa_supplicant is running without a configuration file. I can't find where this command is coming from to change it to read a config file. However, the newest debian method for configuring WPA is with wpa directives in /etc/network/interfaces:

```

auto eth1
iface eth1 inet dhcp
        wpa-driver wext
        wpa-scan-ssid 1
        wpa-conf managed
        wpa-ssid mySecretSSID
        wpa-key-mgmt WPA-PSK
        wpa-proto WPA
        wpa-pairwise TKIP
        wpa-group TKIP
        wpa-psk "mySecretPSK"


```

So I reckon wpa_supplicant is starting without a config, and then ifconfig uses wpa_cli or something to pass the configuration into it. 

Still, it doesn't work for my ipw3945. I tried network-manager / network-manager-gnome but that didn't work either. Although it could see the wireless network, it couldn't connect.

I'd much rather type the config into a textfile than muck abut with GUIs, just so long as there were clear reliable instructions on what to type.

---

### Post by domib on 2006-09-03
Update: it works! Last night, it didn't work. This morning it works. All I've done this morning is read man pages and play with wpa_cli. I haven't actually changed anything. And yet it works.

Edit: what i did to make it work is bounce the interface:

```

sudo ifdown eth1
sudo ifup eth1

```

So pleased am I that WPA is working, i'm not too bothered that i have to bounce the interface to get it up. I think it has something to do with the order in which wpa_supplicant and ifconfig are run.

---

### Post by Zed on 2006-09-05
Based on advice [here](http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA) and [here](http://ubuntuforums.org/showthread.php?t=31418) I finally got it working, using the latest wpa_supplicant and ndiswrapper, built from source. The Dapper wpa_supplicant package is configured to install such that it's started automatically; since I'm not using that, I depend on the pre-up and post-down commands in the latter link, above.

---

