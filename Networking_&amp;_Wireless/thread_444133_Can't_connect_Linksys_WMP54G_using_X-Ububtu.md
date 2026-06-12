---
title: "Can't connect Linksys WMP54G using X-Ububtu"
date: 2007-05-15
forum: Networking &amp; Wireless
---

### Post by rouppe on 2007-05-15
Hi. I am completely new to any sort of Linux. I have a very old machine (PIII 466 Mhz 320Mb RAM) and thought it would be worth a go installing X-Ubuntu 7.04 to see if it performed better than the Win98...

Got the operating system installed OK, and when I went into the Network Settings panel it had recognised my wireless card. However I have not been able to get it to connect to my wirekless network.

I enabled it, set the ssid, and tried all 4 combinations of Password type (ascii or hex) and value (the key I used to generate the hex keys and one of the actual 10 digit hex keys.

Nothing seems to work. I have tried switching the Connection Settings from Auto (DHCP) and Static IP an setting the values to the same as those that show up. I tried disabling encryption ont he router but then discovered that  there was no way of not specifying WEP encryption.

In addition, while trying things I have read on these forums, whenever I log on, I get a message box saying:
> Could not look up internet address for downstairs. This will prevent xfce from operating correctly. It may be possible to correct the problem by adding downstairs to the /etc/hosts file. I have named the machine "downstairs".

Can anyone tell me a) why I can't get the wireless card working? If the error message box can be fixed as well, that would be good. As a last resort, how do I un-install X-Ubuntu and release the partition that was made for me?

The card is a Linksys WMP54G using the RaLink RT2500 chipset.

Many thanks

Andrew

---

### Post by Ken_Lewis81 on 2007-05-16
Ah.  The Ralink chips in your card are at fault.  Ubuntu maintains a driver for it, but it's not compatible with the new NetworkManager tool.  The page for the [Ralink RT2500 on Ubuntu](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500) at [wiki.ubuntu.com](wiki.ubuntu.com) was a good help to me, because I use WPA encryption.

Hope that helps.
Take care.
Ken.

---

### Post by ugm6hr on 2007-05-16
I have no experience with the Ralink wireless cards, but I have recently installed Xubuntu7.04 (Feisty).  Xubuntu does not have Gnome NetworkManager installed as a default, and it sounds like rouppe is trying to manually configure via the standard Networking utility (Applications -> System -> Network).  

According to the wiki link given above (Ken_Lewis81), it should work as rouppe has tried it (albeit in Edgy) with WEP.  It might be worth trying the router without encryption (I think the way to connect without WEP is to leave the "key" blank) to see if it works.  At least that would give you somewhere to start from.

---

### Post by rouppe on 2007-05-16
> **Ken_Lewis81 said:**
> Ah.  The Ralink chips in your card are at fault.  Ubuntu maintains a driver for it, but it's not compatible with the new NetworkManager tool.  The page for the [Ralink RT2500 on Ubuntu](https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500) at [wiki.ubuntu.com](wiki.ubuntu.com) was a good help to me, because I use WPA encryption.

Hope that helps.
Take care.
Ken.

Thanks for that. I'll have a look at the links tonight. I am using the standard networking utility.

---

### Post by rouppe on 2007-05-16
> **ugm6hr said:**
> I have no experience with the Ralink wireless cards, but I have recently installed Xubuntu7.04 (Feisty).  Xubuntu does not have Gnome NetworkManager installed as a default, and it sounds like rouppe is trying to manually configure via the standard Networking utility (Applications -> System -> Network).  

According to the wiki link given above (Ken_Lewis81), it should work as rouppe has tried it (albeit in Edgy) with WEP.  It might be worth trying the router without encryption (I think the way to connect without WEP is to leave the "key" blank) to see if it works.  At least that would give you somewhere to start from.

I thought about trying it unencrypted but it didn't appear that there was a way to do that. Didn't think that leaving the key blank would be the way to do it. Will try tonight.

As an aside, when it comes time to encrypt, I get to specify a key type (ascii or hex) and the actual key. On the router I specify a "passphrase" (such as "WhatALovelyDay") and generate keys which are 10-digit hex strings such as "F0F0F0F0F0". I am assuming that I specify that the key is hex and put in "F0F0F0F0F0" as the key. Given that I have the option on the router to specify 128 bit encryption (instead of the 64-bit I currently specify) is this significant?

Thanks

Andrew

---

### Post by ugm6hr on 2007-05-18
A 128-bit Hex key will be longer than 10 Hex digits (I think it's 26 - someone confirm?).  Might be worth a try with a 128-bit key - Network config on Xubuntu doesn't give an option to specify the length of key (unlike Gnome Network Manager), so perhaps it only allows 128-bit (although that would be bizarre).

I did find these entries (see Monkey2 post):
[http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/345000954831](http://episteme.arstechnica.com/eve/forums/a/tpc/f/96509133/m/345000954831)
[https://launchpad.net/ubuntu/+source/network-manager/+bug/78037](https://launchpad.net/ubuntu/+source/network-manager/+bug/78037)

The first seems to suggest that Network Manager with Feisty works out of the box with this chipset, and the second (perhaps more reliable source) confirms what has been said here.  Nevertheless, perhaps it might be worth a go? (Applications -> System -> Add/Remove... ; search for "Network Manager" - network management framework (GNOME frontend) - and tick and apply).  It also has a suggestion for using ndiswrapper.

---

