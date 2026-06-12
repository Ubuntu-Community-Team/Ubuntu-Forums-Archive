---
title: "Intel 7260 suddenly slowed down connection after 1+ year of fine operation on 16.04"
date: 2018-02-27
forum: Networking &amp; Wireless
---

### Post by S. Cornelissen on 2018-02-27
I have a, to me, mysterious problem. I hope somebody can help, thanks in advance.

I put all my output of the wireless info script in this pastebin, I hope I did it correctly: [https://pastebin.com/NfMivT1k](https://pastebin.com/NfMivT1k)
[B]
The problem in a nutshell: since a few weeks my wireless suddenly has bad reception most of the time[/B]
I have a Lenovo S540 laptop. It contains a Intel Corporation Wireless-N 7260 card. It has been running fine for over a year. A few weeks ago reception has drastically reduced and became very sensitive to the distance to the wifi signal. I.e.: from my house I used to pick up 8-9 wifi networks and was able to use my own wifi throughout the house. Now I only pick up my own wifi network. Connection speed is fine when I remain within +/- 4 metres of the router. When I go further it quicky drops to zero. Important note: sometimes (about 2-5% of the time I would guess) it works fine as it used to. So it is still able to work properly, but does not do so most of the time. I have not discovered a pattern on when it works well and when it does not

**I had this before, then was able to solve it up until now by replacing the wireless card**
I have had the same / a very similar problem before. About 1.5 year ago the same happened with the Intel Corporation Wireless 7260 card that was originally in the laptop. I did not find any solution then either, so I chose to replace the card by ordering a new one. (Same type number, only the version that also supported 5G.) That one worked fine up until the current (identical) problem.

[B]I have tried all the diagnostics / solutions that  I could think of, but no success
[/B]
[LIST=1]
[*]I updated all my packages on Ubuntu 16.04.
[*]I tried to see whether it was a kernel problem: so I downgraded to a 4.8 kernel and upgraded to a 4.13 kernel (from 4.10.0.26) but neither gave improvement.
[*]I tried with a Ubuntu 17.10 live USB-stick: no improvement.
[*]I checked the card itself to see if there was a loose hardware connector: could not see one.
[*]It does not seem to be a problem in my wifi network: other devices like my phone still function the same and see all kinds of other wifi networks.
[/LIST]
[B]
Anyone with a suggestion?
[/B]I would be very grateful. If you need any additional info, let me know. Thanks a lot!

---

### Post by kerry_s on 2018-02-27
have you tried restarting your router?

---

### Post by S. Cornelissen on 2018-02-27
Yes, I have. It unfortunately gave no improvement. I am reasonably sure it is not a problem of my router/network specifically: the laptop with the problem can also not find the wifi of my neighbors anymore, which it could a while ago. In addition: other devices like my phone can still connect flawlessly to my own wifi and spot those of the neighbors.

---

### Post by jeremy31 on 2018-02-27
I would disable power management on the wifi using
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Then reboot

---

### Post by S. Cornelissen on 2018-03-05
Hi Jeremy, thanks for the suggestion! I disabled the power management as you said. It has not solved the problem. I still have poor reception a large part of the time. (It feels that I do have normal reception more often after disabling power management. Say 20% of the time instead of 5%. But I am not sure, it might also be my imagination.)

Any other suggestions? I hope there is more to try. Thanks in advance.

---

### Post by S. Cornelissen on 2018-03-09
The problem has persisted in the previous week. It has gotten to a very annoying point where I am starting to consider buying a new laptop just because of this. Is there anyone with another suggestion? Or a suggestion for a another place to ask for help? Thanks a lot!

---

### Post by jeremy31 on 2018-03-09
I would change the Network Manager settings to disable/ignore IPv6 and disable the firewall

---

### Post by Hadaka on 2018-03-09
Hi the wireless report is showing very weak signal.
how far are you from the router ?
Please re-seat the wireless card and verify antenna connections
are secure and corrosion free.

#Wireless report line..430
```
wlp4s0    Scan completed :

 Cell 01 - Address: <MAC 'Tommie5G' [AC1]>

                     Channel:100

                     Frequency:5.5 GHz (Channel 100)
                     Quality=[COLOR=#ff0000]**33/70**[/COLOR]  Signal level=-77 dBm  
```

#Wireless report line..452
 ```
Cell 02 - Address: <MAC 'Tommie' [AC2]>                     Channel:6
                     Frequency:2.437 GHz (Channel 6)

                     Quality=[COLOR=#ff0000]**25/70**[/COLOR]  Signal level=-85 dBm
```
 
#Set IPv6 to Ignore..
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Tommie5G'
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Tommie'
sudo systemctl restart network-manager.service 
```
Thanks.

---

### Post by S. Cornelissen on 2018-03-13
> **jeremy31 said:**
> I would change the Network Manager settings to disable/ignore IPv6 and disable the firewall

Do you mean the per network settings? I have set IPv6 to "Ignore" for my home wifi network. I am not sure how to disable the firewall. It is greyed out in the Network Manager settings of my home wifi network. Is that enough?

The changes do not seem to make a difference unfortunately.

---

### Post by S. Cornelissen on 2018-03-13
> **Hadaka said:**
> Hi the wireless report is showing very weak signal.
how far are you from the router ?
Please re-seat the wireless card and verify antenna connections
are secure and corrosion free.

Indeed, this is exactly the problem. My wifi suddenly has much weaker signal reception then before. It only functions properly within a few meters of my router. (Or any other router in a place I visit.) Further away then a few meters or with a wall in between I totally lose reception. This has not been the case before, but it started a while ago, see my earlier replies in this thread.

Regarding: checking the wireless card connections. I have checked, they look ok. I have not been able to completely reseat it, because one of the screws of my laptop casing did not come off properly. I will try that after removing that screw entirely. I am not sure whether that will work though: when I had a similar problem a few years back (see my earlier replies in this thread) it did not work. But I will try when I remove the screw.

> **Hadaka said:**
> 
#Set IPv6 to Ignore..
```
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Tommie5G'
sudo sed -i '/ipv6/{n;s/.*/method=ignore/}' /etc/NetworkManager/*/Tommie'
sudo systemctl restart network-manager.service 
```
Thanks.

I have tried this as you and Jeremy suggested, but it does not seem to make a difference. I have noticed also that the problem is not only with my home wifi network / router. It also applies to networks / routers of friends or places I visit for work. So it does not seem to be a network specific problem.

---

### Post by S. Cornelissen on 2018-03-19
> **S. Cornelissen said:**
> 
Regarding: checking the wireless card connections. I have checked, they look ok. I have not been able to completely reseat it, because one of the screws of my laptop casing did not come off properly. I will try that after removing that screw entirely. I am not sure whether that will work though: when I had a similar problem a few years back (see my earlier replies in this thread) it did not work. But I will try when I remove the screw.

I have been able to open the laptop, so I checked and re-seated my wireless card. It unfortunately gave no improvement. Connection is still very poor, while other devices can connect to the same routers without problems. While checking the card I saw no defects in the card, the antenna cables and connections. So there is no clear indication for hardware failure there.

This means I am out of options again. Any new suggestions are greatly appreciated. Thanks!

---

### Post by S. Cornelissen on 2018-05-08
Update: repair shop opened up the laptop. Conclusion: an antenna wire in the screen bezel is broken. So nothing to do with Ubuntu, purely hardware failure. Thanks to everyone for all the suggestions!

---

