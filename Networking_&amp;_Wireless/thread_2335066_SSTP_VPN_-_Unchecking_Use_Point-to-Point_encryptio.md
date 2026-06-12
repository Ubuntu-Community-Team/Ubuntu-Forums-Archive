---
title: "SSTP VPN - Unchecking Use Point-to-Point encryption (MPPE)?"
date: 2016-08-25
forum: Networking &amp; Wireless
---

### Post by ultragamer2 on 2016-08-25
Newbie Question.

There is a vpn setup page that says when setting up an sstp vpn connection to Uncheck **&#8216;Use Point-to-Point encryption (MPPE)&#8217;**
[https://support.ivacy.com/kb/how-to-setup-vpn-on-linux-mint/#sstp](https://support.ivacy.com/kb/how-to-setup-vpn-on-linux-mint/#sstp)

[URL="https://support.ivacy.com/wp-content/uploads/2016/03/Linux-Mint-17.1-2016-03-07-21-12-39.png"][IMG]https://support.ivacy.com/wp-content/uploads/2016/03/Linux-Mint-17.1-2016-03-07-21-12-39.png[/IMG]
[/URL]

If you uncheck this is there no encryption for a vpn connection?

---

### Post by SeijiSensei on 2016-08-25
Yes, though I don't see any good reasons for using the old PPTP protocol with its known [security]("http://security.stackexchange.com/questions/45509/are-there-any-known-vulnerabilities-in-pptp-vpns-when-configured-properly") [vulnerabiilties]("https://www.schneier.com/academic/pptp/") over [OpenVPN]("http://openvpn.net/").

---

