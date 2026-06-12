---
title: "Benefit to keeping &quot;dnsmasq&quot; enabled on Desktop?"
date: 2017-02-06
forum: Networking &amp; Wireless
---

### Post by PrinceVince on 2017-02-06
I'm currently tinkering with my local network to learn about it. I stumbled upon the IP 127.0.**1**.1 and learned that name resolution, instead of directly calling DNS servers, appears to query a process called **dnsmasq** first. Looking into that, I found an article that reads:
[QUOTE="Article on how Ubuntu 12+ does things"]This dnsmasq server **isn’t a caching server** for security reason to avoid risks related to local cache poisoning and users eavesdropping on other’s DNS queries on a multi-user system.[/QUOTE]
Does this mean that there's no performance benefit to keeping **dnsmasq** enabled, or am I misunderstanding this? The feature can disabled by uncommenting *"dns=dsnmasq"* in */etc/NetworkManager.conf*. I have no server behind my router and would simply like to have effective name lookup on my Desktop while surfing.

Any guidance welcome, thanks!

---

### Post by gdesilva on 2017-02-06
This might be useful.

[URL="https://help.ubuntu.com/community/Dnsmasq"]https://help.ubuntu.com/community/Dnsmasq
EDIT:

Also worth checking out the following links;
[/URL][https://gist.github.com/magnetikonline/6236150](https://gist.github.com/magnetikonline/6236150)
[http://askubuntu.com/questions/117899/configure-networkmanagers-dnsmasq-to-use-etc-hosts/130416#130416](http://askubuntu.com/questions/117899/configure-networkmanagers-dnsmasq-to-use-etc-hosts/130416#130416)

---

### Post by PrinceVince on 2017-02-07
I had read the first link and various other discussions, but the github and askubuntu posts I hadn't encountered. I see the sense in keeping the default setup now, thanks.

---

