---
title: "PPTP VPN via USB Modem"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by surfdoc on 2007-10-22
To all network experts!

I'm trying to VPN to a windows PPTP server. My machine is running kubuntu feisty and connects to the internet with a usb modem.
I've tried the various gui howtos with the following results:

knetworkmanager - allows me to configure vpn but when connecting i get the following message in /var/log/syslog

"no currently active network device, won't activate VPN. "

I suspect that it may be looking for eth0 to connect through - but my internet connection is ppp0. I can't see any option for selecting the device to connect through. Is there any way I could connect eth0 to ppp0, to trick it into using that connection? There's lots of sites around discussing problems with wireless connections - is this related?


kvpnc - allows me to configure vpn but reports that pppd does not support MPPE

I've googled this and couldn't find anything except one person suggesting that it is a bug in kvpnc


nm-applet - doesn't even give the option to configure a vpn (im running kde so i'm not supprised)


pptpconfig - apparently depreciated in feisty?


It would be nice to get one of the gui working, but it appears that they're all broken. I've also tried to find instructions on how to configure a vpn through the console, but i don't seem to be able to find anything.

---

### Post by surfdoc on 2007-10-22
Ok thanks to: 

[http://gentoo-wiki.com/HOWTO_PPTP_VPN_client_(Microsoft-compatible_with_mppe](http://gentoo-wiki.com/HOWTO_PPTP_VPN_client_(Microsoft-compatible_with_mppe))

i seem to be getting a bit further. It seems that kvpnc might have been right. The output from pon includes the line "MPPE required but not available".

Looking at:

[http://pptpclient.sourceforge.net/howto-diagnosis.phtml](http://pptpclient.sourceforge.net/howto-diagnosis.phtml)

it appears that there may be a compatibility problem with pppd. However, i'm unsure how to proceed. My kernel (2.6.20-15-generic) has MPPE support. Do i need to do something to pppd?

Any ideas?

---

### Post by surfdoc on 2007-10-22
Ok - a little fiddling with the config files and the firewall, and I seem to be connected!!! I think i had mppe and mppe-128 enabled. Removing the mppe one seemed to work - i think?

Now what? I'm trying to mount a file share - however mount times out on me. Time for bed i think!

---

