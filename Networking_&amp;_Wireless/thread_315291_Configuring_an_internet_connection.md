---
title: "Configuring an internet connection"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by wersdaluv on 2006-12-08
I just installed Ubuntu 6.10. I tried to connect to the internet by connecting to my wifi. After connecting to the wifi, I still was not able to access the internet. What should I do?

---

### Post by endersshadow on 2006-12-08
I need a couple of pieces of info from you before I can help.  I need the outputs of these commands:

```
lspci | grep -i wireless
ifconfig
iwconfig
```

Thanks!

---

### Post by wersdaluv on 2006-12-08
after entering iwconfig, it said, "no wireless extensions"

---

### Post by endersshadow on 2006-12-09
Check out the article on how to do it:

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

---

