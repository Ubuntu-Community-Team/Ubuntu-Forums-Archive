---
title: "Using airodump-ng on Ubuntu"
date: 2007-08-11
forum: Networking &amp; Wireless
---

### Post by Satal Keto on 2007-08-11
I have recently installed the aircrack-ng suite on my laptop which runs Ubuntu (Feisty) when I try and run airodump-ng it will run for about a minute then it will stop.
I have googled this problem and I have come up with the following from the aircrack website
> Airodump-ng stops capturing data after a short period of time

The most common cause is that a connection manager is running on your system and takes the card out of monitor mode. This is a very common problem especially with the Ubuntu distribution. Be sure to stop all connection managers prior to using the aircrack-ng suite. 

I am using the Network Manager Applet 0.6.4 which is automatically on Ubuntu.
I have two questions;
1) How do I remove the Network Manager Applet? is it done through the "Synaptic Package Manager"?
2) How do I configure my Wireless to run without having the Network Manager Applet running?

Thanks for any help in advance :)

---

### Post by michelob22 on 2008-05-20
I have the same problem. I'm running Hardy though. I have MadWifi drivers and an Atheros wireless card (AR5212), and installed the latest version on aircrack, but when I try to capture the networks around in monitor mode, it doesn't capture anything.

---

### Post by wire604 on 2008-06-15
> **michelob22 said:**
> I have the same problem. I'm running Hardy though. I have MadWifi drivers and an Atheros wireless card (AR5212), and installed the latest version on aircrack, but when I try to capture the networks around in monitor mode, it doesn't capture anything.

Hey there Im having the exact same issue, worst is when i was running ubuntu 7.10 lspci returned the card as atheros 5006 something and was working perfectly

also if i use backtrack it works !

ill let you know if I find the resolution, please do the same if you get it !

thanks

PS:is your machine a macbook pro?

---

### Post by ii bk ll on 2008-07-10
have you destroyed the manged mode connection?

type in "iwconfig" and if there are any connections other then your monitor mode then it wont let you collect any packets. 

hope thats what your looking for:confused:

---

### Post by ottojoj on 2008-07-20
i have a problem to it all works on backtrack i installed the patched for injection madwifi-ng-r2756-20071018 i can sudo arimon stop ath0 and start wifi0 
which puts ath0 into monitor mode but when i try sudo airodump-ng it goes up but it doesnt pick up any networks ive done it with bt3 beta on my thumbdrive but it doesnt do any thing and when i do sudo kismet -c madwifi_b,wifi0,asdf ath0 the same thing happens no network and that also works in backtrack

please help

---

