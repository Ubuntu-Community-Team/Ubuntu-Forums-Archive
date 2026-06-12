---
title: "got my broadcom working, but still no net."
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by diamorph on 2008-06-12
i just installed ubuntu 8.04 on my compaq presario v6000 last night. it took me a while until i get my wireless detected/working (broadcom) - installed a couple of packages (b43-firmware, b43-fwcutter). 
now, it does detect the wireless networks, but it can't connect. 
it might be something with the network key, i can't figure it out...
any ideas, suggestions? please?

---

### Post by issih on 2008-06-12
check if the hardware is ok by disabling encryption on the network first.

N.B. if you are using wpa encryption you may want to look at installing wpa-supplicant. Can't tell you much about it, as I don't use it myself, I have a mac address filter on my setup :)

---

### Post by diamorph on 2008-06-12
> **issih said:**
> check if the hardware is ok by disabling encryption on the network first.

N.B. if you are using wpa encryption you may want to look at installing wpa-supplicant. Can't tell you much about it, as I don't use it myself, I have a mac address filter on my setup :)



can't disable the encryption.
the key works just fine on the other machines (WEP, open system)..

---

### Post by Ayuthia on 2008-06-12
> **diamorph said:**
> can't disable the encryption.
the key works just fine on the other machines (WEP, open system)..

Is the passkey in HEX?  If so, I think that network manager does not default to hex when it asks for your password so you need to select it.

---

