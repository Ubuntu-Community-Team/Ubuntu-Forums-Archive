---
title: "Intel Pro 3945 ABG"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by pashby on 2006-09-13
Hi there
I'm having problems using the network manager.
The effect is that nwm will not work when I change between any of my 3 work wireless networks and/or my home network.

I can however, manually change networks but this takes time and is a pain.

The network card is NOT recognised by the system but I can still access the network if I change the settings manually.

I get this from iwconfig

peter@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"wireless"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:B5:B7:A2:B2
          Bit Rate:2 Mb/s   Tx-Power:15 dBm
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/100  Signal level=-42 dBm  Noise level=-43 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

and I can connect.

The device manager does not recognise the card calling the wlan card "unknown"

My computer is an ASUS A6J and runs both Ubuntu and XPpro on a dualboot Hard Drive. XPPro has no problems recognising both the WLAN and the Wired lan cards. Ubuntu finds neither but connects to both.

Can someone point me in the right direction please

Peter

---

### Post by Lightarrow on 2006-09-13
Hi, i am not sure i can help since i don't have the same wireless card as you. All i know is that evrytime i use network-manager-gnome I can only connect to WPA encrypted networks. It will not le me connect to WEP or OPEN wireless networks. I did not try wpa_supplicant yet but I suggest you to disable WPA at home (if that is what you have) and just work with the "normal" network manager in

System-> Administration-> Networking

and select your wireless networks from there.

Hope this helps

Edit:I suggest removing the network-manager-gnome if you decide not to use it.

---

### Post by pashby on 2006-09-14
Thanks for the advice.

My real question is why doesn't Ubuntu recognise the cards but is still able to use them?

Is there a way to make Ubuntu recognise the cards? I'm sure if the cards are found nwm will be able to use them.

Peter

---

