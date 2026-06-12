---
title: "Not able to connect to the bsnl broadband"
date: 2007-12-09
forum: Networking &amp; Wireless
---

### Post by ahmedwaseem2000 on 2007-12-09
Hi,

I was trying to follow the instructions given in the [http://www.ubuntu-in.org/wiki/Broadband_Howto](http://www.ubuntu-in.org/wiki/Broadband_Howto) link. i have finished all the stages and now when i try to save and restart it it gives me timed out error after 15 minutes. could you please help?


Thanks,
Waseem

---

### Post by Original Brownster on 2007-12-09
Hi,
Could you provide more information, which modem make and model do you have / which broadband providor, the instructions you point to are for a number of different modems and providers etc.

are you using an ethernet cable or wireless on the pc and is it recognised in your pc?

---

### Post by ahmedwaseem2000 on 2007-12-09
Hi,

Thanks for the reply. I was referring to bsnl connection and the make and model of the modem is "Huawei ADSL modem/router with ethernet and USB port " It has got both usb port and ethernet card. i tried both ways to connect it. when i try doing it from windows i am able to do it but it doesnt work when i try doing it from ubuntu. It does recognise it when i do pppoe command i does detect the modem.

Thanks,
Waseem

---

### Post by Original Brownster on 2007-12-10
> **ahmedwaseem2000 said:**
> Hi,

Thanks for the reply. I was referring to bsnl connection and the make and model of the modem is "Huawei ADSL modem/router with ethernet and USB port " It has got both usb port and ethernet card. i tried both ways to connect it. when i try doing it from windows i am able to do it but it doesnt work when i try doing it from ubuntu. It does recognise it when i do pppoe command i does detect the modem.

Thanks,
Waseem

Hi, sorry your post says bsnl, never mind. 

Connect using the ethernet cable and card on your pc.

You said running the pppoeconf detects your modem is this whilst using the ethernet cable?

You entered your username and password with no problem?

Did you enter the ip address(s) of some name servers provided by bsnl?

are you using the System>Administration>Networking tool to configure your network card?

from a terminal window post back the output of

$ifconfig -a

$netstat -rn

$cat /etc/resolv.conf

---

