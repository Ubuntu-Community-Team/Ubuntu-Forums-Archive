---
title: "Lubuntu 14.10 how to set a static IP"
date: 2015-05-03
forum: Networking &amp; Wireless
---

### Post by john364 on 2015-05-03
I've followed a few guides which say to edit network and networking etc etc.
I reboot and either networking will not work or my networking reverts back to a dynamic IP address.

I can create a new profile but when I reboot It decides to use the default which is dynamic...


Help how do I get Lubuntu to use a static IP address?

---

### Post by TheFu on 2015-05-03
Please post your /etc/network/interface file - it is probably a tiny mistake that we've all made.

---

### Post by Dennis N on 2015-05-03
Your router may allow you to set static IP addresses. That is how I set mine nowadays. I would check into that possibility first as it is easy to do.

---

### Post by SeijiSensei on 2015-05-03
[https://help.ubuntu.com/lts/serverguide/network-configuration.html#static-ip-addressing](https://help.ubuntu.com/lts/serverguide/network-configuration.html#static-ip-addressing)

[http://ubuntuguide.org/wiki/Ubuntu_Trusty_Networking#Set_a_static_IP_address]("http://ubuntuguide.org/wiki/Ubuntu_Trusty_Networking#Set_a_static_IP_address")

---

### Post by TheFu on 2015-05-03
> **Dennis N said:**
> Your router may allow you to set a static IP address. That is how I set mine nowadays. I would check into that possibility first as it is easy to do.

[http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management](http://blog.jdpfu.com/2011/07/18/use-your-router-to-centralize-your-network-device-management) explains this method. Not a bad idea for most people. I use it for non-servers - like laptops, media devices, etc.

---

### Post by john364 on 2015-05-05
> **Dennis N said:**
> Your router may allow you to set static IP addresses. That is how I set mine nowadays. I would check into that possibility first as it is easy to do.

Unfortunately my router doesn't have this function... My old one did but that is big long rant right there...
And that is how I use to do it when running ubuntu.... Havent run ubuntu since unity.

So no one can tell me how to do it :S....

Currently I am using the gui and have disabled the default network profile. This seems to be working....


I know there is away editing /etc/network and a few other files.... I guess Ill just keep plodding along then.

---

### Post by TheFu on 2015-05-05
Did you read the other replies?
Did you click on those links?
Did you do what was asked both above and in the links?

I know that I've posted at least 20 examples in these forums and that those links above in this thread explain what you need.

Is there something you don't understand?

---

