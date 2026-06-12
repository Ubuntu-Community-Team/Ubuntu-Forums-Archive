---
title: "Can anyone help me translate these instructions?"
date: 2023-08-02
forum: Networking &amp; Wireless
---

### Post by wilsojeffrey on 2023-08-02
From here
[https://blog.abysm.org/2020/03/realtek-802-11ac-usb-wi-fi-linux-driver-installation/](https://blog.abysm.org/2020/03/realtek-802-11ac-usb-wi-fi-linux-driver-installation/)

to install the driver for my wifi dongle  

lsusb output for the device is

Bus 001 Device 004: ID 0bda:b812 Realtek Semiconductor Corp. 802.11ac NIC

(LTS 20.04)

---

### Post by readableauthor on 2023-08-02
[https://askubuntu.com/a/1309991/1592865](https://askubuntu.com/a/1309991/1592865)
Also, you could try installing a newer Ubuntu 23.04. It should work out of the box there as far as I know

---

### Post by chili555 on 2023-08-02
After you install the prerequisites:

```
sudo apt update
sudo apt install git build-essential bc
```

Then follow this: [https://askubuntu.com/questions/1467307/dlink-dwa-182d-wireless-adaptor-not-working-with-ubuntu-22-04-linux-kernel-5-19/1467311#1467311](https://askubuntu.com/questions/1467307/dlink-dwa-182d-wireless-adaptor-not-working-with-ubuntu-22-04-linux-kernel-5-19/1467311#1467311)

---

### Post by wilsojeffrey on 2023-08-04
That didn&#8217;t work. Went through all the steps with no errors, but the very last step asks about editing something. Click no and it just restarts and there&#8217;s still no wifi. Click yes and it takes to some editor that&#8217;s way over my head.
I&#8217;ve upgraded to 22.04. Worried about going to 23.04 because that&#8217;s a short term?
Not sure what else to do (I&#8217;m typing this on my iPad, so can&#8217;t share the screens I&#8217;m seeing). It&#8217;s connected ethernet at the moment but that&#8217;s a bit iffy with my router. Can work for days, or only hours which is why I wanted the wifi. Not spending $200 on a Panda dongle

---

### Post by wilsojeffrey on 2023-08-04
Lsusb output has changed.
now says 
Bus 001 Device 004: ID 0bda:b812 [COLOR=#000000]Realtek Semiconductor Corp. RTL88x2bu [AC1200 Techkey]

[/COLOR]

---

### Post by readableauthor on 2023-08-04
You could try loading 23.04 off the USB stick to see if wi-fi works. 23.04 is short term but updatable. You'll get 23.10 and then a new 24.04 LTS in less than a year

---

### Post by wilsojeffrey on 2023-08-04
> **readableauthor said:**
> You could try loading 23.04 off the USB stick to see if wi-fi works. 23.04 is short term but updatable. You'll get 23.10 and then a new 24.04 LTS in less than a year

You win. That worked. Installing now. Luckily only rescued this machine 2 weeks ago so didn’t have anything saved I wanted to keep, and shouldn’t take too long to get it set up back to how I want it

---

### Post by readableauthor on 2023-08-04
> **wilsojeffrey said:**
> You win. That worked. Installing now. Luckily only rescued this machine 2 weeks ago so didn’t have anything saved I wanted to keep, and shouldn’t take too long to get it set up back to how I want it

I'm glad it worked. Learned just now that soon-to-be-released 22.04.3 will have an updated kernel, so should work as well.

---

### Post by wilsojeffrey on 2023-08-04
> **readableauthor said:**
> I'm glad it worked. Learned just now that soon-to-be-released 22.04.3 will have an updated kernel, so should work as well.

Well I ain’t going backwards. Install is done. Chrome and Teams done. Mail set up. VLC going in now. Would prefer not to touch it for a while (and WIFI working!).

---

