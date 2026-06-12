---
title: "I may have broke my wireless"
date: 2010-01-28
forum: New to Ubuntu
---

### Post by robertrose6 on 2010-01-28
I tryed to turn off my wireless today with the (this was done after a update to)

sudo ifconfig wlan0 down 

It didnt work but now after a shutdown I can not get the card to come up. I allso get a SIOCSIFFLAGS: unkown error 132

here is the output of some commands 


Thanks for any help you can give me

---

### Post by RedSingularity on 2010-01-28
Did you try 

sudo ifconfig wlan0 up

---

### Post by robertrose6 on 2010-01-28
yes I did. I found a couple of commands on line that I tried 

I will post the commands and the results in a couple of min.

---

### Post by danking12 on 2010-01-29
You may want to try this just to see if it is a problem with your wireless card, or maybe just a network/connection configuration issues

```
iwlist wlan0 scan
```

Where wlan0 is the name of your wireless network adapter.

If it works property that should list the wireless networks within range.

Have you tried using the Network Connections applet? You should see it in the top right of your screen near the time. I have had good success using it with wireless in 9.10.

Goodluck!

---

### Post by robertrose6 on 2010-01-31
I did the following commands and then restarted and my wireless came back



rmmod ath5k
rfkill block all
rfkill unblock all
modprobe ath5k
rfkill unblock all
ifconfig wlan0 up

---

