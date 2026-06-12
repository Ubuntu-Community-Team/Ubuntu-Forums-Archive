---
title: "Strange iwlist..."
date: 2007-03-20
forum: Networking &amp; Wireless
---

### Post by t4thfavor on 2007-03-20
I have a weird issue, which may not be an issue, but an undocumented feature. 

I have a prismGT full MAC WIFI card from senao, I believe its a isl3886 or something like that. 
The card works great, but while at work I have a hard time connecting to the wireless AP. I decided that I would boost the txpower a bit in order to clear the walls for better coverage.
When I executed the command 
```

iwlist eth2 txpower

```

I get:
```

eth2      unknown transmit-power information.

          Current Tx-Power=31 dBm       (1258 mW)

```

which is a bit weird, I looked into dbm to watts and it said that the 31dbm should be 255mW not 1258mW. Seems like the driver has something funny going on, or I am just not skilled in the art of google.

---

