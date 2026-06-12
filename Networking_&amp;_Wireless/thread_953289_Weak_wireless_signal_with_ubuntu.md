---
title: "Weak wireless signal with ubuntu"
date: 2008-10-20
forum: Networking &amp; Wireless
---

### Post by Japh on 2008-10-20
Hallo all,

I've noticed that using Ubuntu 8.04 on my laptop(dell) and desktop(HP) I've needed to start using a wireless adapter just to catch the wireless signal in my house, but this is if I'm lucky to get the signal at all. However when I get on my windows partition on my laptop I've got a perfect signal.

Has anyone else had/noticed this issue? If so then have you been able to resolve the issue?

---

### Post by dracule on 2008-10-20
> **Japh said:**
> Hallo all,

I've noticed that using Ubuntu 8.04 on my laptop(dell) and desktop(HP) I've needed to start using a wireless adapter just to catch the wireless signal in my house, but this is if I'm lucky to get the signal at all. However when I get on my windows partition on my laptop I've got a perfect signal.

Has anyone else had/noticed this issue? If so then have you been able to resolve the issue?

yeah, weak wireless forced me to stop using Ubuntu. 

I REALLY REALLY want ubuntu back, but 30kbps and 999ms pings dont cut it when in windows i get around 20 mbps and 4ms pings.

---

### Post by bionnaki on 2008-10-20
what adapter and drivers are you using? perhaps you should use one that's more linux friendly..?

---

### Post by Japh on 2008-10-20
On the Dell laptop(inspiron e1505) it's a broadcom43xx wireless card, notorious for being a pain but it works decently if I'm up close to the wireless router.

On my HP pavilion slimline I've got an RALink usb wireless lan card. Same issue with linux where if I'm a bit "too far away"(less than 30 feet) then it wont connect as easily as windows would.

On the dell, windows picks up and connects to my wireless network perfectly but with linux I need to use a Linksys compact wireless-G USB wireless adapter. I've got my linksys router setup to only broadcast in G.

On the HP it's the same issue however it doesn't have windows vista on it anymore but it connected to the wireless network without a problem when vista existed on the machine.

---

### Post by kreggz on 2008-10-20
Hi,

The Broadcom drivers in Hardy were written by the community, they did a pretty good job with what they had. Broadcom didn't realise drivers at the time.

Broadcom have now kindly provided drivers which have been included in Intrepid. They work a lot better than the Hardy drivers.
[http://blogs.computerworld.com/new_linux_broadcom_wi_fi_drivers_arrive](http://blogs.computerworld.com/new_linux_broadcom_wi_fi_drivers_arrive)

Intrepid comes out in a week or too, maybe give it a try!

---

### Post by Ayuthia on 2008-10-20
> **kreggz said:**
> Hi,

The Broadcom drivers in Hardy were written by the community, they did a pretty good job with what they had. Broadcom didn't realise drivers at the time.

Broadcom have now kindly provided drivers which have been included in Intrepid. They work a lot better than the Hardy drivers.
[http://blogs.computerworld.com/new_linux_broadcom_wi_fi_drivers_arrive](http://blogs.computerworld.com/new_linux_broadcom_wi_fi_drivers_arrive)

Intrepid comes out in a week or too, maybe give it a try!

Actually, the Broadcom STA driver (wl) is now included in the most updated versions of Hardy (kernel 2.6.24-21).  However the driver only works for the 4311, 4312, 4322, 4328 cards (regardless of kernel version).

---

### Post by Japh on 2008-10-20
@kreggz: I realize there is a fix and I've already stated that my broadcom card on my laptop works decently if I'm close enough to the wireless router. The issue is the signal strength if I'm "too far away"(a bit more than 15 feet away).

---

### Post by kreggz on 2008-10-24
Hi,

What I was trying to say is that the driver may affect the performance of the wireless. I have noticed that the performance of the newer driver is better in Intrepid. :)

cheers,

---

### Post by jcbk on 2008-10-25
> The Broadcom drivers in Hardy were written by the community, they did a pretty good job with what they had. Broadcom didn't realise drivers at the time.

What is the state of the intel WM3945 card's driver I suspect I have the same problem, but it's hard to tell (since rebooting is necessary for switching systems)?

---

### Post by sonicb00m on 2008-10-25
I have the same weak signal problem with a dlink g122 i think it is.

---

### Post by afeasfaerw23231233 on 2009-03-11
I have this problem of my build-in Realtek 8187 wireless lan card too. In windows the siganl is great even I am in my neigbour's house. But in Ubuntu it will be broken when I walk 3 metres away from the router, making the wlan completely useless. I am really frustrated with the wireless connection in Ubuntu!!!

EDIT: I am using ndiswrapper at the moment. Neither the native driver from Ubuntu or ndiswrapper (win 98 driver) have good signal and performance. The native driver is even worse that if an extra letter isn't suffix to the ESSID the connection will be broken in high traffic.

---

