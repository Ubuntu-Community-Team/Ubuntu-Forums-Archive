---
title: "WiFi adapter stops responding randomly. Need help!"
date: 2020-07-25
forum: Networking &amp; Wireless
---

### Post by yesint on 2020-07-25
Dear All,
I have a problem with my trusted Asus UX305F laptop. On recent Ubuntu versions (starting from 2020) my WiFi stops working randomly: connection got lost, no wireless networks are visible. If I disable wireless or reload NetworkManager it says "no WiFi available" i.e. the adapter doesn't work any more. When I reload kernel networking modules no errors are reported but WiFi doesn't work. 

The problem got solved only after reboot (until it happens randomly again).

I can't figure out if this is software or hardware problem (the laptop is not new after all).

I tried many things suggested in similar topic but none of them produce anything useful. The problem happens on different versions of kernels and firmware. Upgrades or downgrades doesn't fix it.

Could somebody point me to the step-by-step instruction of testing my WiFi hardware?

---

### Post by kc1di on 2020-07-25
what wifi card does it have?

if you not sure go to terminal and type this command and post the result here. 
```
lspci | grep -i wireless
```

Then download and run the wireless script in my signature.

---

### Post by yesint on 2020-07-26
$ lspci | grep -i wireless
02:00.0 Network controller: Intel Corporation Wireless 7265 (rev 59)

I've also attached output of the script. I've no idea where to look at it for any hints of my problem.

---

### Post by kc1di on 2020-07-26
Have you tired turning off the Network Manager power save feature.
Go to a terminal and type the following ```
gedit admin:////etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
``` the file should look like this 
```
[connection]
wifi.powersave = 3
``` Change the 3 to 2 so it looks like this ```
[connection]
wifi.powersave = 2
```  save and reboot.  see if the wifi still drops out. 
good luck.

---

### Post by yesint on 2020-07-26
Thanks a lot! I'll try.

---

### Post by yesint on 2020-08-14
After some testing I can say that this solution works only partially. The adapter still randomly disappears but this happens less often - once per few hours (it was once per 15-20 min before). On battery power this happens much more often, so It seems that the problem is related to power saving.
Any ideas what else can I do?

---

