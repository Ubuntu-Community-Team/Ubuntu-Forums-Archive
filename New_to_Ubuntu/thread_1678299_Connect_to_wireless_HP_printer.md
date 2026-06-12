---
title: "Connect to wireless HP printer"
date: 2011-01-30
forum: New to Ubuntu
---

### Post by vanbroeK on 2011-01-30
This is really bugging me. I am trying to connect to my printer which is in the office.

It's a HP Color LaserJet 2600n printer which is connected to a server type computer which is the computer that is connected to the modem and the other household printer.

When I was using windows, we were able to connect and print to this printer all the time but I cannot connect to it on ubuntu.

I've installed the hp toolbox and connected it via usb for a sec but cannot install it. I don't know exactly what im doing and I can't get the ip address of the printer either.

Please help.

---

### Post by cogier on 2011-01-30
Regarding "**It's a HP Color LaserJet 2600n printer which is connected to a server type computer**". Can you not connect the printer directly to the Router as a network printer. This way you would be able to use the printer without the "**server type computer**" being switched on.

When you say "**hp toolbox**" I presume you downloaded **HPLIP** from the **Ubuntu Software Centre**.

I have a HP Photosmart and installed it on my laptop using the **Network** option wirelessly (there was no physical connection during the setup).

Hope that helps.

---

### Post by vanbroeK on 2011-01-30
> **cogier said:**
> Regarding "**It's a HP Color LaserJet 2600n printer which is connected to a server type computer**". Can you not connect the printer directly to the Router as a network printer. This way you would be able to use the printer without the "**server type computer**" being switched on.

When you say "**hp toolbox**" I presume you downloaded **HPLIP** from the **Ubuntu Software Centre**.

I have a HP Photosmart and installed it on my laptop using the **Network** option wirelessly (there was no physical connection during the setup).

Hope that helps.

I can but this will mess up all the other window 7 laptops in the house, although I could do this.

And yes i did mean hplip just forgot the name and was in a rush. If i was to connect the printer to the modem, what would it take to reconnect all the other computers?

---

### Post by cogier on 2011-01-30
You would have to setup all the computers to see the printer as a network printer rather than USB but as you already have the Windows drivers installed it should not be too hard (but I have not done this!). 

You could plug the printer with the network cable into the router and test the change on one Windows computer to test it and also see if you can get Ubuntu to see it as well and if all fails you only have one machine to reset.

---

### Post by vanbroeK on 2011-01-30
> **cogier said:**
> You would have to setup all the computers to see the printer as a network printer rather than USB but as you already have the Windows drivers installed it should not be too hard (but I have not done this!). 

You could plug the printer with the network cable into the router and test the change on one Windows computer to test it and also see if you can get Ubuntu to see it as well and if all fails you only have one machine to reset.

Okay thanks I will try this and let you know how it goes

---

### Post by vanbroeK on 2011-01-31
Ok I obviously didn't know what I was talking about because I thought I needed to unplug it from the server computer but I just realised that I can simply put in an ethernet cord and bob's your uncle. It works and it didn't effect the other laptops. Thanks.

---

