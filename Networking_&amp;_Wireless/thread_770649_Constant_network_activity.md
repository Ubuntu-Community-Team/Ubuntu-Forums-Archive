---
title: "Constant network activity"
date: 2008-04-27
forum: Networking &amp; Wireless
---

### Post by barboachtraner on 2008-04-27
I've noticed that my network monitor shows I'm constantly receiving packets at a rate of around 500 bytes to a few KB per second even when I don't have a web browser or any other applications open. It might always have showed activity like that, but I never really considered it before. I tried searching and found a few similar posts where some people suggested using Wireshark, which I haven't done yet. I did check the active connections in Firestarter and nothing showed up. Any idea what all these packets could be from?

---

### Post by Monicker on 2008-04-27
What else is on your network?  How many other devices?  It could be broadcasts from Windows machines, upnp from your router, or a number of other things.

---

### Post by barboachtraner on 2008-04-27
> **Monicker said:**
> What else is on your network?  How many other devices?  It could be broadcasts from Windows machines, upnp from your router, or a number of other things.

The only thing I have is this desktop connected to a cable modem...

---

### Post by Monicker on 2008-04-27
> **barboachtraner said:**
> The only thing I have is this desktop connected to a cable modem...

If you are connected directly to a cable modem, with no router in between to filter traffic, then you are most likely getting lots of probes from external ip addresses, possibly even traffic from other devices on your isp's network.

If so, I would take a good look at what services are accessible on your machine.  Script kiddies are constantly looking for machines which they can attempt to break into.


I would definitely run Wireshark for at least 10 to 15 minutes, to see exactly what type traffic is coming to your machine.

---

### Post by barboachtraner on 2008-04-27
I just started Wireshark for a short time and the vast majority of the captured traffic was like this.

> Cisco_6f:e0:01	Broadcast	ARP

---

### Post by Monicker on 2008-04-27
> **barboachtraner said:**
> I just started Wireshark for a short time and the vast majority of the captured traffic was like this.


That is probably coming from your isp.  Its still a goo idea to make sure you on't have any vulnerable service running, since your machine is connected directly to the cable modem.


You may want to read this: [Ubuntu Security]("http://ubuntuforums.org/showthread.php?t=765421")

---

