---
title: "Problems connecting to a wireless network"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by hurst21uk on 2009-01-06
After just installing Ubuntu, I can not connect to my wireless network. A wired connection is fine as I am typing this in Ubuntu.

I followed the instructions in the Ubuntu help, my driver/wireless adaptor came up as 'UNCLAIMED' so I installed ndisgtk, I went to System > Administration > Windows Wireless Drivers. I then got what I think is the Atheros Wireless network card driver, I click Install New Driver, then in the box of currently installed network drivers it has 'netathr'(name of the driver) Hardware Present : Yes. When I click configure network it says 'Could not find a network configuration tool'

Now I go to System > Preferences > Network Tools and my wireless adaptor does still not show up. 

Being new, I am hoping it is something simple! Any ideas of a solution?

---

### Post by Titan8990 on 2009-01-06
Go to Applications -> Accessories -> Terminal

Type the following:

```
lspci -vv
```


Post the output here.

---

### Post by hurst21uk on 2009-01-06
Its ok now. I managed to find some information. I ended up downloading a different driver and things are now up and running. Thanks anyway

---

### Post by Titan8990 on 2009-01-06
You may also want to look into the madwifi drivers if that is not what you did. Madwifi is typically compatible with Atheros chips.

---

