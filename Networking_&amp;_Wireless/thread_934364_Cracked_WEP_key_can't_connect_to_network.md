---
title: "Cracked WEP key: can't connect to network"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by Alm4riC on 2008-09-30
Hello,

I'm trying to crack my WEP key, which is done: 74:B5:71:F1:C9
Now I want to log in with this WEP key by paste it in NetworkManager (without ":"). But, nothing happens. I've searched Google and this forum, but can't get any solution which can fix my problem. I used the ipwraw (wifi0) driver for injection in airodump. For surfing the web I use the IWL3945 (wlan0).

Anyway, is there something configured in the router what blocks me out?

Things I've done (also tried with wlan0):
iwconfig wifi0
iwconfig wifi0 mode managed key 74:B5:71:F1:C9
ifconfig wifi0 hw ether: 00:11:22:33:44:55

This is the piont where it is going wrong... But is it true if I say: I enter the found WEP key in Ubuntu's NetworkManager / Windows and it has to connect automatically?

I'm out of suggestions...

---

### Post by pytheas22 on 2008-09-30
I'm not sure how much I believe that the router you attacked is your own (since you don't seem to know which security settings are on it), but anyway...

The router could be filtering MAC addresses, in which case you would need to spoof your MAC to match that of an authenticated client.

There could also simply be driver issues on Ubuntu's end, especially if you hacked up your iwl driver in order to get it to support injection.  Make sure that you're really using iwl3945 when you're trying to connect, not ipwraw, and that iwl3945 works.

Also make sure that you're using the correct authentication method for the router.  When you enter your WEP key in Network Manager there's a field where you specify whether to use open authentication, PSK, etc.

You should try connecting to another wireless network somewhere just to verify that your system can successfully connect, or try connecting in Windows.  If you can't connect either in Windows or Ubuntu but you're sure you have the right WEP key, then the router is probably filtering MAC addresses.

---

