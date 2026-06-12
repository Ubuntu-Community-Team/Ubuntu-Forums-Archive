---
title: "No lease (and no connection to the internet), but everything working ok"
date: 2007-01-14
forum: Networking &amp; Wireless
---

### Post by cuniculus on 2007-01-14
hi there.

i am pretty new to linux and ubuntu, but i thought my question would make more sense in here than in the absolute beginner section.

and here is my problem i want to share with the community. (c;

i had a computer with an old suse 9.0 running on it. this suse really made a lot of troubles. so i decided to replace it by ubuntu 6.06.

just did it. basically the installation worked fine. my "only" problem so far is that i don't have any internet.

i have internet via a cable modem. it worked a few hours ago under suse. actually i should get the ip via dhcp, so not much to do, i thought.

here is my reports:
the **ifconfig **tells me the correct physical address of eth0, so the network card is there.

**sudo dhclient eth0** delivers "no dhcpoffers received. no working leases in persistent database - sleeping."

**lsmod **delivers the network card via_rhine and mii as used by via_rhine.

**mii-diag** resulted in "you have link beat, and everything is working OK."

i also reseted the modem, no result.

i assigned the physical address of the network card to my windows-laptop and connected the cable. i immediately got an ip-address and could go online. so it is also not a fault by the isp or something.

i am really getting frustrated now. i called friends who know a little more than me (not too hard i guess), i googled and i searched on this forum. i tried a few things i found here (like disabelling ipv6 on firefox) but i didn't come up with a solution.
i also tried to use an older live-cd (ubuntu 5.04) but had the same "errors" there.

so i am calling for a helping hand now. (*;

---

### Post by koenn on 2007-01-14
some ISP's perform a check on the MAC address of the network card that requests an IP address. I don't think that's the cause of the problem here cause that MAC seemed to have worked for the windows machine, but you cpoulmd try anyway. 
You can set
```
send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
```
in /etc/dhclient.conf

sometimes the following procedure also helps to clear the MAC address the cable modem has stored and get you a new IP address.
1- turn modem of (unplug power)
2- turn pc of
3- wait - 10 minutes or so (some people also suggest you use this time to pray, burn candles and /or incense, perform dances or other rituals, ... )
4- turn modem on - see it boot and wait till status is "ok" (startup complete, connected ...)
5- turn PC on

---

### Post by Floppyjoe on 2007-01-14
My internet connection is DSL through a modem. When i just use the modem in Windows I need special software supplied by my ISP to initiate a PPPoe connection. There are similar programs in Linux to set up a PPPoe connection. If you search Synaptic for PPPoe you will find a few entries for this. I'm not sure this will help.

---

### Post by cuniculus on 2007-01-17
well, the modem does not need special software. not "even" under windows and as i mentioned it worked before with suse 9.0 (which isn't the most uptodate version by far).

i was wondering if it could help, when i try to reinstall ubuntu BUT using a minimal-cd. so that i "force" ubuntu to connect to the internet in a very early stage - aleady while installing. could this possibly help or would this be just a waste of time?

another question relating to this issue: i have an old notebook with ubuntu 5.04 on it. how can i assign a specific mac-address to the network-card there? i would like to try if this notebook gets an ip since i know that it worked before.
so if the problem persists there i guess it's not directly ubuntu's fault.

although, i tried to run the live-cd on another computer yesterday. this computer is behind a router and uses a linksys wifi-card. i tried dapper and edgy. but the problem is similiar there. it recognises the card (as ra0), i can configure it with the settings for my wifi (ssid, wep key, etc.) but i do not get a lease.
also if i do "iwlist ra0 scan", it tells me that there is nothing to scan.
for me it seems like the problem is similiar to the one above or can there be a difference?

i am really wondering because i remember, when i set up ubunut 5.04 on my old ibm t21 i could connect it straight away to the net. no problems at all. thus i am kinda getting frustrated right now. ),=

---

