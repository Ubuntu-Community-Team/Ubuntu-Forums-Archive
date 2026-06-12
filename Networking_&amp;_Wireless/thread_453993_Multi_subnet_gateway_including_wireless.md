---
title: "Multi subnet gateway including wireless"
date: 2007-05-25
forum: Networking &amp; Wireless
---

### Post by Spudz0r on 2007-05-25
I hope i didnt scare everyone off with the title, but i am after a little help with setting up a 3 way gateway server.

in other words..
eth0 - WAN
eth1 - LAN (subnet 1)
wlan0 - LAN (subnet 2)

firstly, what wireless cards are recommended, based on ease of installation, running @ full 54mbps, and support WPA, preferably WPA2-PSK.
i only need B/G support no A or N for the time being. or even 108G. too much hassle with compatability.

i need SN1 to have full access to SN2 and vica verca.

i can set seperate firewall / port forwarding to and from each SN to the WAN. this is not an issue. in fact it also gives me a little more control over the wireless.

ftp server will need access to all 3 subnets.

also want any samba shares to be available to both subnets.

Will be using Ubuntu 7.04 for the time being. - will be installing LAMP also, along with dhcpd and dnsmasq. maybe squid and sendmail also.
planning to have webmin/webconfig installed for easy management and reporting.

would also like to set it so it defaults to console only (not sure if ubuntu uses same principals as redhat.. ie. init 3)

system hardware is still in the planning stage, but will be at least celeron500 with 512mb ram and 20gb hdd.
possible dual p3 733 with 1gb ram. but this is not preferable as its too noisy =P


anybody able to post links to howtos? or post me some suggestions? thanks.

---

### Post by Spudz0r on 2007-05-28
if its easy to find help, i could always just use another wired nice plugged directly into an AP to cut the wireless issues out of the equasion.


anybody out there able to point me in a direction to work this out?
i have spent a number of hours trawling through the ubuntu forums, but havent really found anything at all on setting up a multi subnet gateway.

so yer.. any help is good.

---

### Post by Spudz0r on 2007-05-31
bumpness.


has anybody got anything that could point me in the right direction?

---

### Post by Spudz0r on 2007-06-26
anybody?

---

### Post by Austin_KW on 2007-06-26
Are you sure you want different subnets. I am no expert but for filesharing and the like wouldn't it be easier just to bridge eth0 and wlan0 on the same subnet.

---

### Post by 65 mustang on 2007-06-26
The easiset way may be to just get 2 ethernet cards and a 802.11g router that you can configure to be a gateway.

Then setup [http://www.shorewall.net/](http://www.shorewall.net/) in the 2 devices configuration they have there.

Getting wireless cards in AP mode is kinda challenging, but i did get my atheros one to work with the madwifi driver.  I suggested the AP because its about the same cost and it eliminates a step.

---

### Post by Spudz0r on 2007-06-27
thanks for the replies.


multi subnets are fine for filesharing. - as long as you set up the routing correctly on the gateway.
in some cases you need to add the additional subnet pc's into your LMHOSTS (on windows machines) but it isnt always necessary (from what i can gather).

as for the wireless. i had decided some time ago to just use an AP connected to the third NIC as after sifting through many threads on the issue it seems its more difficult than what is really worthwhile. - you also get the same effect from the AP.

---

