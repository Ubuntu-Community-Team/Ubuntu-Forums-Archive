---
title: "Problem with new router"
date: 2008-05-09
forum: Networking &amp; Wireless
---

### Post by toadliy on 2008-05-09
I just got a new Linksys router (WRT54G v8) set up and configured. With an ethernet cable between my computer and the router I can connect to the internet just fine, but I can't connect to it wirelessly. It's not an issue with my wireless card; I could connect to my old router wirelessly without issue, as could the Windows computer downstairs. Now, both computers detect the router's wireless broadcast, but can't actually connect to the internet. The windows computer can't connect to the router, period, whereas my laptop (running Ubuntu) insists that it's connected wirelessly, but can't actually get online. Either way, no wireless internet connection. I've had a friend with much more experience than myself have a look at it, and his conclusion was that the router is probably defective. I restored factory defaults and configured it a second time, with the same results. Should I just give up and send the router back to NewEgg and get a new/different router?

---

### Post by Pumalite on 2008-05-09
How did you configure your router? What settings?

---

### Post by .rdg on 2008-05-09
Don't know your exact configuration, so can't be 100% sure. There is a small possibility you configured your wifi section of the router to permit only selected MAC addresses to connect (Wireless MAC Filter). But as you told yourself - Ubuntu connects to your network just fine. You could test whether you receive a proper address from DHCP server included in this router (in terminal just type: ifconfig). It *should* just work, but you never know when you can't see.

Also - did you try to upgrade the firmware? Perhaps there is some issue with the current one?

Regards,
.rdg

---

### Post by toadliy on 2008-05-09
I upgraded the firmware this morning, actually. I have wireless security disabled (just until I get the wireless working, don't worry...) and MAC address filtering disabled. As far as the other options, it's configured exactly the way it's supposed to be according to the Linksys website. I've been speaking with a tech support person for a good 35-40 minutes now, but nothing seems to be working.

---

### Post by .rdg on 2008-05-10
It would leave just the simplest tests to do then:

- ping the gateway (the router) after you get your IP address from dhcp,
- traceroute to some Internet address.

The second one should definitely say if it's broken.

---

### Post by toadliy on 2008-05-10
Thank you, everyone, for your help. As per tech support's suggestion, I reset the router and reconfigured, and it's working correctly. Third time's the charm, I guess.

---

