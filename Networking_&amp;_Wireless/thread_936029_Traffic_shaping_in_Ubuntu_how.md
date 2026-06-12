---
title: "Traffic shaping in Ubuntu: how?"
date: 2008-10-02
forum: Networking &amp; Wireless
---

### Post by Stason on 2008-10-02
I am setting up internet access in the area where only wireless internet is available. The tariff provides for unlimited internet from 00:00 until 08:00 and per Mb charge otherwise. I want to restrict P2P and large files (possibly even some extensions) in per Mb time. Where to start? Is it possible in Ubuntu at all?

---

### Post by puppywhacker on 2008-10-02
[Bandwidth Limiting HOWTO]("http://www.faqs.org/docs/Linux-HOWTO/Bandwidth-Limiting-HOWTO.html")

Hi, the above link discusses limiting bandwith, mainly using CBQ and Squid. It also discusses time-ing restraints. The funniest solution in that link is the use of cron to set different configurations for squid one for the night time and one for the daytime. You could use the same cron trick to firewall all P2P traffic during the day, or to limit the bandwith significantly.

filename or filesize blocking is protocol dependant. So if you are talking about HTTP you could use the squid http proxy. If you are talking abount P2P you have very little options.

---

