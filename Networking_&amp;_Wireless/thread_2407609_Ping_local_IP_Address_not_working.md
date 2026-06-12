---
title: "Ping local IP Address not working"
date: 2018-12-06
forum: Networking &amp; Wireless
---

### Post by qwin2 on 2018-12-06
Hi all, newby that can't get up and running.

_Background_
I have a BT smart hub6 Router as default gateway.

An Odroid C2 SBC connected by Ethernet cable with a minimal Ubuntu (18.04) image installed, so no GUI. This unit is earmarked for use as headless music server, so it also has MPD installed and running from boot up.

My controlling device for MPD will be, for now, a Windows10 laptop connected by wifi.

[U]Problem
[/U]I can ping the SBC IP Address from the laptop and get a report, but not particularly fast turn round averaging 9 to 29ms.
But if I ping the laptop IP address from the SBC, it sends, but does not report and just hangs until it times out.
If I ping the router from the SBC it gets stuck in a loop and keeps sending, approx once a second, I killed it after 330 sends with one line reports.

The IP Address's for connected devices at the router match those reported for the Laptop and SBC. I have a working internet connection from Laptop and SBC.

I have looked at some of the search results here, but non match this exact problem and similar threads ask for locations and commands not used on my recent version of Ubuntu, eg ifconfig.

Anyone know what I should check ?

---

### Post by The Cog on 2018-12-06
> I can ping the SBC IP Address from the laptop and get a report, but not particularly fast turn round averaging 9 to 29ms.
Sounds reasonable for a low powered SBC.
> But if I ping the laptop IP address from the SBC, it sends, but does not report and just hangs until it times out.
In Ubuntu (any Linux I think), ping does not keep printing timeout messages for every ping that fails, it only prints when it gets a response. So trying to ping something that doesn't answer simply doesn't print anything. Are you sure your laptop firewall isn't blocking the ping requests?
> If I ping the router from the SBC it gets stuck in a loop and keeps sending, approx once a second, I killed it after 330 sends with one line reports.
Unlike the Windows ping, the Linux ping keeps on indefinitely until you stop it with Ctrl-C unless you use -c (e.g. -c 3) to tell it how many to do before stopping.

You can use the command **ip address** to print your ip address, and **ip neigh** to check that your Ubuntu has found the router's MAC address, and **ip ro** to see your routing table.

---

### Post by qwin2 on 2018-12-06
@The Cog - Thanks, all that was very relevant. Windows Defender was blocking the ping.

The info that Ubuntu sends continuous until stopped if not told how many packets to send, makes sense of what was happening.

I think all is good.

---

