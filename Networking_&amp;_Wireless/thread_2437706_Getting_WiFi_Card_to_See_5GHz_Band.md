---
title: "Getting WiFi Card to See 5GHz Band"
date: 2020-02-28
forum: Networking &amp; Wireless
---

### Post by mmontanaro on 2020-02-28
Running Ubuntu 18.04.4 LTS on an HP Pailion dv7 laptop.

The WiFi card is not seeing the 5GHz band.  This machine was formerly a Windows 7 machine and the WiFi card was able to see the 5GHz frequencies and connect to my network just fine.

After changing to Linux, no love.

The iwlist chan command has the following output...
marlo@data2:~$ iwlist chan
lo        no frequency information.


eno1      no frequency information.


wlo1      14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
marlo@data2:~$ 


So, I have a feeling it just isn't using the correct driver- but I have no proof of that.  I'm a newb at this point when it comes to Linux.

Let me know what commands to run and I'll post the output.

Thanks in advance for the help- always learning.

---

### Post by wildmanne39 on 2020-02-28
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using the pastebin link created and someone should be able to help .

*Thread moved to **Networking & Wireless a more appropriate sub-forum**.*

---

### Post by mmontanaro on 2020-02-28
Thanks for the help!!!!  Here's a link to the pastebin.[URL="https://pastebin.com/u3ZVL31X"]

https://pastebin.com/u3ZVL31X[/URL]

---

### Post by CelticWarrior on 2020-02-28
You have a Ralink RT5390, a legacy product, that I'm almost sure doesn't support 5GHz.

---

### Post by mmontanaro on 2020-02-28
The card in this laptop ran on my 5GHz network for several years with Windows 7.  It very definitely does support 5GHz. In fact, that was the only WiFi network I had configured for awhile- there was no 2.4GHz network until I got a printer that was 2.4 only.

Are you 100% sure that the driver that is loaded and what Linux is reporting matches the hardware?

---

### Post by CelticWarrior on 2020-02-28
How was it identified in Windows?

---

### Post by mmontanaro on 2020-02-28
> **CelticWarrior said:**
> How was it identified in Windows?

No idea... it was not something I ever took note of on the machine.  One day, the hard drive died and I switched to a newer Windows machine for my main work.  When I decided to revive this computer, I stuck a new SSD in place for the main drive and just installed Ubuntu on it... so I have no idea what the hardware actually is.  I was relying on Ubuntu to figure that out.  It's not a laptop I want to spend much more money on, so I may just buy a USB WiFi adapter and be done with it. I kind of know where the card is inside the machine, but I honestly don't feel like taking it all apart to find out.

The computer does have some useful life to it, but it does need to have a fully functional WiFi card for that to be the case (I go to some places where they've turned off 2.4GHz Wifi).

I wonder if I look up the serial number on the HP support site if it will give me an inventory of the hardware?... worth a check on a Saturday afternoon...

---

### Post by CelticWarrior on 2020-02-29
All the searches I've made result in "Ralink RT5390R 802.11b/g/n 1x1 Wi-Fi Adapter" for your reported ```
VID:PID - 1814:539a 
```- which is reported directly by the hardware. I'm unaware of any situation where this was identified incorrectly. The OS may not identify a specific model in a full human-readable form or even show the VendorID/ProductID only. 

Before further considerations I must disclose I'm no expert. The WiFi resident expert is @chili555 , I hope he sees this.
That said I'm confident in the hardware identification (the PID "539a" really suggests RT5390 or similar). It's hard to check specs for this because Mediatek, owner of Ralink, has it in the legacy products section with only a link to old Windows drivers, no specs sheet. Googling "RT539x 5GHz" also finds no mention of its support, only mentions of people trying and failing to connect to 5GHz networks, threads like this (Windows 7): [https://forums.techguy.org/threads/solved-ralink-rt5390-802-11b-g-n-wifi-adapter-problems.1000462/](https://forums.techguy.org/threads/solved-ralink-rt5390-802-11b-g-n-wifi-adapter-problems.1000462/)

Again, not an expert, but I'm almost certain the "802.11b/g/n" protocol, the "n" part allowed 5GHz support but wasn't mandatory. it was in "802.11a/b/g/n" of the same vintage as yours. I remember back in the day that same "802.11b/g/n" chips did support 5GHz "n" networks and that being a selling point it was always profusely advertised. I couldn't find such mention for the one you supposedly have. Are you sure that WiFi card wasn't replaced at some point before the revival?

---

### Post by chili555 on 2020-02-29
> 
The WiFi resident expert is @chili555 , I hope he sees this.
Good Morning! I'm here!

A great many things work perfectly in Windows but not Linux and vice-versa. This device and driver combination are textbook examples. It is the driver that is lacking here, not the physical device. The Linux driver in question, rt2800pci, just doesn't support 5 gHz. A Google search confirms this; there are many inquiries going back a decade. There is no solution offered.

As far as I can determine, the driver was written to be good enough; it connects, sometimes with some difficulty, and passes traffic. Good enough.

I suggest that you consider two alternatives: first, content yourself with 2.4 gHz or, second, if you have no whitelist issues, transplant a better device into your laptop. I suggest Intel.

[https://goughlui.com/2014/08/02/laptop-wireless-card-whitelists-an-upgrade-nightmare/](https://goughlui.com/2014/08/02/laptop-wireless-card-whitelists-an-upgrade-nightmare/)

> At this time, it is known that some recent Lenovo, Toshiba, Dell, HP and Compaq follow this whitelisting practice. From my experience, it appears that Asus, Acer, and MSI don’t.

---

### Post by chili555 on 2020-02-29
> 
Running Ubuntu 18.04.4 LTS on an HP Pailion dv7 laptop.
Please see page #8 here: [http://h10032.www1.hp.com/ctg/Manual/c02842278](http://h10032.www1.hp.com/ctg/Manual/c02842278) There is a listing of the wireless cards that came with the DV7 and that, I assume, will pass the whitelist test. Included are three Intels.

---

### Post by mmontanaro on 2020-03-01
THANK YOU!  As far as this issue is concerned, you have saved me from insanity.

As I said, the laptop is on the order of 6 years old maybe?  Not worth putting any money into. It does seem to work fine on 2.4GHz, so I'll be content with that for now.  Mobile operation with this machine will be the exception rather than the rule.  Should things ramp up with work, I'll look into a newer machine.  For now, it is wired to the network for the vast majority of time.

---

