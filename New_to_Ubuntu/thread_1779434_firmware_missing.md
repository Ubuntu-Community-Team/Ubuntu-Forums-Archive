---
title: "firmware missing ?"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by hookitup on 2011-06-10
i installed ubuntu 11.04 on my dell inspiron 5160 and when i try to connect to wireless i see the wireless network greyed out and a message below saying firmware missing, can anybody help, i know its wireless capable because when i had XP on it the wireless worked. do i have to download firmware and where to find it or what can i do ?? oh and i have also tryed doing the system > administration > addition driver> and it didnt come up with anything for wireless. and all updates are downloaded as well., and i reinstalled just to make sure something wasn't wrong with the installation and in the BIOS the wireless is on. only error i got while installing was my hardware doesn't support unity but that has nothing to do with wireless. so some help would be great.

thanks in advance

---

### Post by hhh on 2011-06-10
Run lspci -v in a terminal. Look for something like "02:0d.0 Network controller: (Manufacturers Name) Wireless PCI Adapter" and post that paragraph back here.

---

### Post by wildmanne39 on 2011-06-10
> **hookitup said:**
> i installed ubuntu 11.04 on my dell inspiron 5160 and when i try to connect to wireless i see the wireless network greyed out and a message below saying firmware missing, can anybody help, i know its wireless capable because when i had XP on it the wireless worked. do i have to download firmware and where to find it or what can i do ?? oh and i have also tryed doing the system > administration > addition driver> and it didnt come up with anything for wireless. and all updates are downloaded as well., and i reinstalled just to make sure something wasn't wrong with the installation and in the BIOS the wireless is on. only error i got while installing was my hardware doesn't support unity but that has nothing to do with wireless. so some help would be great.

thanks in advance
Hi, start by going into the additional drivers folder and see if there is a driver for your wireless card if so enable it, then restart and put in your wireless password. Open dash and type add and it will bring up additional drivers then click on it.

---

### Post by wildmanne39 on 2011-06-10
> **hookitup said:**
> i installed ubuntu 11.04 on my dell inspiron 5160 and when i try to connect to wireless i see the wireless network greyed out and a message below saying firmware missing, can anybody help, i know its wireless capable because when i had XP on it the wireless worked. do i have to download firmware and where to find it or what can i do ?? oh and i have also tryed doing the system > administration > addition driver> and it didnt come up with anything for wireless. and all updates are downloaded as well., and i reinstalled just to make sure something wasn't wrong with the installation and in the BIOS the wireless is on. only error i got while installing was my hardware doesn't support unity but that has nothing to do with wireless. so some help would be great.

thanks in advance
Hi, sorry I did not see earlier that you had already looked in additional drivers. Run this in a terminal and 
```
lspci
```  post it back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by hhh on 2011-06-10
@wildmanne, thanks for posting the same thing I did. That's awesome.

---

### Post by wildmanne39 on 2011-06-10
> **hhh said:**
> @wildmanne, thanks for posting the same thing I did. That's awesome.
Hi, sorry I did not see the last part where you told him to post back here, I thought you just told him where to look, my fault.

---

### Post by hookitup on 2011-06-10
got it working from the link provided , thanks.

---

### Post by hhh on 2011-06-10
No problem, wildmanne, thanks for the apology.

hookitup, nicely done.

---

