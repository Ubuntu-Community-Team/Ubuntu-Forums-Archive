---
title: "captive portals"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by polemarchus on 2007-05-03
I have recently created a captive portal for my family to use at home. We live in a very residentual area and have previously had lots of people pinching our connection.

So now I have set up a captive portal system, very similar to the one you might get in Starbucks.

Now what I want to do is check the security. How can I try to break my own defences?

---

### Post by netztier on 2007-05-03
> **polemarchus said:**
> I have recently created a captive portal for my family to use at home. We live in a very residentual area and have previously had lots of people pinching our connection.

So now I have set up a captive portal system, very similar to the one you might get in Starbucks.

Now what I want to do is check the security. How can I try to break my own defences?

Ehm.. wouldn't using some decent WPA/WPA2 setup with a good, long Pre-Shared-Key have had an even better result? If you don't want one shared key for everyone, think along 802.11i with Radius (which is essentially WPA2) and individual usernames/passwords for each user and a rigorous password change policy. 

**JUST [COLOR="Red"]DON'T[/COLOR] RUN YOUR WIRELESS LAN UNECRYPTED!** [SIZE="1"](sorry for yelling, just wanted to make this point strong!)[/SIZE]

The fun thing with an unencrypted WLAN is this (regardless if there is a captive portal or not!):

Your neighbor can merrily sit at his pool and eavesdrop on your WLAN without having to join it nor even obtain an IP address from your router's DHCP function. Just sit passively there and listen. :twisted: Unless you catch him while doing it, you'll never be able to find him, since his "listen only" interface is passive and does not talk to any other device.

It's quite fun to see usernames and passwords of POP3 mail accounts float by in cleartext :twisted:, imagine the possibilities... and thinking that a lot of people use the same passwort almost everywhere.. oh well, sometimes it's just too easy!

Electronic Banking is mostly secure nowadays - but with some tricks that are a bit more cunning and that require your neighbor to join the WLAN, he can pose as a Man-In-The-Middle and have the connection between you laptop and your router flow through his machine. Not what you want.

In short: a captive portal controls the access to the internet from your local (wireless) network. But it won't protect your wireless network from eavesdropping. Neither do MAC access lists - it's easy to fake a MAC address on a WLAN NIC, once you know one. And you can find one - right - by eavesdropping.

Another way to become immune against eavesdropping is more difficult to achieve: 
[LIST]
[*] Always use encrypted connections when using an unecrypted Wireless LAN: 
[*] VPN where available (e.g. when connecting to your office), 
[*] the secure variants of POP3, SMTP and IRC, 
[*] HTTPS wherever you have to enter a username/password into a web form, etc.
[/LIST]

The problem with this is that your service provider has to offer these secure protocols, and not all of them do.


Best regards

Marc

---

