---
title: "Which ADSL modems are supported 'out of the box' by Ubuntu?"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by starbase1 on 2006-10-10
IIs there a list available of which ADSL modems are supoported out of the box by Ubuntu?

It doesn't recognise my current one, but I have noticed how cheap they are, (and I was planning on moving to something faster anbyway).

Thanks,
Nick

---

### Post by Buffalo Soldier on 2006-10-10
> **starbase1 said:**
> IIs there a list available of which ADSL modems are supoported out of the box by Ubuntu?

It doesn't recognise my current one, but I have noticed how cheap they are, (and I was planning on moving to something faster anbyway).

Thanks,
NickSafest assumption:[list]
[*] Any modems that's connected to the PC using USB is not supported.
[*] Any modems that's connected to the PC using Ethernet/CAT5 is **most probably** is supported.[/list]

---

### Post by starbase1 on 2006-10-10
No usb modems? That sounds like a majopr hole in hardware support to me...

Anyway, thanks for the info.
Nick

---

### Post by rejser on 2006-10-10
I never got the idea why one would use USB-modems.....

My DSL 320T works fine dsl2+ 24mbit

---

### Post by TheWizzard on 2006-10-10
same for me. 
i started with an usb-modem & windows. couldn't get it working. neither could the technician. in the end i had to send it back. 

ethernet is perfect. OS independent. moreover, you can exteend your network easily by putting a router between the modem and the pc.

---

### Post by starbase1 on 2006-10-10
Well, I suppose I have it because the service p[provider included it in the deal originally... And looking around the computer shops, the ones on display there seemed to all be USB connected as well. I generally expect USB to be more portable I guess - hence the U in USB!
:rolleyes: 

Anyway, I found one of the DSL 320's on the web, and the price certainly seems no worse than a USB one.

But I have 2 PC's, (well, number 2 should be delivered any day now), with a 1 socket network card in each. I was planning on sticking a crossover cable between the two to network them.

Does this mean I would need a second network card for the new modem? 

Cheers, Nick

---

### Post by Buffalo Soldier on 2006-10-10
Most Ethernet-capable modems can be connected to a hub/switch. Then depending on the number of ports on the hub/switch you can connect to as many PC as you wish. The cheapest usually comes with 4 or 8 ports.

Another option is to buy a modem/router combo such as this one that I'm using -> [http://www.aztech.com/prod_adsl_dsl600er.html](http://www.aztech.com/prod_adsl_dsl600er.html)

Heck, if you something like this one -> [http://www.aztech.com/prod_adsl_dsl600ew.html](http://www.aztech.com/prod_adsl_dsl600ew.html) you're already set for wireless.

---

### Post by mips on 2006-10-10
> **starbase1 said:**
> No usb modems? That sounds like a majopr hole in hardware support to me...


Uhm, maybe but you can only blame the hardware vendors. Some USB ADSL devices use chipsets that are supported in Linux.

USB ADSL is less portable than Ethernet ADSL. Ethernet is a universal standard and no further drivers are required for the router, as long as your ethernet port works everything is ok. With USB ADSL you need a driver in order to get the device to work.

I will NEVER recommend USB ADSL to anyone, even a windows user. I always advice going with a Ethernet Router.

---

### Post by TheWizzard on 2006-10-11
> **mips said:**
> I will NEVER recommend USB ADSL to anyone, even a windows user. I always advice going with a Ethernet Router.

absolutely. stay away from usb-modems!

---

### Post by Magnes on 2006-10-11
Well, my provider for example gave me ADSL modem for free, to buy ethernet router I'll need some (for me big) amount of money.
I use ADSL modem without (big) problems though using ueagle-atm (for sagem 800). The detailed HOWTO is on this forum.

---

### Post by starbase1 on 2006-10-11
I think Magnes has it - I'm pretty sure most will take what the services provider includes...

Sorry, I don't mean to take a pop at the hardware support. It does seem to me though that with network connectivity so crucial to getting everything up and running, the widest possible modem support would be a big help in getting Ubuntu more widely adopted.

Anyway, as I said I think I might need to get a more modern modem anyway, to cope with the higher speeds that are around.  And I will certainly look for an ethernet one!

Thanks guys,
Nick

---

### Post by Buffalo Soldier on 2006-10-11
Nothing Ubuntu or any other GNU/Linux distro would want more than total hardware coverage. But unless manufacturer cooperate by giving the documentation... not much distros can do.

---

### Post by mips on 2006-10-12
> **Magnes said:**
> Well, my provider for example gave me ADSL modem for free, to buy ethernet router I'll need some (for me big) amount of money.
I use ADSL modem without (big) problems though using ueagle-atm (for sagem 800). The detailed HOWTO is on this forum.

Fair enough, I understand.

Also keep in mind that the provider usually gives you the cheapest model. If you asked/specified a ethernet router they would probably supply you one for free or at a small additional surcharge.

---

### Post by IanGB on 2006-10-12
May I just ask what I can do when I still run XP on the master drive with a USAB modem and ubuntu will not connect with it. Do I have to give up the supplied modem?

iangb

---

### Post by TheWizzard on 2006-10-13
> **IanGB said:**
> May I just ask what I can do when I still run XP on the master drive with a USAB modem and ubuntu will not connect with it. Do I have to give up the supplied modem?

iangb


1) find yourself a cheap old pc with Win2k/NT and use this as a router. 

2) check at your isp if it states that your modem is winXP only or if it supports all operationg systems. i don't know wheather it is impossible to use your usb-modem with linux or not. you'll have to do the research yourself i'm affraid because most people here won't have experience with usb-modems. 

3) start complaining at your isp. depending on where you live, there is a good chance you can trade your usb-modem for an ethernet-modem. 

4) choose a linux-friendly isp next time ;)

---

### Post by mips on 2006-10-14
> **IanGB said:**
> May I just ask what I can do when I still run XP on the master drive with a USAB modem and ubuntu will not connect with it. Do I have to give up the supplied modem?

iangb

It might work in Linux but you need to know what chipset it uses in order to determine if it will work or not.

---

