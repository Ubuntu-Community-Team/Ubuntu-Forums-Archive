---
title: "Sharing a connection XP or Vista -&gt; Fiesty"
date: 2007-05-01
forum: Networking &amp; Wireless
---

### Post by cthom06 on 2007-05-01
Im afraid i lready know the answer, but i wanted to ask before i went out and wasted money.

Here's the setup... I have 2 Notebooks which both connect to the internet using a WWAN card and Verizon National Access (global DSL basically). 

I also have a desktop running Fiesty. 

Is there anyway to share the internet connection from either of the 2 laptops with the desktop? Or do I have to buy a crossover cable?

---

### Post by stealth17 on 2007-05-12
> **cthom06 said:**
> Im afraid i lready know the answer, but i wanted to ask before i went out and wasted money.

Here's the setup... I have 2 Notebooks which both connect to the internet using a WWAN card and Verizon National Access (global DSL basically). 

I also have a desktop running Fiesty. 

Is there anyway to share the internet connection from either of the 2 laptops with the desktop? Or do I have to buy a crossover cable?

Sure. Probably the best way (considering they are laptops) is to buy a cheap USB wireless dongle for your desktop and setup internet sharing from the laptops wireless card to your desktop. So it would be like this:

--> Internet in via PCMCIA Card --> Share to laptop's wireless card --> desktop connects to laptop with wireless

I would recommend the [Belkin Wireless G USB Adapter]("http://catalog.belkin.com/IWCatProductPage.process?Product_Id=179211"). I was worried about buying a USB card, but it turns out these things are really handy to have around. It's just a little bigger then a thumb drive, but you can carry it around and use it to hope on the internet at anytime. You can also use them to make really cool homemade antennas, check it out [here]("http://www.usbwifi.orcon.net.nz/"). For $40 you can't go wrong, and I have got mine to install and run on Ubuntu flawlessly :)

If you want to share via ethernet, you may need a crossover but it all depends on if you NIC is autosensing. If your computers are fairly new (last 2 years rough estimate) then it *should* be and autosensing NIC so a patch will work just fine. I run mine through a patch without any problems at all.

[Here]("http://ubuntuforums.org/showthread.php?t=91370") is a guide on how to get the internet sharing configured once you buy the wireless adapter.

8-)

---

