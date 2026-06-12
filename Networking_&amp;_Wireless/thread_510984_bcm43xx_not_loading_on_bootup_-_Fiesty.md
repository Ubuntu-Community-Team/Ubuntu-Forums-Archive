---
title: "bcm43xx not loading on bootup - Fiesty"
date: 2007-07-27
forum: Networking &amp; Wireless
---

### Post by neil1961 on 2007-07-27
Having performed the steps to use the native drivers in the kernel as detailed in the link below:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty) 

I am having to manually load the bcm43xx module each time I start Ubuntu. I am using kernel 2.6.20. I thought the bcm43xx module is loaded automatically but looking at dmesg there is no sign of this being loaded.

Note: I had previously upgraded from Dapper to Edgy to Fiesty and was using ndiswrapper. I was having wireless network problems and decided to use the bcm43xx native driver now i had the 2.6.20 kernel. 

any any ideas?

---

### Post by kevdog on 2007-07-27
What command are you using to load the bcm43xx driver??

If it is: sudo modprobe bcm43xx,
then do the folowing:
```

echo bcm43xx | sudo tee -a /etc/modules
```

---

### Post by neil1961 on 2007-07-27
Fixed - thank you so much. I was using the entry  "modprobe bcm43xx" in the modules file - pretty dumb of me. 

As matter of interest why do i have to do this? All communication I have seen related to this suggests bcm43xx is loaded automatically on boot up. The only way to prevent it is to blacklist this - which I had for the last 18months when I was using ndiswrapper.

Thanks again for the support...:)

Neil

---

