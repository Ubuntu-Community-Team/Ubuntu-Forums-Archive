---
title: "Cannot Connect to Wireless Router, dhclient to blame?"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by Marsol0x on 2006-09-02
I have a Belkin 802.11g wireless network card, and I have followed instuctions posted here on how to get it to work, and it has worked for many months afterwards, with my old router. After that one broke, for whatever reason, I went out and bought (well, I traded for it with my Uncle, he bought a new one to complete the trade) a Belkin G wireless router. And my network card and the router communicated just fine for a couple of weeks, now, my network card will not connect to the router and I don't know why.

Something must have changed, but I don't know what.

I'm using Kubuntu, and I have not updated anything that has to do with the internet. I'm using the Wireless Assistant that comes with Kubuntu and it has worked for me just fine.

I do not have the logs with me, since I am not at home, therefore I am able to get online and ask, but what seems to happen is that the dhclient seems to skip over certain important information.

Here is basically what happens:
[LIST]
[*]My network card looks for the router
[*]My network card finds the router
[*]The router offers something (DHCPOFFER)
[*]The network card requests something (DHCPREQUEST)
[*]The router sends a pack (DHCPPACK)
[*]My network keeps looking for something, checking through intervals before giving up.
[/LIST]

Anyone know what is going on?

---

