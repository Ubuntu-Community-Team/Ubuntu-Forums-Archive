---
title: "Shared Network Keys."
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by methodmanrdm on 2008-05-06
ok, i have a wireless network setup with a WEP encryption.

and i have no problem entering the password, nor do i have a problem finding the network.

my problem IS, however, that the shared network key i have it setup on is on Shared Key 2 instead of the default 1.

is there anywhere/anyway to change this?

ive been searching for some time now, n have been having to use my neighbors unprotected, which im sure he doesnt appreciate haha.

---

### Post by jhursh on 2008-05-06
I am having the same problem, hopefully we will find this soon, I am using a wired connection.

Jim

---

### Post by chili555 on 2008-05-06
sudo iwconfig eth1 key [2] 0123456789

Substitute your detals, of course. Not really Network Manager friendly. If you have a computer that stays home, you can turn off Roaming and put your details in */etc/network/interfaces.*

---

### Post by methodmanrdm on 2008-05-07
i think im missing something out of this man.

i enter it. try connecting to that network (instead of the default unprotected one) and it just keeps searchin and then goes back to the unprotected one?

also, i tried turning off roaming, and that made it stop switchin back, however it still didnt connect to my home network.

---

### Post by chili555 on 2008-05-08
Please turn off roaming. Then do:```
sudo iwconfig eth1 essid <ur_essid>
sudo iwconfig eth1 key [2] 0123456789
sudo dhclient eth1
```I don't know a way to use Network Manager, the little whirling icon, to specify key 2. I don't know if there even is a way with NM.

Let us know.

---

### Post by methodmanrdm on 2008-05-11
k. well i did all of those.

n everything works fine up until the last one.

the dhclient.

it reads off all the ports n whatnot n gives me this:

No DHCPOFFERS received.
No working leases in persistent database - sleeping.

---

### Post by chili555 on 2008-05-11
Please try this instead:```
sudo iwconfig eth1 essid <ur_essid>
sudo iwconfig eth1 key [2] 0123456789 **restricted**
sudo dhclient eth1
```Substitute your details. Let us know.

---

