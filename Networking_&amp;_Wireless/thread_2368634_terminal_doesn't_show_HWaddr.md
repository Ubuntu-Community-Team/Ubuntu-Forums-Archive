---
title: "terminal doesn't show HWaddr"
date: 2017-08-13
forum: Networking &amp; Wireless
---

### Post by trambar18 on 2017-08-13
i have a problem with my wireless interface. i wanna know my hardware adress but the "ifconfig" command doesn't give me anything. it gives me an ether output that looks like a hardware addres but i'm not sure if they are the same thing. how do i solve this??

---

### Post by vocx on 2017-08-13
> **trambar18 said:**
> i have a problem with my wireless interface. i wanna know my hardware adress but the "ifconfig" command doesn't give me anything. it gives me an ether output that looks like a hardware addres but i'm not sure if they are the same thing. how do i solve this??
What do you call a "hardware address"? This may be what is called more generally the "MAC address", which is basically fixed, and different for each hardware device in existence.

The MAC address has this hexadecimal form 4D:34:88:52:A7:0F

Check with 
```

lshw -c net
ifconfig

```

In the "lshw" output, it says "serial". In the "ifconfig" output it says "HWaddr".

This is different from the "IP address". The "IP address" is in general variable, and assigned by your router, while the MAC address is fixed for your device.

So, you should probably explain what you want to do ultimately with those addresses.

---

### Post by praseodym on 2017-08-13
Does it show "nothing" or does it not show your wireless interface? Try
```

ifconfig -a
```

---

### Post by chili555 on 2017-08-13
> **trambar18 said:**
> i have a problem with my wireless interface. i wanna know my hardware adress but the "ifconfig" command doesn't give me anything. it gives me an ether output that looks like a hardware addres but i'm not sure if they are the same thing. how do i solve this??They are the same. Please compare:```
lshw -C network
```It is called* serial *there, but you will see that both ether and serial refer to the device MAC address.

---

