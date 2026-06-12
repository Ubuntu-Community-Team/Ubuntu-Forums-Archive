---
title: "Bluetooth keeps connecting and immediately disconnecting after upgrade to 18.04"
date: 2018-06-07
forum: Networking &amp; Wireless
---

### Post by pldiewald on 2018-06-07
After I upgraded to 18.04 a few days ago, I've found that there's an issue with Bluetooth. When I try to use my Bose wireless headphones to listen to something on my Ubuntu laptop, I keep hearing the message, "[network name] connected", then immediately, "[network name] disconnected" without my having done anything to disconnect the headphones. The connection isn't being lost--if I did, I'd hear, "[network name] lost." If I go into my settings, I see that Bluetooth is turned on, but the network is disconnected.

Now, if I restart my laptop, the connection works just fine. The problem seems to occur only when I close the lid and put the laptop to sleep, then wake the laptop from sleep mode. I've tried re-pairing the headphones with the laptop, and that only works until I put the laptop in sleep and then wake it.

The headphones worked just fine before the upgrade, and there's been no recent update to the Bose firmware, so I am pretty sure this problem is caused by the upgrade.

Suggestions on how to resolve it? I don't want to have to restart my laptop all the time just to listen to music.

---

### Post by minecnly on 2018-06-08
I'm having exactly the same problem here. ```
systemctl restart bluetooth
``` solves the problem for me.

---

### Post by pldiewald on 2018-06-08
Thanks! It only fixes the problem temporarily - if I just shut the laptop and wake it from sleep, I have to do this again. Still need a permanent fix, but at least this keeps me from having to restart all the time.

---

### Post by mkay581 on 2018-07-10
I am also having this problem. The workaround works temporarily until you close the laptop.

---

### Post by pldiewald on 2018-07-29
Well, I'm quite happy to report that this issue stopped with a recent update. No more restarting the bluetooth.

---

