---
title: "Huawei E392u-21 LTE dongle setup"
date: 2014-03-13
forum: Networking &amp; Wireless
---

### Post by Hans_Garry on 2014-03-13
I am trying to setup a Huawei E392u-21 4G dongle in Ubuntu (I am trying various different versions - mainly 12.10 and 13.10). I have managed to make the device work with the 'wvdial' command, via appropriate configuration in wvdial.conf. The wvdial approach creates a pp0 interface. When doing some speed tests, I observe that the maximum downlink speed that I get is around 42 Mbps. I have tried other LTE dongles in the past in Ubuntu (such as the Sierra Wireless Aircard 313u) and I have managed to see approximately 65 Mbps downlink throughput. I suspect that the low throughput with the E392u-21 is the fact that it is using a ppp0 interface, which the Aircard 313u is using a wwan0 interface (via simply doing $ dhclient wwan0 as root). However, I have not managed to setup the E392u-21 to work as a wwan0. Could someone help me configure that? 

Thanks, 
HG

---

