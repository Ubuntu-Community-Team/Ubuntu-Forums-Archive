---
title: "Help: Dyn DNS Server"
date: 2008-02-26
forum: Networking &amp; Wireless
---

### Post by usernameomar on 2008-02-26
hey guys i need a good guide about installing and configuring a Dyn DNS Server in a single server

---

### Post by ruy_lopez on 2008-02-26
Set up an account with someone like no-ip. They offer free dynamic dns names. Then install the no-ip client. "sudo apt-get install no-ip" Then see "man no-ip" for configuring the client.

You don't actually run a dynamic dns server. You run a client which updates the ip address to which the dynamic name points.

---

### Post by .nedberg on 2008-02-26
> **ruy_lopez said:**
> Set up an account with someone like no-ip. They offer free dynamic dns names. Then install the no-ip client. "sudo apt-get install no-ip" Then see "man no-ip" for configuring the client.

You don't actually run a dynamic dns server. You run a client which updates the ip address to which the dynamic name points.

+1

I use no-ip and I have never had trouble. Easy and works!

I see a lot of people recomend [dyndns]("http://www.dyndns.com/") with ddclient though.

---

