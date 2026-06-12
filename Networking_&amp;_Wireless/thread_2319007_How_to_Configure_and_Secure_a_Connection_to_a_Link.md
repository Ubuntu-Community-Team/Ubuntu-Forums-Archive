---
title: "How to Configure and Secure a Connection to a Linksys Smart-WiFi Dual-Band Router?"
date: 2016-03-31
forum: Networking &amp; Wireless
---

### Post by oldefoxx on 2016-03-31
My old EA3500 router died a lingering death on me, but when it completely went, I learned you cannot install Ubuntu unless yjere is something   wiithout some tie to the network, even if it is an essentially dead router with no attachment to a modem.  That doesn't make much sense.  There is plenty of DVD drive space to make a much bigger ISO image, .leaving less to download and install on the fly.  Just a passing observation.

Working with Linksys tech support via chat, they had me rename and set WPA2 security on band 2.4GHz and 5GHz. This disrupted connections, but they reconnected well enough until suddenly 192.168.1.1 would not connect a all.  A reboot to care of that.  But checking the network from Ubuntu's side. I was startled to see the original network name from the factory, two new test connections, and only my 2.4GHz connection there.  No sign of the 5GHz  connection.

But if I edit the connections.  I see what I set up as connection on the router, with major differences.  First. one connection has a MAC address, but not in a style I would expect.  It contains embedded colons.  The other connection has a blank for a MAC address.  But when I go back and check just now, it looks right.  I click ob the ghost connections from the factory testing and get asked for a password.  I click Cancel instead, and they disappear.

Meanwhile Ubuntu has created twp unsecured connections. Wired Connection 1 and Eithernet connection 1.  Good if you need to connect and work with tech support to configure the router anf not have yo cable around it direct to the modem to get online -- but maybe this is the router's doing if it hasn't been set up yet.

I need expert input/  I ;ppk at Network and all I see is network:///smb-root.  That's it.  It calla itself Windows Network, buyt it is an empty folder.  I see various tools listed for onstallong, but nothing highly rated.  You know what they say, "If you don't knpw, Ask".

For a new network or connection, do I do a Create then an Add?  If I elect to create, I only have 2 types of WEP to consider for security.  At another point, I only have MDS to consider.  How do I weigh these choices against router settings that are limited to WPA, WPA Personal, WPA Enterprise,  WPA2 Personal, WPA2 Enterprise, WPA2/WPA Mixed Personal, WPA2/WPA Mixed Enterprise.

---

