---
title: "Random failures to connect"
date: 2008-09-07
forum: Networking &amp; Wireless
---

### Post by jamespetts on 2008-09-07
I am having some very bizarre problems with my home network. I have had problems for some time, but shall not elaborate unless requested, since that would make this post extremely long.

The issue at present, however, is this: of four computers on the home network, Study, Bedroom, Kitchen and Parlour, Parlour can connect to Bedroom, but not to Study or Kitchen; Study can connect to Bedroom, but not to Kitchen or Parlour; bedroom can connect to Parlour and Study, but not to Kitchen; and Kitchen can connect to Bedroom, but not Parlour or Study. (I test by pinging; all the computers have firewalls, but none block pings from computers on the local network). This behaviour is not always consistent. 

I have just upgraded Parlour from Windows XP Home to Linux (Ubuntu Hardy), which I hoped would solve the problem, but it has not. Kitchen and Bedroom are also Ubuntu Hardy; Study is Windows XP Pro. 

The network is configured using a Westell 4-port router. My ISP gives me 8 IP addresses, so each computer is assigned its own, static, internet IP address (which, taking into account the broadcast address and router's own address, leaves one spare). 

I originally thought that the problem was Linux related, since I first saw it when I upgraded to Gusty from Feisty, or alternatively a problem with the Windows XP Home machine (it was an old install dating back to 2002 with other problems), but this is doubtful now that the problem is still present on upgrading.

Could it be an issue with my router? Any help would be very, very much appreciated, as this is really causing me serious problems.

---

### Post by jamespetts on 2008-09-28
I discovered ultimately that the problem was caused by firewalls. The Windows machine's firewall (Zone Alarm Pro) had lost its original configuration specifying my network's IP range as the trusted zone when I had to reinstall it recently.

As for the Linux machines, I removed Firestarter and switched to ufw, where I was able more precisely to set an IP range within which all incoming and outgoing traffic would be allowed with no filtering (although the visual feedback for IP ranges in ufw is wrong). This effectively solved the problem, and I can now connect from anywhere to anywhere.

---

