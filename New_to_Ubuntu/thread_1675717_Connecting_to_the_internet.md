---
title: "Connecting to the internet"
date: 2011-01-26
forum: New to Ubuntu
---

### Post by kaustabh93 on 2011-01-26
I'm absolutely new to UBUNTU and use UBUNTU 9.10.My ethernet is DG41RQ.My modem(Nokia Siemens C2110) supports both ethernet card as well as USB.How do I connect to the internet.Please give me step by step instructions.

---

### Post by fabricator4 on 2011-01-26
> **kaustabh93 said:**
> I'm absolutely new to UBUNTU and use UBUNTU 9.10.My ethernet is DG41RQ.My modem(Nokia Siemens C2110) supports both ethernet card as well as USB.How do I connect to the internet.Please give me step by step instructions.

According to [this]("http://www.intel.com/support/motherboards/desktop/dg41rq/sb/CS-030262.htm") blurb from Intel your board is supported by the kernel.

Just plug the ethernet cable into your router/modem and it will connect automatically.

If it doesn't connect you may not have an ISDN connection to your service provider's servers.  If you can ping the router then problem will be from the router to the service provider.

To Ping the router:
Look in the manual for your router and find the IP address you need to configure the router.

Click System -> Administration -> Network tools

Next click on the ping tab, type the IP address into the box, then click on the ping button.

If it pings OK then you are talking to the router.

Next open Firefox and type the IP address into the address bar.  It should open up the configuration for the router.  Don't change anything you don't understand the use of, but if it's also a wireless router _do_ make sure security is enabled.

A this point, if you can get to the router configuration and you're not connecting to the internet the best people you can speak to are the technical support team for your internet service provider.  They'll be able to help you configure the router so that it will connect to their servers, assuming that your telco has configured everything correctly.

Chris.

---

