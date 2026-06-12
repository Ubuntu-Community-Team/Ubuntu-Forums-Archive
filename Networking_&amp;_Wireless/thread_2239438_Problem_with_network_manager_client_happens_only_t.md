---
title: "Problem with network manager client happens only to switching SSID"
date: 2014-08-13
forum: Networking &amp; Wireless
---

### Post by mctiew on 2014-08-13
I am using xubuntu LTS 14.04.

I have been using network manager to connect to a single configured AP without problem.

But as soon as I configure additional APs with correct password, switch to that SSID using network manager client is closed to impossible. It keeps saying "wireless network disconnected" or something.

However, if I delete the old SSID and only have one configured SSID, and then put the notebook to sleep and wake up, conection to the target SSID can be made very quickily. 

This problem make it impossible for me to store preconfigured SSIDs for switching. Each time I switch SSID, I have to delete the old SSID. You can imagine it's quite a nuisance.

---

### Post by mctiew on 2014-08-13
I found something in the network manager client setting which might have impact on this.

By default, when a SSID is configured, the attribute "automatically connect to this network when it is available" under the "general" tab will be ticked. So when multiple SSIDs are configured and multiple SSIDs are available, the software will get into a catch-22 situation of not knowing which SSID to connect to, and eventually it might connect to a SSID which is not the one selected manually.

 I think I will disable this setting and give it a test to see if this fixes my problem.

---

