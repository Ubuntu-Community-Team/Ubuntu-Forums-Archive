---
title: "Bluetoothctl automate pairing process"
date: 2015-05-03
forum: Networking &amp; Wireless
---

### Post by erotavlas on 2015-05-03
Hi,
I'm using Ubuntu 14.04 LTS and I installed Pulseaudio 6 together with Bluez 5.30. Now, I'm looking for a way to automate the process of bluetooth pairing that requires to be logged into the system.
So I know that the necessary step are:
```

bluetoothctl
power on
discoverable on
agent on
default-agent
pairable on

```
For instance, I can write a script like this
```

#!/bin/bash
bluetoothctl << EOF
power on
discoverable on
agent on
default-agent
pairable on
EOF

```
but I do not know how to intercept the pairing request coming from devices and how to answer yes. After, I would like to run it as daemon. For reference [https://wiki.archlinux.org/index.php/Bluetooth](https://wiki.archlinux.org/index.php/Bluetooth)
Thank you

---

### Post by Matthew_Epler on 2016-01-20
Were you able to solve this? I'm trying to solve the same problem. Thanks for posting!

---

