---
title: "Wireless suddenly ceased to work"
date: 2016-05-08
forum: Networking &amp; Wireless
---

### Post by someone2353 on 2016-05-08
[COLOR=#111111][FONT=Ubuntu]Until recently my wifi worked fine, but suddenly it ceased to connect to the wifi network. I can see the network on the wifi list but the connection fails. I'm pretty sure it's not a hardware issue, because when I do the same in windows (I have dual boot), everything works fine.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Does anyone have any idea how to solve the problem?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]You can find my wireless info [here]("http://pastie.org/private/womfogvzuahb2qh9g0na").[/FONT][/COLOR]

---

### Post by afz12 on 2016-05-09
Hi someone2353

I have the same problem on a HP Envy notebook, running Ubuntu 16.04 and Mint Cinnamon 17.3. The internal WiFi modem disappears but sometimes it works for no reason. It seems to sometimes work on one OS then not the other, but it is not reliable in being unreliable. I don't think it's a hardware fault as it goes well when it goes! When it stops it doesn't see any networks. However Ethernet works fine, also my wireless mouse works. I plugged in a TP-Link 721 WiFi modem and it works but is deaf (no drivers installed but it still works). I suspect something in Ubuntu 16.04 OS is the culprit and somehow infects my other OS after dual boot. Is this possible? 

I guess the WiFi card could have a faulty contact but this would only show up if I move the notebook - there is no obvious change with moving it and when stationary, the WiFi link is still unreliable.

Are there any Linux commands I can use to diagnose the internal modem? Also are there any good diagnostic / repair applications I could download - the software centre seems a bit light on these

Any suggestions are welcome:D - if all else fails I don't mind trying a USB modem - the TP-821 series seems quite inexpensive and its "Linux driver" might work on this machine (however its PDF installation guide assumes older versions)

---

### Post by praseodym on 2016-05-09
@someone2353:

Add the nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
``` 

@afz12: Please open a new topic showing the wireless-script outputs

---

### Post by someone2353 on 2016-05-10
> **praseodym said:**
> @someone2353:

Add the nameservers:
```

echo -e "nameserver 8.8.8.8\nnameserver 8.8.4.4" | sudo tee -a /etc/resolv.conf
sudo service network-manager restart
``` 

@afz12: Please open a new topic showing the wireless-script outputs

It didn't help.

---

### Post by RobGoss on 2016-05-10
> **someone2353 said:**
> [COLOR=#111111][FONT=Ubuntu]Until recently my wifi worked fine, but suddenly it ceased to connect to the wifi network. I can see the network on the wifi list but the connection fails. I'm pretty sure it's not a hardware issue, because when I do the same in windows (I have dual boot), everything works fine.[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]Does anyone have any idea how to solve the problem?[/FONT][/COLOR]
[COLOR=#111111][FONT=Ubuntu]You can find my wireless info [here]("http://pastie.org/private/womfogvzuahb2qh9g0na").[/FONT][/COLOR]

Hello and welcome to the forum, Sometimes I have found using my own **Wireless router **that my signal would drop quite often more them I wanted it to, I would have to reset it in order to get it working again

Try to reset your router by unpluging it for about 10 seconds then plug it back in and see how it work after that. it's worth a try

---

### Post by him610 on 2016-05-10
@praseodym

> nameserver 8.8.8.8\nnameserver 8.8.4.4

shouldn't it read

> nameserver 8.8.8.8\nameserver 8.8.4.4

---

### Post by him610 on 2016-05-10
Not an expert, but try this...

Set your router wireless security to WPA2-PSK[AES]

and this... (substitute IS for your region/country code) - a temporary fix
```
sudo reg set IS
``` 

make it permanent with your favorite editor

```
sudo nano /etc/default/crda
```

# edit last line to read...  *REGDOMAIN=IS*

# review, save, reboot - better?

---

