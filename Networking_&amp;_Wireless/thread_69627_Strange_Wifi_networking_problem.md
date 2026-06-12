---
title: "Strange Wifi networking problem"
date: 2005-09-27
forum: Networking &amp; Wireless
---

### Post by grinchy on 2005-09-27
I have a laptop running Ubuntu 5.04 and also windows 2000.

I am trying to connect to my colleges wifi network.

When i try with w2k i have absolutly no problems.

with ubuntu i have to first get my dhcp lease for the day using w2k then manually input  the ip, mask and dns servers.
Then ubuntu only sometimes connects to the network and only after a long time.

Any ideas?



Oh and the connection randomly drops for no apparent reason

---

### Post by odin on 2005-09-27
umh...I dont know if I undertand you well but I can tell you how I conect to my wifi network.

Follow all this commands(Let's say your wifi interface is eth0):

iwlist scanning eth0

then find in the list the Access Point you wanna conect to and then:

iwconfig eth0 essid "Whatever the AP is named"
dhclient eth0

and that's it.

That should make it work assuming that the Access Point has dhcp enabled.

hope this can help you out

---

