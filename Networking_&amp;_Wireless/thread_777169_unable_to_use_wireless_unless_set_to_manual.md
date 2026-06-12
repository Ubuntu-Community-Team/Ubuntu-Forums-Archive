---
title: "unable to use wireless unless set to manual"
date: 2008-05-01
forum: Networking &amp; Wireless
---

### Post by Borzo on 2008-05-01
Hi All,

I have just upgraded to Hardy Heron ( clean install ) but I am unable to connect to any networks when network manager is set to roaming mode.

I am able to connect to my home network when network manager is set manual, however the network is never connected on boot time. To make it work I have to do : 

sudo /etc/init.d/networking restart

Is there any way have roaming mode working? or atleaset to have the connection start automatically?

thanks.

---

### Post by cemptor on 2008-05-02
Have been having similar problems in the last few months with Gutsy and now with Hardy.

I can start wireless networking if I do a /etc/init.d/networking restart.

I have a Broadcom wireless card and Hardy 64 bit

---

