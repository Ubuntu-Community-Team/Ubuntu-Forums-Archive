---
title: "Internt Not Work? (Live CD)"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by ToaStOmGi on 2008-02-14
Was wondering if you could get on the internt while using the Live CD. Because i was using the Live CD and my internet would not work. So idk if i want to install it or not. Any help?

---

### Post by jan quark on 2008-02-14
perhaps you need to install the proper drivers for your

wlan or ethernet ?

run these commands in terminal to specify your network devices and post the output 
thank you

```
iwconfig
```
```

ifconfig
```
```

lspci
```

```
sudo lshw -C network
```

---

### Post by ToaStOmGi on 2008-02-14
I am using ethernet, And how do i bring up the terminal to run the commands?

---

### Post by ToaStOmGi on 2008-02-14
It works now. Thanks for the help anyway <3

---

