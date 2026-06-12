---
title: "Wireless N and Intel 4965AGN"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by mike984 on 2007-10-23
My HP Laptop has built in Intel 4965AGN and I can connect to my DLink Xtreme N DIR-655 router but it always connects using G method and does not connect using N.  Is there something I need to configure or is connecting using G as good as it gets.

thanks

---

### Post by larstorben on 2007-10-23
I have the same card and router, but Asus G1S instead of HP notebook.

I can't connect at all. Using the clean install with network-manager I can see my network, but not connect. dmesg says that association is denied (code=10) and sometimes it says that an authentication was received but that it's not in authentication mode.

I've uninstalled network-manager-gnome and network-manager and installed wicd. Same results.

iwconfig lists my wireless network just fine, as does iwlist scan.

FWIW (not much) wireless N works fine on this notebook from Vista on the other partition.

What authentication scheme are you using?


Torben

---

### Post by mike984 on 2007-11-05
I use WPA-Personal.

---

### Post by Lambert on 2007-11-05
> **mike984 said:**
> My HP Laptop has built in Intel 4965AGN and I can connect to my DLink Xtreme N DIR-655 router but it always connects using G method and does not connect using N.  Is there something I need to configure or is connecting using G as good as it gets.

thanks

The simple answer is the driver and kernel stack for wireless is currently not ready to utilize .11N standards. At somepoint in the near future you will be able to use .11N with your device. Just need to wait for the software code to mature.

If you want to to try and get it to work, you can with a few things but it's marked as expirimental and might not work. It's sort of the testing grounds to set up the code that will be merged later.
It involves instalilng a new mac80211 stack with changes, new firmware, and a possible kernel rebuild.

Not knowing your experience, I would suggest staying with .11G for now and look to a future release with the code stabilized and merged.

I have a question for you, I have a dir-655 and find my router very unstable when running in mixed mode. So I set it to .11G only for now. Do you see anything that points to problems running in the mixed mode?

---

### Post by Jimmy_r on 2007-11-28
I also have the same card and router :)

Under Ubuntu Gutsy it will not work, even after I tried upgrading mac80211, iwlwifi and iwl4965 uCode.

It works great straight from the Fedora 8 livecd though :)

These are my settings, for the record:
Setup -> Wireless settings -> Click "Manual wireless network setup" button.
I set 802.11 mode to "802.11n only" and set the channel width to "Auto 20/40 MHz".
WPA mode: WPA2 only
Cipher Type: AES
The rest are the default settings.

---

### Post by Jeff_From_VA on 2007-12-10
I have an HP dv9500t.  which has the same card.  I got horrible performance out of the linux driver for this card under gutsy. 

 I installed feisty, and used ndiswrapper and the windows driver.  I connect to my wap at 130mb, and the laptop gets the same speed on our network as my 100mb desktop does.  I can not tell I am not plugged in at all, it screams now!!!!   

I am very pleased with the results.   I had to use an older version of the windows driver, and ndiswrapper 1.43 to get it all working.   When I tried latest version of both it would not work at all.  I found a thread here [http://ubuntuforums.org/showthread.php?t=523733&highlight=dv9500t](http://ubuntuforums.org/showthread.php?t=523733&highlight=dv9500t) -- I used the same versions that that guy used, and it all worked great.   

I highly recommend it over the linux drivers at the moment.  I would prefer native support, but for me it did not work, and this did.  As soon as that driver is working right, I will switch back.

---

