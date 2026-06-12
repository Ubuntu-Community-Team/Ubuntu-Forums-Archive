---
title: "Dell Vostro 15 3000 series/ Intel Corporation Wireless 3160/ No stable connnection"
date: 2018-06-20
forum: Networking &amp; Wireless
---

### Post by luca-liontos on 2018-06-20
Hey guys, I need your help:
My Dell laptop refuses to stay connected with any wireless network at least according to the gui it does. 
Ifconfig shows that it is connected and has an ip. Either way it doesnt work.
I found an old post saying I have to run a script and give you guys the pastebin link so here I go:
[https://paste.ubuntu.com/p/Yz3Qshqqxw/](https://paste.ubuntu.com/p/Yz3Qshqqxw/)

Thanks in advance :)

---

### Post by chili555 on 2018-06-20
We notice this in your paste:> Channel occupancy:

     [COLOR="#FF0000"] 9   APs on   Frequency:2.412 GHz (Channel 1)[/COLOR]
      2   APs on   Frequency:2.437 GHz (Channel 6)
      3   APs on   Frequency:2.457 GHz (Channel 10)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.467 GHz (Channel 12)
      1   APs on   Frequency:5.18 GHz (Channel 36)
      1   APs on   Frequency:5.5 GHz (Channel 100)And also:> Cell 19 - Address: <MAC 'devolo-steini' [AC19]>
                    Channel:1
                    Frequency:2.412 GHz [COLOR="#FF0000"](Channel 1)[/COLOR]
                    Quality=70/70  Signal level=-32 dBm  
                    Encryption key:on
                    ESSID:"devolo-steini"Is your router set to channel 1 because you selected it unaware that you were in the most congested channel possible? Or is your router set to auto-select the channel? Here is an interesting post which explains why auto channel select is a terrible idea: [https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection](https://superuser.com/questions/1311149/why-do-wifi-routers-do-such-a-bad-job-of-channel-selection)

Please check the settings in the router and after turning off auto channel select, pick a less congested channel like 6 or 11.

If these steps don't help, we'll dig a bit deeper.

---

### Post by luca-liontos on 2018-06-20
Thank you :)
It was selected automatically. I changed it as suggested to 6. 
And ... It works. I hate AVM from now on and I freaking love you :D

For some reason this device was the only one affected. This device is the only one I own running Linux which is why I expected the problem there.

Thanks again :)

---

### Post by chili555 on 2018-06-20
Awesome! Glad it’s working.

---

