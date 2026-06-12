---
title: "Wake On Lan not workin"
date: 2022-09-18
forum: Networking &amp; Wireless
---

### Post by carnagelan on 2022-09-18
Hi All,

I have an ubuntu server which i would like to wake up via ether-wake
I have done my checks and the network card on the server does support WOL and it is enabled in the BIOS

If i manually shut down the server via the commant ```
sudo shutdown
```

On my work station pc which is running centos  i type in ```
sudo ether-wake -i eth0 macaddress
```
and that doesnt start up my server.

If i manually turn on my pc via the power button and before it gets to the boot loader turn it off again.
Then i redo the ether-wake command it will turn on the pc. This has been confusing me

So in theory, everytime i run the shutdown command it wont turn on the server
but, if i manually turn it on then off again. ether-wake works

---

