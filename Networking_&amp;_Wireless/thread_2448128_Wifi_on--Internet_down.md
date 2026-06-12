---
title: "Wifi on--Internet down"
date: 2020-08-02
forum: Networking &amp; Wireless
---

### Post by jps984 on 2020-08-02
Hello,
I am fairly new to linux and know a few of the basic commands.

I have a seemingly random problem with my internet connection.  The internet connection will drop, but the wifi will still show connected to y ATT modem.   I can resume using the internet connections after turning off, then on the wifi connection.

I have tried troubleshooting the issue myself, but it is beyond my capabilities and would like some help.  

[LIST]
[*]nmcli will show change connectivity from full to limited.
[*]Ip address still shows my ip address
[*]Cannot ping modem, other local machines or internet
[*]Can ping localhost
[/LIST]

Thanks for your help 

Here are the results from wireless-info.txt on pastebin

[https://paste.ubuntu.com/p/KSSsBw9pqW/](https://paste.ubuntu.com/p/KSSsBw9pqW/)

ubuntu 18.04.04
lenovo w520

---

### Post by chili555 on 2020-08-02
```
ATT6BKu7I8                      <MAC 'ATT6BKu7I8' [AC3]>  Infra  11    2462 MHz  130 Mbit/s  80      &#9602;&#9604;&#9606;_  WPA2         no             
ATT6BKu7I8                      <MAC 'ATT6BKu7I8' [AC1]>  Infra  136   5680 MHz  540 Mbit/s  66      &#9602;&#9604;&#9606;_  WPA2         yes     *      
```I suspect that at least some of the issue is that your wireless device is roaming between the 2.4 gHz and the 5 gHz segments of your router, looking for a better connection. That reminds me of my ex-girlfriend!

In the administration pages of the router, I suggest that you rename the segments to something like ATT6BK-2.4 and ATT6BK-5. Set both segments to fixed channels, not autoselect. Then connect to the usually faster 5 gHz segment ATT6BK-5 and I suspect that the dropping will be solved.

---

### Post by jps984 on 2020-08-03
Thanks chili555 I will try it.

jp

---

