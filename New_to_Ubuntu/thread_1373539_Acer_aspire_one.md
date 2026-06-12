---
title: "Acer aspire one"
date: 2010-01-05
forum: New to Ubuntu
---

### Post by Unhubbed on 2010-01-05
[COLOR=#008000][COLOR=black]I was able to download and instal ubuntu 9.10 useing[/COLOR] [COLOR=red]_Unetbooting.com_[/COLOR] [/COLOR][COLOR=black],also I was able to install it to my computer, everything seemed ok but ubuntu wont find my wireless connecton, so i added my Belkin manualy in settings to ssid, saved restarted and still NO connectivity, CAN ANYONE HELP?[/COLOR]
 
Edit: My computer is a brand new Acer Aspire One  netbook Model D250-1842

---

### Post by spiderbatdad on 2010-01-05
Generally wireless works by default in 9.10 on AAO.
Please confirm your card is Atheros with sudo lshw -C net
You may need to edit/create the file /etc/modprobe.d/blacklist-ath_pci.conf and add the line ```
blacklist ath_pci
```

---

