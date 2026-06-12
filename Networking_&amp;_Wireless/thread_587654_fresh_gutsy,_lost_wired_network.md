---
title: "fresh gutsy, lost wired network"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by pneaveill on 2007-10-22
I hope I am not re-opening a closed can of worms, but think this is just different enough to start a new thread. If I am wrong, I am willing to be corrected.

The problem: after the update from feisty killed my dual monitors, gutsy lost access to the network card. I did first update and rebooted (assuming it did some sort of kernel upgrade), which lost access to network card.

my machine is an athlon 1.4GHZ w/ 768 mb SDRAM
ubuntu 7.10, running kernel 2.6.22-14-generic #1 Sun Oct 24 23:05:12 GMT i686

lspci shows the network card as 00:0d:0 Ethernet controller: Realtek ....
Network manager shows zilch for network cards.

[edit] I rebooted that computer just to see what would happen. I saw it flash the network switch upon bootup and it even tells me I have 60 updates I can get. However, when I rerun the network, it is not there. Instead, it gives me a ghosted ppp modem for whatever reason.

Also ran ifconfig, which gives nothing for the eth0, but does give the lo setting [/edit]

Appreciate the help.

---

### Post by Blackcomb on 2007-10-23
My computer with Realtek WiFi also doesn't work. The other interface (ethernet) works fine and the wifi (intel) and ethernet interface on my laptop are also ok (with Gutsy)

---

### Post by pneaveill on 2007-10-23
As that computer is also dual booted with w2k (for God only knows what reason still) I tried a couple of experiments with that computer. I wiped the drive and reinstalled feisty and it still refused to see the network card.  Somewhere in the back of my mind I remembered an offline friend of mine say that in the early days of linux that he had a similar problem. 

[quote="Richard"]
(1) Check and double-check that everything is as close as you know it can be,
(2) **[COLOR=Blue]SHUTDOWN computer completely[/COLOR]**
(3) then trace cables down. Unplug and replug all network connections [COLOR=Blue]completely and carefully[/COLOR]
(4) reboot and recheck 
[/quote]

=================

my wired system works fine on feisty again, now to upgrade to gutsy again 

Thanks Richard

---

