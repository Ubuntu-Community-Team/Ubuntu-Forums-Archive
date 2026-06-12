---
title: "slow internet"
date: 2015-10-12
forum: Networking &amp; Wireless
---

### Post by Amir_P on 2015-10-12
hey
im new to ubuntu and i am learning it just for 5,6 days
i have trrebble internet speed in ubuntu. my download speed in windows is about 300-400kbps but in ubuntu with terminal and firefox its ~10kbps
how to fix it?

---

### Post by Amir_P on 2015-10-13
upppppp

---

### Post by sandyd on 2015-10-14
Hi, is this over Wifi or Wired?

---

### Post by mimran on 2015-10-14
I had a similar problem where it was extremely difficult to connect wireless and when it did connect, it was very slow. I found my  solution by disabling wireless-n in Terminal:

  > $ sudo rmmod -f iwlwifi
$ sudo modprobe iwlwifi 11n_disable=1
  If this fix works for you, then make it permanent:
  > $ gksudo gedit /etc/modprobe.d/iwlwifi.conf
  and add this line to the file:
  > options iwlwifi 11n_disable=1


---

### Post by Amir_P on 2015-10-17
> **sandyd said:**
> Hi, is this over Wifi or Wired?
over wifi

---

### Post by Amir_P on 2015-10-17
> **mimran said:**
> I had a similar problem where it was extremely difficult to connect wireless and when it did connect, it was very slow. I found my  solution by disabling wireless-n in Terminal:

    If this fix works for you, then make it permanent:
    and add this line to the file:
i will try thanks

---

### Post by slickymaster on 2015-10-17
*Moved to the ***Networking & Wireless*** sub-forum*

---

