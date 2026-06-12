---
title: "installing programs in VirtualBox"
date: 2010-06-01
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-06-01
OK, trying it again. Finally got a "legal" version of XP and installed that in VBox. Put in the Avast! antivirus. Installed the SonyEricsson W760 PC Suite from the disc. Also went to SE and got the updates program and installed that on VBox.

Problem. Have tried everything but cannot get the PC Suite/Updates to recognize that the phone is plugged in. 

It does show up on the Ubuntu window side (can see that by downsizing the VBox window), shows as mounted (twice) but get messages like "unable to mount" and the FStop offer to transfer the photos.

Using Ubuntu 9.10, Oracle VBox 3.2.0 r16806, installed XP Pro w/SP3 as a user in VBox.

Any suggestions on how to get this all synchro'd?

---

### Post by QIII on 2010-06-01
You are plugging the phone in with a USB cable?

---

### Post by flyfishingphil on 2010-06-01
> **QIII said:**
> You are plugging the phone in with a USB cable?
Yes. Have Toshiba Laptop 305 with 3 USB port and have tried all three. Obviously it is recognized as being connected by Ubuntu because of all that pops up. Just can't get the VBox/XP side to recognize it.

---

### Post by Zeike on 2010-06-01
> **flyfishingphil said:**
> Yes. Have Toshiba Laptop 305 with 3 USB port and have tried all three. Obviously it is recognized as being connected by Ubuntu because of all that pops up. Just can't get the VBox/XP side to recognize it.

You have to add a "USB Device Filter" in the VirtualBox settings dialog for your XP virtual machine.  If you click on the add button you should be able to pick your usb device by name.  This will tell VirtualBox to allow your virtual machine to access your usb device.

---

### Post by flyfishingphil on 2010-06-01
> **Zeike said:**
> You have to add a "USB Device Filter" in the VirtualBox settings dialog for your XP virtual machine.  If you click on the add button you should be able to pick your usb device by name.  This will tell VirtualBox to allow your virtual machine to access your usb device.
Went into Device postion of VBox and did that. Also went in to USB Device Filter and checked the SE box. Still no connection.

Noticed when I plug in the SE via USB and click on phone mode, while in Ubunutu or VBox/XP, the FStop window pops up, the "unable to mount" box pops up and there is a "Wired Network error" fader that shows up on upper right corner of screen. (Looks like the ethernet connection) Not using any form of wired network, do that WiFi. Any help hearing this?

EDIT ADD: Forgot to mention this. Even tho' there is the box that says unable to mount there are two mounts, showing SE W760 camers instead of a phone, on the Ubuntu desktop while all of this is going on.

---

### Post by tom.swartz07 on 2010-06-01
do you have OSE version of Virtualbox?

The usb support for that doesnt work. You would have to get the full version from the virtualbox website.

---

### Post by flyfishingphil on 2010-06-01
> **tom.swartz07 said:**
> do you have OSE version of Virtualbox?

The usb support for that doesnt work. You would have to get the full version from the virtualbox website.
don't think it's an OSE(What's that?) Went to VBox and downloaded and installed Oracle VBox 3.2.0 r16806. It was the one recommended there for Ubuntu 9.10.

---

### Post by tom.swartz07 on 2010-06-02
> **flyfishingphil said:**
> don't think it's an OSE(What's that?) Went to VBox and downloaded and installed Oracle VBox 3.2.0 r16806. It was the one recommended there for Ubuntu 9.10.

HAHA! yeah, if you dont know what it is, you dont have it.
OSE is the Open Source Edition of Virtualbox. 

You downloaded the official full version from vb's website, so youre all set there. It might just be that you have to set up the usb device.


Also, you had mentioned that you were a bit confused with the internet connection. the Host, IE Ubuntu, is connected with wifi, but the Client, IE XP sees the internet connection as a wired one. This is just because it doesnt have access to the wifi card directly, and is 'patched' through to the internet with a pseudo wired connection.

There is a strong distinction between the hardware on the Host and the hardware that is recognized by the Client. You just have to set up the USB connection similarly to how the internet is connected.

Ill look around and see if I could dig up the guide I used to set up USB for VB

---

### Post by flyfishingphil on 2010-06-02
> **tom.swartz07 said:**
> HAHA! yeah, if you dont know what it is, you dont have it.
OSE is the Open Source Edition of Virtualbox. 

You downloaded the official full version from vb's website, so youre all set there. It might just be that you have to set up the usb device.


Also, you had mentioned that you were a bit confused with the internet connection. the Host, IE Ubuntu, is connected with wifi, but the Client, IE XP sees the internet connection as a wired one. This is just because it doesnt have access to the wifi card directly, and is 'patched' through to the internet with a pseudo wired connection.

There is a strong distinction between the hardware on the Host and the hardware that is recognized by the Client. You just have to set up the USB connection similarly to how the internet is connected.

Ill look around and see if I could dig up the guide I used to set up USB for VB
Thanks Tom. While you're doing that I can continue to gather the info, do the malware scan and clean up my wife's Win7 laptop that's got the latest "ransomware" in it. She picked up the "AntiSpyware.Soft" that takes over the computer and screws everything up royally. Doing a malware scan on it now to get rid of it.

Funny, was just telling her that one of the benefits of Linux/Ubuntu is I have found no references to malware problems like Windough$ has. (2 of her friends just did total formats and startovers because of that malware.)

---

### Post by flyfishingphil on 2011-08-14
Consider solved. Just eliminated need for VBox with clean install of 11.04. Too many problems with VBox so gave up.

---

