---
title: "Wireless driver issues"
date: 2010-11-16
forum: New to Ubuntu
---

### Post by vldster on 2010-11-16
I am going to start off by thanking everyone for the help. 
 
I am running 10.04 desktop on a Acer Asipre 3630 and I am unable to get the wireless set up to work. Making this harder, I can not get the internet throught the laptop's modem. The OS registers that it is plugged into the router but I can not access the internet. What did do wrong and how do I fix it?

---

### Post by amjjawad on 2010-11-17
> **vldster said:**
> I am going to start off by thanking everyone for the help. 
 
I am running 10.04 desktop on a Acer Asipre 3630 and I am unable to get the wireless set up to work. Making this harder, I can not get the internet throught the laptop's modem. The OS registers that it is plugged into the router but I can not access the internet. What did do wrong and how do I fix it?

Hi,

Did you try: ***System > Preferences > Network Connections > Wireless*** Tab?

Do you have a LAN port on that laptop? perhaps you could connect through LAN and download the driver of your Wireless Adapter just in case you need that.

Open a Terminal (Applications &#9656; Accessories &#9656; Terminal) and type the command: 
```
sudo lshw -C network
```

Please, post back the output and wrap the text with CODE tag.

---

### Post by pritam_par on 2011-07-20
Is your wireless driver are installed correctly. If not then install it by going to synaptic manager and search for "bcmwl". Install it . This has worked for me, hope this will help you also.

---

