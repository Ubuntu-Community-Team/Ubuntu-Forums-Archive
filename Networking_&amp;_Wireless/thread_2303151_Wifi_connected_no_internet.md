---
title: "Wifi connected no internet"
date: 2015-11-16
forum: Networking &amp; Wireless
---

### Post by robert1826 on 2015-11-16
[COLOR=#111111][FONT=Ubuntu]I have used ubuntu 14.04 lts for quite some time now and i find it pretty cool ... but now i cannot access internet through wifi despite of being connected to a network. i tried editing /etc/pm/power.d/wireless file but no success. currently i want my internet access back please help. thx in advance.[/FONT][/COLOR]

---

### Post by praseodym on 2015-11-16
Please run the wireless-script from the sticky thread and show the outputs

---

### Post by robert1826 on 2015-11-16
here is the output when i run wireless-info: [http://pastebin.com/dN3C9ZJw](http://pastebin.com/dN3C9ZJw)

---

### Post by Hadaka on 2015-11-16
hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe bcma
```
then do..
```
sudo iw reg set EG
sudo sed -i 's/^REG.*=$/&EG/' /etc/default/crda
```
boot
then..access your router and remove the space between "my wifi"
perhaps my_wifi , as blank spaces in ssid names can cause issues,
also you currently are using a setting TKIP please change that to wpa2 only
no tkip.
boot and test wifi

---

### Post by robert1826 on 2015-11-16
hi hadaka ... i forgot to mention that i used the same wifi network with the ssid and password to access the internet on the same laptop before .. it suddenly didn't work ... should i continue with the steps you mentioned or that might change something ?

---

### Post by Hadaka on 2015-11-16
hi, changing the TKIP setting will have no effect on the computer for logging in
changing the my wifi ssid....will...so either dont change it or change it in the router
and the computer wifi configuration

---

### Post by robert1826 on 2015-11-16
so i should do the commands first ? ok ... and sorry for being a newbie but how to change the TKIP setting ?

---

### Post by robert1826 on 2015-11-16
never mind my last question ... executing the command without change neither the ssid or the TKIP worked perfectly :D :D ... thanks very much :D

---

### Post by Hadaka on 2015-11-16
ok,if you are happy so am I.  please take the time to mark this
thread solved by clicking the tools at the upper right of this thread
and mark solved.
thanks.

---

