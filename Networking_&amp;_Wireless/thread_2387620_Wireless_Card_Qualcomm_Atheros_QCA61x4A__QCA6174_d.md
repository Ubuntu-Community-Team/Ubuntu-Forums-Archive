---
title: "Wireless Card Qualcomm Atheros QCA61x4A / QCA6174 device not found"
date: 2018-03-21
forum: Networking &amp; Wireless
---

### Post by andreas.2 on 2018-03-21
Dear Community,

my Qualcomm Atheros QCA61x4 doesn't work with xubuntu 16.04.
My device is a Acer Aspire V15 Nitro (VN7-571G) Notebook.

I've been trying it for some time now but none of the solutions worked so far. 
I know there were some threads about it already, like 
[https://ubuntuforums.org/showthread.php?t=2323812](https://ubuntuforums.org/showthread.php?t=2323812)
But i had no success.
The Network panel displays: Device not found.

The card is working on Windows.

The Wireless-info tool output is here: 
[https://pastebin.com/C4zayeUf](https://pastebin.com/C4zayeUf)

Thanks very much in advance.

Andreas

---

### Post by jeremy31 on 2018-03-21
Welcome to the forums.  I would open terminal and paste ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Shutdown the computer, then power it on

---

### Post by andreas.2 on 2018-03-21
> **jeremy31 said:**
> Welcome to the forums.  I would open terminal and paste ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Shutdown the computer, then power it on

Hello Jeremy, thanks for the quick reply.

Sadly this doesn't change the problem. 
A new paste:
[https://pastebin.com/aSX6GbsS](https://pastebin.com/aSX6GbsS)

---

### Post by jeremy31 on 2018-03-21
I would power it off, remove bottom cover, then remove and reinstall the wifi card as the script results show what I think is a faulty card or bad connection to the motherboard

---

### Post by andreas.2 on 2018-03-21
> **jeremy31 said:**
> I would power it off, remove bottom cover, then remove and reinstall the wifi card as the script results show what I think is a faulty card or bad connection to the motherboard

That sounds very drastic and i'd like not to open the whole back because there is no maintenance hatch.
Like i said in #1, the card is working with Windows.

Maybe i'll try it later, but other ideas are very welcome..

---

### Post by jeremy31 on 2018-03-21
Did the wifi work during install?

---

### Post by andreas.2 on 2018-03-21
> **jeremy31 said:**
> Did the wifi work during install?

No the Wifi card did not work during install.
I used network cable to apt update & upgrade.

---

### Post by jeremy31 on 2018-03-21
Can you download the Ubuntu 17.10.1 ISO and see if that works without installing it?

---

### Post by andreas.2 on 2018-03-21
> **jeremy31 said:**
> Can you download the Ubuntu 17.10.1 ISO and see if that works without installing it?

I remember it trying before but i did it again, same issue. Wifi Unavailable.

[https://pastebin.com/p1cvx2ZJ](https://pastebin.com/p1cvx2ZJ)

Thank you very much for your efforts.

---

### Post by jeremy31 on 2018-03-21
Post results from 16.04 for ```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

---

### Post by andreas.2 on 2018-03-21
> **jeremy31 said:**
> Welcome to the forums.  I would open terminal and paste ```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
```
Shutdown the computer, then power it on

> **jeremy31 said:**
> Post results from 16.04 for ```
cat /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```

The output is:
```
[connection]
wifi.powersave = 2
```

---

### Post by jeremy31 on 2018-03-21
I was looking at the results from the second time you ran the script and noticed wifi power management was enabled.
We could try unloading the module and reload it to see if it functions then
```
sudo modprobe -r ath10k_pci && sleep 10 && sudo modprobe ath10k_pci
```

---

### Post by andreas.2 on 2018-03-21
> **jeremy31 said:**
> I was looking at the results from the second time you ran the script and noticed wifi power management was enabled.
We could try unloading the module and reload it to see if it functions then
```
sudo modprobe -r ath10k_pci && sleep 10 && sudo modprobe ath10k_pci
```


This didn't work and when it should have reloaded the module, the Wifi menu didn't come back at all.

wireless-info output, probably not relevant: [https://pastebin.com/222jAkRP](https://pastebin.com/222jAkRP)

dmesg: [https://pastebin.com/3DTjaVC6](https://pastebin.com/3DTjaVC6)

---

### Post by jeremy31 on 2018-03-21
Take a look at [https://ubuntuforums.org/showthread.php?t=1011078](https://ubuntuforums.org/showthread.php?t=1011078) and file a bug report against package linux.  I am not sure what is happening but it is not normal

---

### Post by andreas.2 on 2018-04-25
Hello,

i finally opened the notebook and replaced that crappy Qualcomm Atheros card with another card: Intel 7265. 
Finally i can enjoy xubuntu on my device. Thanks for your help jeremy31!

---

