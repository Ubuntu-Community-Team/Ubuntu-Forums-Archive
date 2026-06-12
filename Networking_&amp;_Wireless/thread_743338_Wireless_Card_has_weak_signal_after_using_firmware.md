---
title: "Wireless Card has weak signal after using firmware - please help"
date: 2008-04-02
forum: Networking &amp; Wireless
---

### Post by dunnthetown on 2008-04-02
How do you get your wireless card to work as if it were on Windows? I went ahead an installed Ndiswrapper and then downloaded the driver of my Wireless card from the Dell website, extracted and installed the driver to Ndiswrapper, but it won't show wireless networks in my area. I am using the internet via Ethernet cord. Do you have to blacklist / modprobe the broadcom driver? All I want is for my wireless card to have a strong signal so I can use the internet on my college campus or at a cafe. Maybe there is a step that I missed. I went ahead an fed the driver information to memory, after having to install Ndiswrapper from the source because there is a bug where the source does not get compiled when you install ndiswrapper from Synaptic. Please help me. I included a picture so you know that I have the driver installed. Thanks a lot.

 

[IMG]http://img137.imageshack.us/img137/2438/screenshotbm8.png[/IMG]

---

### Post by Ripfox on 2008-04-02
Start over and try this...[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice#head-f744e28e6c78eb83d22be77819b130016a8e51f3](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_rev_01_(ndiswrapper)?highlight=(WifiDocs%2FDevice#head-f744e28e6c78eb83d22be77819b130016a8e51f3)

---

### Post by dunnthetown on 2008-04-02
Ok, but how do I get my wireless card to have a strong signal?

---

### Post by Ripfox on 2008-04-02
Which version of Ubuntu are you using? Did you try the firmware for broadcom wireless?

---

### Post by dunnthetown on 2008-04-03
> **ripfox said:**
> Which version of Ubuntu are you using? Did you try the firmware for broadcom wireless?

I am using Gutsy Gibbon. I am using the firmware for Broadcom right now, but the signal only goes to two bars inside my house, and when I go to college, it won't connect to the school's network because the signal is too weak.

---

### Post by kutjara on 2008-04-03
> **dunnthetown said:**
> How do you get your wireless card to work as if it were on Windows? I went ahead an installed Ndiswrapper and then downloaded the driver of my Wireless card from the Dell website, extracted and installed the driver to Ndiswrapper, but it won't show wireless networks in my area. I am using the internet via Ethernet cord. Do you have to blacklist / modprobe the broadcom driver? All I want is for my wireless card to have a strong signal so I can use the internet on my college campus or at a cafe. Maybe there is a step that I missed. I went ahead an fed the driver information to memory, after having to install Ndiswrapper from the source because there is a bug where the source does not get compiled when you install ndiswrapper from Synaptic. Please help me. I included a picture so you know that I have the driver installed. Thanks a lot.


I generally find that wireless performance under Linux using ndiswrapper (and madwifi) is significantly weaker than under Windows. This has been true of every laptop I've used since about 2002. It just seems to be a result of the open source solutions not being able to squeeze every drop of performance out of the cards yet.

---

