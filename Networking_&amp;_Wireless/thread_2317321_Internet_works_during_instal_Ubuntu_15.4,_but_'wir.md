---
title: "Internet works during instal Ubuntu 15.4, but 'wireless device not available' on use"
date: 2016-03-15
forum: Networking &amp; Wireless
---

### Post by Ananthanarayanan on 2016-03-15
I have a Dell Inspiron 15 and I have installed Ubuntu 15.4. During the install process, the system connects to the Internet and installs packages (except one). But on logging in, it says 'you are not connected to the Internet' and the network manager says, 'wireless device not available', but this message is greyed.
I have run iwconfig and the wireless device, Qualcom Atheros, is shown.
Need guidance, please.

---

### Post by michi1983 on 2016-03-16
Hi,

could you please open up a terminal and post the output of ```
sudo rfkill list
```

---

### Post by gordintoronto on 2016-03-16
Also, Ubuntu 15.04 is end-of-life, so you should be trying 15.10.

---

