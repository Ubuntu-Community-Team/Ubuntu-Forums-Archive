---
title: "Wireless Issues with BCM4303 on Dell Inspiron 8200"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by Nrbelex on 2007-04-20
Hi, I just installed Feisty on a Dell Inspiron 8200. Everything has worked great except for my wireless card. Inside is a Dell Truemobile 1180 aka **BCM4303 **wireless card. When I use the Network Manager, **nothing is detected** though I know** two wireless networks are present** (another computer one foot away has a strong connection on one of the two and an OK connection on the other). Is there any way I can test to see if the wireless card is working? Networking is enabled and works while wired and Wireless is enabled as well. Is this card supported?

Thanks!
~ Brett

---

### Post by Nrbelex on 2007-04-20
Jordan_U on the Ubuntu IRC channel was enormously helpful. Here's what I did to solve the problem:

Install the package named "bcm43xx-fwcutter"

or run ```
sudo apt-get install bcm43xx-fwcutter
```

then either restart the computer or run 

```
sudo modprobe bcm43xx
```

Problem solved!

~ Brett

---

