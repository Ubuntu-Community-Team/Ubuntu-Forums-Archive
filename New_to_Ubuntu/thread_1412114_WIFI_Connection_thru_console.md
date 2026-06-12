---
title: "WIFI Connection thru console"
date: 2010-02-20
forum: New to Ubuntu
---

### Post by theharshone on 2010-02-20
Hey,

Because the rt2x00 people discontinued their legacy drivers, I am forced to use their all-in-one drivers, that won't work to well. With the legacy drivers, I would just do
```

sudo ifconfig rausb0 up
sudo iwconfig rausb0 essid <name> key open <key>
sudo dhclient rausb0

```

But now, the same commands do not work. dhclient can never find any working leases. Therefore, I am forced to use NetworkManager, which I do not like because I do not know how to use NetworkManager in connection scripts. Are there any other parameters that I need to use for the new drivers?

Thanks,

TheHarshOne.

---

