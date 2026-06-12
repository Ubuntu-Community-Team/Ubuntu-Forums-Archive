---
title: "Compatibles Usb Ac wifi dongle"
date: 2023-07-04
forum: Networking &amp; Wireless
---

### Post by ckrles on 2023-07-04
Hi. My mother has a laptop with an internal wifi card which is hardly getting 6-10mbps. It runs ubuntu 22.04lts. It's a M.2 wifi N capable and the chipset is 2.4ghz (chipset?) Insuspect 150mbps. Her connection is fiber 300mbps. I do not intend to get that much (it would be great though), but it would be great to have at least 50mbps for flawless web surfing. I was looking at some usb ac wifi dongles, but all seem to be incompatible or troublesome after updates with ubuntu. Any budget recommendations on how to improve its poor 6-10mbps?

Thank you very much.

---

### Post by jeremy31 on 2023-07-04
Moved to Networking, see the wireless script link in my signature and post results

---

### Post by morrownr on 2023-07-04
USB-WiFi

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

Read menu item 1 and then take a look at menu item 2. You can post question in Issues.

There are many good quality usb wifi adapters available. 

The above link is also in the top pinned message.

---

### Post by ian-weisser on 2023-07-05
> **ckrles said:**
> Any budget recommendations on how to improve its poor 6-10mbps?

Lots of troubleshooting you can do for free.

Have you checked that the laptop is using the correct kernel module?

Is the wireless side of the access point fully capable? Have you checked the access point settings to be sure it's not intentionally degraded? Do other devices works fast?

Is the laptop in a wireless dead zone? Or behind wireless-opaque walls? Does moving the laptop close to the access point improve performance?

---

### Post by ckrles on 2023-07-05
> **ian-weisser said:**
> Lots of troubleshooting you can do for free.

Have you checked that the laptop is using the correct kernel module?

Is the wireless side of the access point fully capable? Have you checked the access point settings to be sure it's not intentionally degraded? Do other devices works fast?

Is the laptop in a wireless dead zone? Or behind wireless-opaque walls? Does moving the laptop close to the access point improve performance?

As for troubleshooting, the pc (I don't know why I wrote laptop) has a win10-ubuntu 22.04 dual boot. Windows gives the same or a slightly lower speed. So, it doesn't seem to be the OS. Both SO are fresh installs. As for the router, it seems to be ok in terms of wifi speed. I tested speed at the same location, by the pc, with my android phone and got 35mbps in 2.4ghz and 210mbps in 5ghz.

That leads me into believing it's a hardware issue, where the integrated m.2 wifi card gets a poor signal or is limited to a low speed.

At home I've got an old alfa 54gb wireless usb card lying around. I may give it a try, buy if possible, I'd like to get a budget ac wifi card, at least 600mbps.

---

### Post by morrownr on 2023-07-05
> I'd like to get a budget ac wifi card, at least 600mbps.

You say card but I thought you previously said usb adapter. There are internal cards and external usb adapters?

I'm going to go with usb adapter that is AC600 class:

The following adapter gets good review (it is a model I don't have). It is single-state, single-function and runs with an in-kernel (Plug and Play) driver. Those are all characteristics you want for a troubles-free experience.

[https://www.amazon.com/dp/B08NPX2X4Z/?tag=pandaw-20](https://www.amazon.com/dp/B08NPX2X4Z/?tag=pandaw-20)

The full Plug and Play list is location at:

[https://github.com/morrownr/USB-WiFi/blob/main/home/USB_WiFi_Adapters_that_are_supported_with_Linux_in-kernel_drivers.md](https://github.com/morrownr/USB-WiFi/blob/main/home/USB_WiFi_Adapters_that_are_supported_with_Linux_in-kernel_drivers.md)

The Main Site is located at:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

USB-WiFi gets over 1000 hits per day with the overall site getting over 2000 hits per day. I say this so that you understand that the sites I am linking are heavily used with the information and adapters being checked by Linux users around the world everyday.

---

### Post by ckrles on 2023-07-06
> **morrownr said:**
> > I'd like to get a budget ac wifi card, at least 600mbps.

You say card but I thought you previously said usb adapter. There are internal cards and external usb adapters?

I'm going to go with usb adapter that is AC600 class:

The following adapter gets good review (it is a model I don't have). It is single-state, single-function and runs with an in-kernel (Plug and Play) driver. Those are all characteristics you want for a troubles-free experience.

[https://www.amazon.com/dp/B08NPX2X4Z/?tag=pandaw-20](https://www.amazon.com/dp/B08NPX2X4Z/?tag=pandaw-20)

The full Plug and Play list is location at:

[https://github.com/morrownr/USB-WiFi/blob/main/home/USB_WiFi_Adapters_that_are_supported_with_Linux_in-kernel_drivers.md](https://github.com/morrownr/USB-WiFi/blob/main/home/USB_WiFi_Adapters_that_are_supported_with_Linux_in-kernel_drivers.md)

The Main Site is located at:

[https://github.com/morrownr/USB-WiFi](https://github.com/morrownr/USB-WiFi)

USB-WiFi gets over 1000 hits per day with the overall site getting over 2000 hits per day. I say this so that you understand that the sites I am linking are heavily used with the information and adapters being checked by Linux users around the world everyday.

I don't know why I said "card". I meant a wifi usb adapter.
I have visited those links you posted. Wonderful information. I didn't how rough it was to find a decent ac wifi adapter. The links have been very useful. I finally ordered [https://www.amazon.es/Brostrend-Adaptador-escritorio-computadora-AC1L/dp/B07FCNP2VL/](https://www.amazon.es/Brostrend-Adaptador-escritorio-computadora-AC1L/dp/B07FCNP2VL/)
I think it's not on the list, but it's highly rated, the description indicates that it's Linux compatible and comments from other customers indicate the same. It's not exactly Plug& Play. It requires a driver, which, from what I understood, is basically a couple of commandlines in the terminal. I might have read that a .deb package is available.
I haven't tried it yet and I won't know until I try, so I may be wrong.

---

### Post by morrownr on 2023-07-08
You can go ahead and install the driver while you wait for the adapter:


[https://github.com/morrownr/88x2bu-20210702](https://github.com/morrownr/88x2bu-20210702)


Once you upgrade to Ubuntu 23.10 or later, you should be able to remove the out-of-kernel driver and use the in-kernel driver.

---

