---
title: "Using the Belkin Wireless Pre-N Notebook Network Card with ubuntu"
date: 2006-09-02
forum: Networking &amp; Wireless
---

### Post by nickk on 2006-09-02
Hi,

I bought the above wireless network card for my laptop today. Im having problems installing it, been battling it all day. I installed ndiswrapper, and installed the windows drivers for the card. I know it recognizes the hardware because when the card is inserted, and I run
> 
ndiswrapper -l


It tells me:
> 
Installed ndis drivers:
netani          driver present, hardware present


And when I remove it, it doesnt say "hardware present". 
When I go to System -> Administration -> Networking, it doesnt find anything but the standard eth0 (normal NIC). Any help would be appreciated.

Thanks,
Nick

---

### Post by nickk on 2006-09-02
I'm totally lost now...
I tried doing this:
> 
sudo ndiswrapper -m


and it tells me:
> 
modprobe config already contains alias directive


When I type
> 
modprobe ndiswrapper


it tells me
> 
FATAL: Module ndiswrapper not found.


and I put "ndiswrapper" in the /etc/modules file. I'm totally lost and I really need to get this done soon, any help would be appreciated.

---

### Post by nickk on 2006-09-03
anyone?

---

### Post by JDRU on 2006-09-10
I have the same card - have you had any luck, with the installation since? posting. I would also like to get this card working with Ubuntu.

Regards,](*,)

---

