---
title: "How to configure ADSL on Ubuntu?"
date: 2005-08-08
forum: Networking &amp; Wireless
---

### Post by Tux on 2005-08-08
I just installed Ubuntu. The system works more or less, except for Internet.
Obviously: I'll have to log in through my ISP. I did not encounter a configuration step for this during installation. I use an ADSL "modem" as gateway, which is accessible on the local network.
Where in Ubuntu do I configure Internet access? Presumably I'll have to use PPTP (that's what I use with my iMac on the same ADSL gateway).
On my previous Debian install I used pppd, but that is a pain to configure.

---

### Post by manicka on 2005-08-08
System-->Administration-->Networking

---

### Post by Tux on 2005-08-08
[QUOTE=manicka]System-->Administration-->Networking[/QUOTE]

Ah, well.  Those menu items do not work on my system.  When I select it I have to enter a password; whether I use the password of the login account or root, I always get the error box:
    "Failed to run network-admin: Child terminated with 1 status."
I can log in and from another menu I can open a terminal and su to root, so I know the passwords are correct and the login account has privileges.

Any idea what is wrong?

TIA,

---

### Post by Sianis on 2005-08-08
[QUOTE=Tux]Ah, well.  Those menu items do not work on my system.  When I select it I have to enter a password; whether I use the password of the login account or root, I always get the error box:
    "Failed to run network-admin: Child terminated with 1 status."
I can log in and from another menu I can open a terminal and su to root, so I know the passwords are correct and the login account has privileges.

Any idea what is wrong?

TIA,[/QUOTE]
 Try it: sudo pppoeconf - i use it for my ADSL. After setup it will starting your Internet.

Maybe you give this : Failed to run network-admin: Child terminated with 1 status. cause the prestart death and stay into the processlist. After restart maybe fixed this probleme.

---

### Post by Tux on 2005-08-08
[QUOTE=Tux]Ah, well.  Those menu items do not work on my system.  When I select it I have to enter a password; whether I use the password of the login account or root, I always get the error box:
    "Failed to run network-admin: Child terminated with 1 status."
[/QUOTE]

O wait.  Apparently my login account was not added to sudoers during install.  I fixed that by hand.
However, the network-admin tool only allows to:
1) configure eth0, which is fine (for my LAN).
2) configure ppp0 to call out on a serial line through a serial port.
However, I have ADSL which works with a dumb gateway/router that has my LAN ethernet on one side and the telephone line on the other.  I have to prod my ISP through that channel.

In a previous install I used pppd for that.  It apparently is present on Ubuntu, but is a pain to configure.  Also PPTP is the protocol of choice nowadays I am told.  So is there a standard tool on Ubunto to achieve this?

    Thanx,

---

### Post by varunus on 2005-08-08
As the post 2 above says, try pppoeconf.  It configures PPTP for most DSL connections.  Type "sudo pppoeconf" in a terminal.

---

### Post by Tux on 2005-08-08
[QUOTE=Sianis]Try it: sudo pppoeconf - i use it for my ADSL. After setup it will starting your Internet.
[/QUOTE]

Thanx for your suggestion.  I ran pppoeconf, but it did not recognise the "Access Concentrator".  I have the impression that PPPoE is not supported by the "modem" (an Alcatel SpeedTouch).  In fact, when I access its webinterface, only PPTP routing is configurable; PPP and CIP "are not available for this product".

---

### Post by Sianis on 2005-08-08
[QUOTE=Tux]O wait.  Apparently my login account was not added to sudoers during install.  I fixed that by hand.
However, the network-admin tool only allows to:
1) configure eth0, which is fine (for my LAN).
2) configure ppp0 to call out on a serial line through a serial port.
However, I have ADSL which works with a dumb gateway/router that has my LAN ethernet on one side and the telephone line on the other.  I have to prod my ISP through that channel.

In a previous install I used pppd for that.  It apparently is present on Ubuntu, but is a pain to configure.  Also PPTP is the protocol of choice nowadays I am told.  So is there a standard tool on Ubunto to achieve this?

    Thanx,[/QUOTE]
 So. Your first question is "Where in Ubuntu do I configure Internet access?". 

ASK: $ sudo pppoeconf . Try it, you can reach Internet trought ADSL modem with this...

---

### Post by Sianis on 2005-08-08
[QUOTE=Tux]Thanx for your suggestion.  I ran pppoeconf, but it did not recognise the "Access Concentrator".  I have the impression that PPPoE is not supported by the "modem" (an Alcatel SpeedTouch).  In fact, when I access its webinterface, only PPTP routing is configurable; PPP and CIP "are not available for this product".[/QUOTE]
 Try it: 

[http://ubuntuguide.org/#configuredialupconnections](http://ubuntuguide.org/#configuredialupconnections)

or 

[http://ubuntuguide.org/#configuredialupconnections](http://ubuntuguide.org/#configuredialupconnections)

---

