---
title: "On startup wired network not detected 50% of the time - 14.04"
date: 2014-07-25
forum: Networking &amp; Wireless
---

### Post by shag00 on 2014-07-25
Approximately half of my logon (Ubuntu restarts) attempts result in no network connection (no connection to router). The other half connect and work as expected. The connection never drops once it is connected so I have discounted a cable problem. My motherboard has 2 ethernet connectors with different MAC addresses and both return the same result so I have discounted a faulty ethernet port. Two other computers connect reliably to the router and I have swapped ports so I have discounted a router problem. The only way I can connect is to restart Ubuntu. The problem has only surfaced after upgrading to 14.04.

Any help appreciated.

---

### Post by justin-c-hawkins92 on 2014-07-26
Must be a bug or something went wrong during the installation from the upgrade. Are you only using the eth or wlan as well? Did you try to manually reatart it via terminal? It could be a work around for you if you can only connect 50% of the time:```
**# sudo /etc/init.d/networking restart**
``` Or you can try and stop then start back up with these: ```
**# sudo /etc/init.d/networking stop**
``` ```
**# sudo /etc/init.d/networking start**
```

---

### Post by shag00 on 2014-07-27
I tried both these methods firstly with the '#" and then without and it appears nothing happened, I certainly did not disconnect from the network which is what I expected after stopping the service.

To answer your question this PC is only connected via ethernet.

---

### Post by BadMichael on 2014-07-27
FWIW - I'm experiencing the same network start up problem as well. Turning off my DSL modem and turning it back on does the trick, but is not a long term solution.

---

### Post by justin-c-hawkins92 on 2014-07-27
I'm sorry that didn't work. Did you try: ```
sudo ifconfig eth0 down
``` then use: ```
sudo ifconfig eth0 up
``` I just tried those commands with my laptop with wlan0 and worked, but I had to disconnect and reconnect from my router. You are on ethernet so only thing you might need to do it unplug the cable and plug it back in if it doesn't start back. I appologize, I didn't tell you to not input the hashtag (#). The hashtag just means root access in the terminal, but with ubuntu the sudo command gives you root permission for the specified command.

Did you try and push in the reset button on your modem and let is cycle through? That might work as well. I can help you further if you post your output from running ifconfig in the terminal.

---

### Post by shag00 on 2014-07-29
It appears that the problem is related to the booting/logon process as all attempts to disconnect and reconnect without shutting Ubuntu down all connected without any problems.

After inputting the above commands there was no output at all, either with the router connected (with internet access) or disconnected.

---

