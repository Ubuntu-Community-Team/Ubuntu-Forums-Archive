---
title: "Dell Latitude D600 Wireless networking problem"
date: 2008-05-11
forum: Networking &amp; Wireless
---

### Post by jsrsarc on 2008-05-11
I am using Dell Latitude D600 and this is the output from lspci |grep BCM

02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

I am loosing my wireless connection frequently. I don't have problem with wired network. While booting i am getting PHY transmission error..

Could someone help me?:confused:

---

### Post by EricMcGregor on 2008-05-13
Hi!

I have the same exact issue!

in the beginning I had wlan contact in a coulpe of hours, now it is a matter of minutes before i shuts down. Works with cable.

---

### Post by jsrsarc on 2008-05-14
I don't know why this strange behaviour. My system used to be fine with earlier versions of Ubuntu.

---

### Post by supremedalek on 2008-05-14
I have had the same problem myself when using the broadcom wireless card that came in the machine. It turned out I had to go to the bios and disable the onboard modem as it was conflicting with the wireless somehow. That said, be prepared: the broadcom speed is anything but stellar.

---

### Post by leberama on 2008-05-14
> **jsrsarc said:**
> I am using Dell Latitude D600 and this is the output from lspci |grep BCM

02:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)

I am loosing my wireless connection frequently. I don't have problem with wired network. While booting i am getting PHY transmission error..

Could someone help me?:confused:

I was getting the same error.  I set my bios POST to complete test and problem went away.

---

### Post by jsrsarc on 2008-05-15
> **leberama said:**
> I was getting the same error.  I set my bios POST to complete test and problem went away.

Hi leberama,

I am a newbee to Linux...what do you meant by "I set my bios POST to complete test"

---

### Post by EricMcGregor on 2008-05-15
Knock on wood, I disabled the internal modem in Bios and removed the wlan settings in "Wireless network" so it would load new settings.

and it has worked for a while now, but I`m not 100% sure that it works yet, I`ll have to wait a couple of hours to see if it really works :D

---

### Post by EricMcGregor on 2008-05-15
Okey it did not work :(  I got wlan for a longer time, but after an hour it died again and the network icon disappeared (?)

---

