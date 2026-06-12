---
title: "Wireless card works, just don't know how to set up a connection"
date: 2006-09-18
forum: Networking &amp; Wireless
---

### Post by cobbweb on 2006-09-18
Hi, 
  I am usinga Net Gear Router and know that my Internet connection should work for my wireless card on my ubuntu machine, I just am having a problem getting connected to it. I used this same wireless card to connect to the internet on my Linux Desktop so I know that its not a driver issue, just a configuration thing. The way I have it set up is my SSID is not being shown but there is no encryption. (I figure if they can find my SSID they woun't have a problem getting past my encryption anyway). I'm a little confused on where to start, it has been a while since I last set up a wireless network on a Linux machine. Coun't anyone point me in the right direction on how im suppose to set somthing like this up? 
 
 Thanks a bunch, 
     Cobbweb

---

### Post by sp0nge on 2006-09-18
Try System>Administration>Networki

Is the wireless card there?

---

### Post by cobbweb on 2006-09-18
ya the wireless card is there....

---

### Post by sp0nge on 2006-09-18
Select that then click Properties.

Enter your ESSID

Key Type: HEX

Config:DHCP

click OK
 
Then de-activate eth0 and activate wlan0

---

### Post by cobbweb on 2006-09-18
for some reason my wireless card shows up as eth3? Is that correct? ....

---

### Post by sp0nge on 2006-09-18
never seen it show up that way, but try it and see what happens

---

### Post by ximok on 2006-09-18
Network devices can show up a number of different ways.  wlanX will always be a wireless networking device

ethX will always be an ethernet based networking device (This can include wireless devices)

pppX will always be a point-to-point connection (Such as a serial connection via dial-up modem)

The list goes on.  But, in a nutshell, all eth3 means is that you have an eth0, eth1, eth2, and eth3.  These can be multiple networking cards, ieee1394 devices (*i think*), and potentially virtual devices.

---

### Post by karamba_kid on 2006-09-18
> **cobbweb said:**
> (I figure if they can find my SSID they woun't have a problem getting past my encryption anyway).

Did I read that correctly?  Hidding your SSID offers you absolutely no security what-so-ever.  You broadcast your SSID in the clear in each packet you send and picking that out of the air is elementary. When your using wifi your broadcasting all your packets out into freespace where they continue on out into the universe forever.  Adding in a feature like WPA-PSK (the easiest and most practical for home users) will make these packets just look like noise and nobody will be able to decipher it unless they have the key.  WPA/TKIP with a long and random passphrase is currently believed to be secure, so until someone develops a quantum computer nobody will be able to get past your encryption.  Just don't use the weak WEP encryption, because  that implementation is worthless, but setting up wpa-psk isn't.  I would highly suggest using it.  I use the wpasupplicant package which you can apt-get. It's not too difficult just PM me if you need some help getting it setup.  Also it won't only protect you from would be evesdroppers but it will also help prevent somebody from logging into your network to scan your internal network, launch man-in-the middle attacks, or leech your internet for illicit uses.

---

### Post by wieman01 on 2006-09-19
> **karamba_kid said:**
> Did I read that correctly?  Hidding your SSID offers you absolutely no security what-so-ever.  You broadcast your SSID in the clear in each packet you send and picking that out of the air is elementary. When your using wifi your broadcasting all your packets out into freespace where they continue on out into the universe forever.  Adding in a feature like WPA-PSK (the easiest and most practical for home users) will make these packets just look like noise and nobody will be able to decipher it unless they have the key.  WPA/TKIP with a long and random passphrase is currently believed to be secure, so until someone develops a quantum computer nobody will be able to get past your encryption.  Just don't use the weak WEP encryption, because  that implementation is worthless, but setting up wpa-psk isn't.  I would highly suggest using it.  I use the wpasupplicant package which you can apt-get. It's not too difficult just PM me if you need some help getting it setup.  Also it won't only protect you from would be evesdroppers but it will also help prevent somebody from logging into your network to scan your internal network, launch man-in-the middle attacks, or leech your internet for illicit uses.
Let me correct that statement please. WPA-TKIP is NOT considered secure. Don't want to hijack this thread... But I had to say that. WPA2 with AES is the most secure method you can pick. WPA with simple TKIP is WEP based and hence insecure. But you are right in that it is a better choice than WEP, however, not the best one.

---

### Post by clrvynt on 2006-09-19
Hi,

I installed Ubunto 6.05 and in the Network Manager, I see ath0 (my integrated network card) and from the drop down I see the list of available networks. 

I have WEP security and selected my network. I tried entering the HEX values of the key (128 bit although there's no option to selection encryption level) and ascii format. Neither works. It does not connect.

However, if I remove WEP and keep it an open network, it works fine.

This happens with the integrated Atheros card and Netgear W11 card. 

Any help is appreciated.

---

### Post by happy-and-lost on 2006-09-19
PEOPLE!

```
sudo apt-get install wifi-radar
```

It's as easy as that!

---

### Post by clrvynt on 2006-09-19
I guess I need to get the package?

Here's the message I got:

Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package wifi-radar

---

### Post by karamba_kid on 2006-09-19
> **wieman01 said:**
> Let me correct that statement please. WPA-TKIP is NOT considered secure. Don't want to hijack this thread... But I had to say that. WPA2 with AES is the most secure method you can pick. WPA with simple TKIP is WEP based and hence insecure. But you are right in that it is a better choice than WEP, however, not the best one.

Not to steal the thread or anything, but WPA with TKIP using the rc4 cipher is considered secure as long as you use a large and random passphrase.  If you use a dictionary word for your key... of course it can be cracked. TKIP fixed the underlying problems with WEP.  The problem with WEP wasn't a weakness in the RC4 cipher, it was a weakness in how it was implemented, WPA/TKIP fixed this problem.

---

### Post by wieman01 on 2006-09-19
> **karamba_kid said:**
> Not to steal the thread or anything, but WPA with TKIP using the rc4 cipher is considered secure as long as you use a large and random passphrase.  If you use a dictionary word for your key... of course it can be cracked. TKIP fixed the underlying problems with WEP.  The problem with WEP wasn't a weakness in the RC4 cipher, it was a weakness in how it was implemented, WPA/TKIP fixed this problem.
I don't want to argue nor hijack this thread (apologies), but read this:

[http://en.wikipedia.org/wiki/IEEE_802.11i]("http://en.wikipedia.org/wiki/IEEE_802.11i")

The reason why they established WPA2 is the fact that WPA(1) is WEP based and has similiar shortcomings. So by no means should enterprises or government institutions use WPA for instance.

But you're right, an average user would not be able to crack it or break into a WPA(1) secured network, but professionals can, even if you choose a random key. 

WPA2 with EAP is the most secure choice you can make.

---

