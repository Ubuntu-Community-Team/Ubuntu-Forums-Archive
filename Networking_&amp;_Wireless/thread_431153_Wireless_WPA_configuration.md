---
title: "Wireless WPA configuration"
date: 2007-05-02
forum: Networking &amp; Wireless
---

### Post by stormie_abdul on 2007-05-02
I just installed Ubuntu 7.04 on my Dell Inspiron Machine with Dell Wireless 1370 WLAN MiniPCI Card.

I am trying to configure my wireless router with WPA-Personal security. But I don't get to see configuration windows (Network Manager) as I see in [https://wiki.ubuntu.com/7.04Tour#head-98085b4c8272960e5a16777dd55bbfdf2266a834](https://wiki.ubuntu.com/7.04Tour#head-98085b4c8272960e5a16777dd55bbfdf2266a834)

I am just able to configure WEP with ascii/hex network key.

How can I get the latest Network Manager.

Best Regards,

Abdul

---

### Post by meglamaniac on 2007-05-02
Hello!

I had this exact problem too.
What you need to do is to click on the network icon and select "manual configuration".
From there, go into the properties for your wireless connection, select "enable roaming mode" and press ok.
Close the manual configuration dialog box.

It should now be working how the tour images show it. I'm not sure if it's a problem with some installs or they forgot to turn it on by default, but it wasn't working on my fresh install either.

---

