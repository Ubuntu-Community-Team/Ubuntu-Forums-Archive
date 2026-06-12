---
title: "Zerbronics Wi-Fi adapter is not getting detected Ubuntu18.04 in JeTson nano"
date: 2022-08-09
forum: Networking &amp; Wireless
---

### Post by eldho1416 on 2022-08-09
Hi Everyone, 

I have been testing my new jetson nano board and was trying to connect it to internet using Zebronics USB adapter([https://www.amazon.in/Zebronics-ZEB-USB150WF-WiFi-Adapter-Driver/dp/B07HRS1GYX](https://www.amazon.in/Zebronics-ZEB-USB150WF-WiFi-Adapter-Driver/dp/B07HRS1GYX)) which I have and the problem is it is not getting detected in the Jetson Board neither I could find any drivers related to it.

So, I request someone to help me with this.

Thank you

---

### Post by TheFu on 2022-08-10
18.04 support ends in April after 5 yrs.  Is it really worth the effort to try to get it working?  If it were me, I'd move to 20.04 ASAP and see if the newer kernel, which supports newer hardware, doesn't "just work".  New hardware is the enemy of all Linux systems.  If a NIC is less than 1 yr old (the chips aren't widely used), then avoid those chips.

You can use lshw and lspci and lsusb to get more details about the adapter.  Nobody can help without that information, since a brand often changes which chips are used even if they don't change the marketed name of a device.

Plus, very few people will have a JeTson, making the exact setup even less likely for someone else to reproduce.

---

### Post by eldho1416 on 2022-08-10
Hi Fu,

I got the wifi adapter working also I wish I could install ubuntu 20.04 in Jetson but it is not supported yet.

FYI: I'm using Jetson Nano

---

### Post by TheFu on 2022-08-11
The best way to help the community is this:

a) mark a threat SOLVED using the "Thread Tools" button (this helps people seeking answers and doesn't waste the time of others)
b) describe the solution and steps so that someone else can follow to achieve the same results that you did.

Please.

---

### Post by coffeecat on 2022-08-12
Not a chat thread.

*Moved to the **Networking & Wireless** support forum.*

---

