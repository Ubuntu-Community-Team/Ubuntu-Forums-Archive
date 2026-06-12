---
title: "web-stick disconnects randomly"
date: 2019-01-16
forum: Networking &amp; Wireless
---

### Post by rosika on 2019-01-16
Hi altogether,


every now and then it happens that my web-stick disconnects all by itself.
About half a minute after that it connects again and I can establish a new connection to my umts-provider. But it gets annoying.


My modem is:```



lsusb | grep -i huawei
Bus 001 Device 024: ID 12d1:1001 Huawei Technologies Co., Ltd. E169/E620/E800 HSDPA Modem



```On [https://gist.github.com/Rosika2/030b75abbd24f98cba5c099c1435b7c3](https://gist.github.com/Rosika2/030b75abbd24f98cba5c099c1435b7c3)  I posted the output of my syslog-messages which might give a clue
as to what´s happening. But I really need help with that as I´m bit at a loss here.

Thanks a lot in advance.

Rosika :confused:

P.S.: my system: Lubuntu 16.04.5 LTS

---

### Post by rosika on 2019-01-28
O.K.,
it seems like I´ve got too many usb-devices connected to my hub(s). I was able to discuss this matter on [https://itsfoss.community/t/web-stick-disconnects-randomly/2771/13](https://itsfoss.community/t/web-stick-disconnects-randomly/2771/13) .
[FONT=Helvetica]The disconnection seems to be directly linked to the low power due to my hub-configuration.

I´m going to try to solve the problem by changing that.

Cheers.
Rosika [/FONT]:)

---

