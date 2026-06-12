---
title: "Low throughput with Qualcomm Atheros QC988x 802.11ac adapter"
date: 2017-01-26
forum: Networking &amp; Wireless
---

### Post by mpotts on 2017-01-26
Hi all, 

I'm using a QC Atheros QC988x 802.11ac radio adapter with Ubuntu 14.04 LTS and getting really low upstream (STA to AP) throughput. The specific radio I using is the Compex WLE900VX 

[http://www.compex.com.sg/product/wle900vx/](http://www.compex.com.sg/product/wle900vx/)

Testing using iperf, I cannot achieve much more than 15 Mbps. Downstream throughput (AP to STA) is roughly 145 Mbps. I get the same performance when testing with a variety of 802.11ac access points. Other 802.11ac client devices (iPads etc) can achieve 200+ Mbps upstream to the same test setup. I'm using the 5 GHz band.

The ath10k driver version and firmware appear to be pretty recent:

driver: 4.4.0-59-generic
fw: 10.2.4.70.9-2

iwconfig reports the radio as 802.11abgn. It almost appears that the radio is using its lowest transmit rates for some reason. 

Is anyone else able to achieve high STA to AP transmit rates with this chipset?

Thanks
Martin

---

