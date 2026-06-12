---
title: "it cannot connect to wifi after changing wifi 's mac address"
date: 2020-04-19
forum: Networking &amp; Wireless
---

### Post by creatxr on 2020-04-19
it cannot connect to wifi after changing wifi 's mac address.

is here someone resolved it now?

or the new version 20.04 resolve it now?

thanks.

---

### Post by jeremy31 on 2020-04-19
Are you using a USB wifi adapter?

---

### Post by creatxr on 2020-04-19
the wifi adapter is integrated with my laptop.

i 've tried with macchanger, ifconfig, network-manager, ip link set dev xxx address xx:xx:xx:.......,


i 've read the topics. 

but i am never success connecting to wifi after change the mac address.

it seems that many people ask for that, i don't know if someone resolved it now?

---

### Post by CelticWarrior on 2020-04-19
Forget the old connection/profile and reconnect.

---

### Post by creatxr on 2020-04-19
> **CelticWarrior said:**
> Forget the old connection/profile and reconnect.


i dont understand. what's means "forget the old connection"?

if i delete the old network connection in the panel and reconnect by choose ssid in the list,

it will use the original mac address, not the random mac address which i set in "cloned mac address" .

---

### Post by CelticWarrior on 2020-04-19
Yes, that's what I meant. Why do you think you need to change the MAC address?

---

### Post by creatxr on 2020-04-19
> **CelticWarrior said:**
> Yes, that's what I meant. Why do you think you need to change the MAC address?

1)

what's the solution to change mac?

---

### Post by kurt18947 on 2020-04-19
You should be able to edit/delete connections using this command. Press alt-F2 to open a window then type this:
```
nm-connection-editor
```
You can delete saved connections and re-connect.

---

