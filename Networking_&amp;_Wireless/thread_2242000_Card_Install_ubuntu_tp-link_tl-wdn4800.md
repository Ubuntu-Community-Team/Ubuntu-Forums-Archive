---
title: "Card Install ubuntu tp-link tl-wdn4800"
date: 2014-08-29
forum: Networking &amp; Wireless
---

### Post by bs0d2 on 2014-08-29
Super new to ubuntu... I purchased the subject card and it doesn't work for me out-of-the-box. 

lspci -nn: 
```

5:00.0 Network Controller [0280]: Atheros Communications Inc. AR9300 Wireless LAN adaptor [168c:0030] (rev 01)

```
uname -r:
```

3.5.0-44-generic

```

I tried:
```

sudo apt-get install firmware-atheros

```

and it says package not found. 

Any help would be appreciated. It would be great if achievable without the internet. Thanks

---

### Post by chili555 on 2014-09-01
In recent Ubuntu versions, your device is covered by default by the driver ath9k:```
$ modinfo ath9k | grep 0030
<snip>
alias:          pci:v0000[COLOR="#FF0000"]168C[/COLOR]d0000[COLOR="#FF0000"]0030[/COLOR]sv*sd*bc*sc*i*

```Your kernel 3.5.0-xx is undoubtedly too old. It will be far easier for you to install 14.04 than to download all the bits and pieces and their dependencies needed to build the driver.

---

