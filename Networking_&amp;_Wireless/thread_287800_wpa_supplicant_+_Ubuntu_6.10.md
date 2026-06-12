---
title: "wpa_supplicant + Ubuntu 6.10"
date: 2006-10-29
forum: Networking &amp; Wireless
---

### Post by sionghua on 2006-10-29
I follow the instructions in 
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)
and
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA](http://ndiswrapper.sourceforge.net/mediawiki/index.php/WPA)
to setup my engenius EUB-862, I successfully detected all wireless networks when issuing
iwlist wlan0 scan

but after I issue
wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

I get the following error.

Using existing control interface directory.
ctrl_iface exists, but does not allow connections - assuming it was leftover from forced program termination
Could not unlink existing ctrl_iface socket '/sbin/wpa_supplicant/wlan0'
Failed to initialize control interface '/sbin/wpa_supplicant'.
You may have another wpa_supplicant process already running or the file was
left by an unclean termination of wpa_supplicant in which case you will need
to manually remove this file before starting wpa_supplicant again.

And I don't know what to do, anybody understands knows what to do?

---

### Post by sionghua on 2006-10-30
I found the mistake and corrected my /etc/wpa_supplicant.conf to

ctrl_interface=/var/run/wpa_supplicant

instead of 

ctrl_interface="path to wpa_supplicant" (I thought it refer to the binary, so stupidly changed the path to the binary of wpa_supplicant, it actually referring to a directory where wpa_supplicant can work in). 

Anyway I got it running and now I am connected using Engenius EUB-862 (Atheros ar5523 chipset, usb-based) connected on WPA using ndiswrapper. I'm happy that it works after I spent so much time on it. The above mentioned instructions really are very useful :) 

Now I need to find out how to configure it to run with Upstart so that I don't have to run it every time. (may be I should used sysvinit since its still supported).

---

### Post by sionghua on 2006-10-30
I got everything setup and running ok, except that it is not automated even though I included the wpa_supplicant command in /etc/network/interfaces so everytime I start my computer I need to run wpa_supplicant manually and then dhclient manually as well in order to access to internet. Any idea why automation is not working?

my interfaces file as follow:

> auto wlan0
iface wlan0 inet dhcp
wireless-mode Managed
wireless-essid bplus1
pre-up wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -Bw
post-down killall -q wpa_supplicant
By the way I notice that I need to completely shut down my computer before I login to ubuntu again to make sure the usb adapter refresh, if I simply restart it will not be detected.

---

### Post by Nobber on 2006-10-31
I'm not sure what's wrong. My setup is very similar to yours, but the only obvious difference is that I'm using the full paths to  wpa_supplicant and killall in /etc/network/interfaces.

---

### Post by l4tran on 2006-12-13
Hello, I have the exact same wireless adapter as you and I am trying to get it to work in DSL-N.  I downloaded the EUB-862 2.1 driver but haven't had any success.  I was wondering if it is possible for you to send me the INF drivers that you are using.  My email address is [email]l4tran@yahoo.com[/email].  Thanks.

---

