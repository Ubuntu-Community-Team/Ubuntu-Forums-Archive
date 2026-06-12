---
title: "Network Config Error on Pi"
date: 2022-04-09
forum: Networking &amp; Wireless
---

### Post by uRock on 2022-04-09
Howdy,

I am getting error ```
/etc/netplan/50-cloud-init.yaml:16:7: Invalid YAML: could not find expected ':':
        password: 12345678
```

My config is as follows;

```
network:
  ethernets:
     eth0;
      dhcp4: true
      optional: true
  wifis:
      wlan0:
        dhcp4: true
        optional: true
        accesspoints:
        accesspointname
        password: 12345678
```
Not sure what I am doing wrong. Any direction would be awesome!

---

### Post by jeremy31 on 2022-04-09
You could try
```

network:
  ethernets:
     eth0:
      dhcp4: true
      optional: true
  wifis:
      wlan0:
        dhcp4: true
        optional: true
        accesspoints:
        accesspointname:
        password: 12345678
```

---

### Post by chili555 on 2022-04-09
Please see:

```
cat /usr/share/doc/netplan/examples/wireless.yaml
```I believe you have some indentation and spacing errors. I also believe that the network name and password are enclosed in quotes "xxxxx".

---

### Post by uRock on 2022-04-09
Thanks, the ; I posted here was the correct : in the actual configuration. I've been messing around with the indentation, but still getting errors about indentation.

If the error has a caret is under the left of an entry, does that mean it needs more indentation and to the right needing more/less to the right.

---

### Post by chili555 on 2022-04-09
I don't know for sure that the carat means to indent left or right; I just assumed it meant that what I have is wrong!

I just try to match perfectly the indentation in the example.

---

### Post by uRock on 2022-04-09
Thanks chili555. I found that the quotation marks and a ":" were missing after the accesspoints entry.

Now to move on to the fun stuff.

In case someone else finds this thread;
```
network:
  ethernets:
    eth0:
      dhcp4: true
      optional: true
  wifis: [COLOR="#FF0000"]<2 spaces>[/COLOR]
    wlan0: [COLOR="#FF0000"]<4 spaces>[/COLOR]
      dhcp4: true [COLOR="#FF0000"]<6 spaces>[/COLOR]
      optional: true [COLOR="#FF0000"]<6 spaces>[/COLOR]
      access-points: [COLOR="#FF0000"]<6 spaces>[/COLOR]
        "SSID": [COLOR="#FF0000"]<8 spaces>[/COLOR]
          password: "password" [COLOR="#FF0000"]<10 spaces>[/COLOR]
```

---

### Post by uRock on 2022-04-09
> **chili555 said:**
> I don't know for sure that the carat means to indent left or right; I just assumed it meant that what I have is wrong!

I just try to match perfectly the indentation in the example.

Thanks, was hoping it had more purpose. Was purposeful enough to let me know something was missing to the left of it. It mentioned indentation, but ended up being the need for a ":"

---

