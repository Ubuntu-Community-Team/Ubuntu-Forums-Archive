---
title: "Setup WDS using TP-Link W8970 v3 stock and Netgear WNDR4300 v4 openWRT"
date: 2015-10-07
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2015-10-07
Hi,
I would like to setup a WDS by using my two routers. I have a TP-Link W8970 v3 with stock latest firmware installed and a Netgear WNDR4300 v4 with openWRT 15.05 installed. I cannot install openWRT on my TP-Link and I have to use it as Master device.
I followed the official guide from TP-Link [http://www.tp-link.com/lk/faq-440.html](http://www.tp-link.com/lk/faq-440.html) where is specified only how to configure the Client of a WDS. So I understood that I have to configure it as normal Master Access Point and there is not the possibility to configure it as WDS Master Access Point (from documentation, Enable WDS: unchecked (WDS is only enabled on the Client)).
I read the official documentation of openWRT [http://wiki.openwrt.org/doc/recipes/atheroswds](http://wiki.openwrt.org/doc/recipes/atheroswds) and I used it to configure my Netgear WNDR4300 via GUI (from documentation Access Point the wireless mode should be "Access Point (WDS)" while for the remote wireless bridge device the wireless mode should be "Client (WDS)"). I made a scan of available networks and I joined the Master Access Point network.
Now, I can connect together the two routers via 2.4 GHz 802.11 b/g/n network. However, in order to allow to the wifi devices to use the Client router, I have to setup a second network at 5 GHz 802.11 a/n on my Client router and it does not extend the original network. Moreover, if I configure a static address LAN interface I can use wired connection on the Client router.
This is not the behaviour that I expect about a WDS configuration. Where is my mistake?

---

### Post by Elizabeth_Berry on 2016-04-27
In order to setup and configure your Netgear router using the default ip address 192.168.0.1, you should have an active internet connection and also necessary [configuration information]("http://www.ipaddressdefinition.com/192-168-0-1/") given by your internet service provider (ISP). Additionally, you should also have static ip addresses, DNS addresses, domain & host names, and router&#8217;s default login details like username and password.

---

