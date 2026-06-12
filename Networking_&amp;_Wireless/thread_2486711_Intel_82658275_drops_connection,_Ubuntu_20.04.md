---
title: "Intel 8265/8275 drops connection, Ubuntu 20.04"
date: 2023-05-08
forum: Networking &amp; Wireless
---

### Post by norwayluta on 2023-05-08
[URL="https://pastebin.com/Th6SKeMn"]Here is a link, a noobie who  needs a bit of help, thank you!


https://pastebin.com/Th6SKeMn[/URL]

---

### Post by chili555 on 2023-05-09
Here is a noobie that needs a* lot* of help.

Your paste shows many attempts to solve what I believe is a simple problem. Most are, as you found out, ineffective as they do nothing to solve your issue. Let’s try to fix them. From the terminal:

```
sudo rm /etc/modprobe.d/iwlwifi-speed.conf
sudo nano /etc/modprobe.d/iwlwifi.conf

```
Remove all of these entries:

```
options iwlwifi 11n_disable=1
options iwlwifi swcrypto=1
options iwlwifi 11n_disable=8
```

Save and exit nano.

```
sudo nano .etc/rc.local
```

Remove everything, save and exit nano.

```
sudo nano /etc/netplan/01-network-manager-all.yaml
```

Revert it to its default wording:

```
network:
  version: 2
  renderer: NetworkManager
```

Save and exit netplan.

I strongly suspect that the drops are caused by your router and and its interaction with the driver and Network Manager. Your wireless may be dropping because there are two wireless access points with the same name and password. This is typical when you have a 2.4 gHz segment and a 5 gHz segment of the same router. Your wireless may be roaming, looking for a better connection. If this is the case, I suggest that you rename the access points; something like R&L2.4 and R&L5.

I recommend a fixed channel, rather than automatic channel selection. 

After making these changes, reboot the router.  

If you do not have administrative privileges to the router, bind your wireless to the 5 gHz segment by its MAC address like this: [https://askubuntu.com/questions/1192099/19-10-ubuntu-automatically-connects-to-a-weaker-wi-fi/1192112#1192112](https://askubuntu.com/questions/1192099/19-10-ubuntu-automatically-connects-to-a-weaker-wi-fi/1192112#1192112)

---

### Post by norwayluta on 2023-05-09
Thank you, I do have admin rights to the router so I will try this and report back soon!

---

### Post by norwayluta on 2023-05-09
I have no internet, when i tried sudo nano .etc/rc.local it says no such directory. I made the other changes. What next?

---

### Post by norwayluta on 2023-05-09
[COLOR=#000000]I have no internet, when i tried sudo nano .etc/rc.local it says no such directory. I made the other changes. What next?[/COLOR]

---

### Post by norwayluta on 2023-05-09
Okay, I now have wifi and have renamed one of the SSIDs. 
Are there any other changes I need to make? See the new link:

[https://pastebin.com/wcvg2keX](https://pastebin.com/wcvg2keX)

Thank you!

---

### Post by chili555 on 2023-05-10
> when i tried sudo nano .etc/rc.local it says no such directory.I'm sorry. I meant to say:

```
sudo nano /etc/rc.local
``` ...and remove everyhing and save and exit. Sorry for my mis-step.

We still see some interesting messages in the log, such as:

> Microcode SW error detected.  Restarting 0x82000000
.....
HW problem - can not stop rx aggregationHowever, as long as your wireless works well, I suggest we ignore these. If your wireless becomes intermittant, please post back and we'll look for a fix.

---

### Post by norwayluta on 2023-05-10
i made that final change and wireless is working well. Thank you very much for your assistance.

---

