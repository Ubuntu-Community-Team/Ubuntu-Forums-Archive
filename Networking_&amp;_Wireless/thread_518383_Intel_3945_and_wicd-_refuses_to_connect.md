---
title: "Intel 3945 and wicd- refuses to connect"
date: 2007-08-05
forum: Networking &amp; Wireless
---

### Post by saxonthebeach908 on 2007-08-05
Just did a fresh install of Feisty on my m1210, and no matter what I do, my Intel PRO/wireless 3945 will not connect to my network. I noticed many people were saying around here to switch to wicd, so I tried that, and still no luck- it sees the network fine, but gets stuck at "obtaining IP adress..." and then times out. I have tried everything in terms of encryption- WEP, WPA, and no encryption at all but to no avail. 

Can anyone help me? I really want to use ubuntu on this laptop, but without wireless, its useless...

---

### Post by imdano on 2007-08-05
The 3945 usually works without any problems out of the box.  Whats the output of ```
sudo lshw -C network
```

---

### Post by Jay_Bee on 2007-09-04
I use Gutsy Tribe 5 with this wireless in my laptop and I am experiencing the same problem. I see the networks available but I am unable to connect to them. So I tried Wifi radar and that didn't work so I tried Wicd, but it also gets stuck at Obtaining IP address... I belive this is the driver issue

---

