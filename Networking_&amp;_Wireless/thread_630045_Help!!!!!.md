---
title: "Help!!!!!"
date: 2007-12-02
forum: Networking &amp; Wireless
---

### Post by lollylegs on 2007-12-02
i'm a newbie to ubuntu and am trying to set up home webserver - no trouble doing that, but i figure out how to configure my external static ip (router) to private static ip (lan). when i ping my domain name i just keep getting my router and cant get through to my webserver. i have set up portforwarding to my static ip on lan but i'm just going around in circles. Hope somebody out there can help
regards lollylegs Australia

---

### Post by jflaker on 2007-12-02
> **lollylegs said:**
> i'm a newbie to ubuntu and am trying to set up home webserver - no trouble doing that, but i figure out how to configure my external static ip (router) to private static ip (lan). when i ping my domain name i just keep getting my router and cant get through to my webserver. i have set up portforwarding to my static ip on lan but i'm just going around in circles. Hope somebody out there can help
regards lollylegs Australia

you will need to open port 80 on the router.  Any other port will only get your router, not your internal machine.  Also, you must make sure your system has a static IP address or you may lose communications should the system IP address change.  Another consideration is that your ISP may be blocking inbound port 80 to prevent hosting a webserver, like you intend to do......

---

### Post by lollylegs on 2007-12-02
thanks for you quick response. just a couple of questions.
1. my router has static ip from isp e.g 124.178. etc
do use that as my gateway and disable dhcp or do i use 10.0.0.138 which is current gateway

2. if i used 124.178. etc could i then forward it to static system ip 10,0,0,36 for example

---

