---
title: "Performance on Hp Pavilion 504a"
date: 2010-04-25
forum: New to Ubuntu
---

### Post by FrancesL on 2010-04-25
Hi everyone
Sometime back, in Aug '09 in fact, I posted and received a heap of responses relating to a very slow performance on my Hp Pavilion 504a when I installed Ubuntu 9.4. since then my HD died & along with a load of life's interferences, I have just got back online with that pc. I am hoping it is now time to try another install of Ubuntu but will I have the same slow performance if I do? Do I need a new graphics(?) / video card to get better performance. I am not worried about all the fancy tricks. I just want to use Facebook/Club pogo/ IM/ internet/email but with a pleasant experience. All my specs in my signature. I am using a borrowed machine to post this. 
I opened the CPU on pavilion & gathered the following off the PSU:
 Bestec ATX-1956A P1
input rating: 100v-127v-6A 60Mhz
                      200v-240V-3A 50Mhz
+5v & + 12v 163W max + 33v & 5V 1500W Max
and found this on line at a price I could afford but don't know if it is suitable? MSI Radeon HD 4350 Graphics Card ATi Radeon HD 4350 600MHz - 512MB DDR2 SDRAM 64bit - PCI Express 2.0 x16 - DVI-I, HD-15, HDMI Features - Product Name: Radeon HD 4350 Graphics Card - Product Type: Graphics Card - Host Interface: PCI Express 2.0 x16 - RAMDAC Speed: 400 MHz, 400 MHz - Maximum Resolution: 2560 x 1600, 2560 x 1600 - Analog Signal: Yes - Digital Signal: Yes - HDCP Support: Yes - Dual Link DVI Support: Yes - Chipset Manufacturer: ATi - Chipset Model: Radeon HD 4350 - Processor Speed: 600 MHz - Standard Memory: 512 MB - Memory Technology: DDR2 SDRAM - Bus Width: 64 bit, 64 bit - Interfaces/Ports: 1 x HDMI Digital Video, 1 x HDMI Digital Video - Green Compliance: Yes - Green Compliance Certificate/Authority: RoHS
Any help is welcome!

---

### Post by Jon Monreal on 2010-04-25
Those specs do suggest that it would be at least a little sluggish.

How experienced are you with Ubuntu? You could try the very lightweight (but full-featured) Lubuntu. There is a LiveCD that you could try or even install from. If a LiveCD would be too slow, you can do an alternate command-line install of Ubuntu and then install lubuntu-desktop with that (you would just need an ethernet connection).

Of course, Lubuntu is pre-release software and working with the command line can be challenging, so if you aren't up to it or have any doubts I'll look into something else.

---

### Post by sandyd on 2010-04-25
> **FrancesL said:**
> Hi everyone
Sometime back, in Aug '09 in fact, I posted and received a heap of responses relating to a very slow performance on my Hp Pavilion 504a when I installed Ubuntu 9.4. since then my HD died & along with a load of life's interferences, I have just got back online with that pc. I am hoping it is now time to try another install of Ubuntu but will I have the same slow performance if I do? Do I need a new graphics(?) / video card to get better performance. I am not worried about all the fancy tricks. I just want to use Facebook/Club pogo/ IM/ internet/email but with a pleasant experience. All my specs in my signature. I am using a borrowed machine to post this. 
I opened the CPU on pavilion & gathered the following off the PSU:
 Bestec ATX-1956A P1
input rating: 100v-127v-6A 60Mhz
                      200v-240V-3A 50Mhz
+5v & + 12v 163W max + 33v & 5V 1500W Max
and found this on line at a price I could afford but don't know if it is suitable? MSI Radeon HD 4350 Graphics Card ATi Radeon HD 4350 600MHz - 512MB DDR2 SDRAM 64bit - PCI Express 2.0 x16 - DVI-I, HD-15, HDMI Features - Product Name: Radeon HD 4350 Graphics Card - Product Type: Graphics Card - Host Interface: PCI Express 2.0 x16 - RAMDAC Speed: 400 MHz, 400 MHz - Maximum Resolution: 2560 x 1600, 2560 x 1600 - Analog Signal: Yes - Digital Signal: Yes - HDCP Support: Yes - Dual Link DVI Support: Yes - Chipset Manufacturer: ATi - Chipset Model: Radeon HD 4350 - Processor Speed: 600 MHz - Standard Memory: 512 MB - Memory Technology: DDR2 SDRAM - Bus Width: 64 bit, 64 bit - Interfaces/Ports: 1 x HDMI Digital Video, 1 x HDMI Digital Video - Green Compliance: Yes - Green Compliance Certificate/Authority: RoHS
Any help is welcome!

hey, can you list the processor speed? the info above only lists the psu, motherboard, and graphics card

---

### Post by Jon Monreal on 2010-04-25
It's in the signature - 1.7 Ghz Intel processor. From other info about the Pavilion 504a, probably an old and slow netburst Celeron.

---

### Post by FrancesL on 2010-04-26
> **carlee said:**
> hey, can you list the processor speed? the info above only lists the psu, motherboard, and graphics card

Hp Pavilion 504a desktop,1 x 400 GB HD 1.5GBRAM: 1.7 Ghz Intel processor.Intel 8284 5g/GL [Brookdale-G][Intel 82845G/GL/GE/PE/GV graphics controller].

---

### Post by FrancesL on 2010-04-26
Thank you for taking the time to read my post

---

### Post by user1397 on 2010-04-26
I don't see why a full install of regular ubuntu would not be speedy, especially for your needs.  You don't seem to require anything graphics intensive, your onboard card should do fine.

Of course, a more lightweight distro will be a bit faster, but regular ubuntu should be more than fine.

---

### Post by FrancesL on 2010-04-26
> **ubuntuman001 said:**
> I don't see why a full install of regular ubuntu would not be speedy, especially for your needs.  You don't seem to require anything graphics intensive, your onboard card should do fine.

Of course, a more lightweight distro will be a bit faster, but regular ubuntu should be more than fine.

Thanks for the reply. When I last installed Ubuntu 9.4, the performance was so slow, I have to say it was frustrating. Thus the post here. But then, perhaps I am thinking zebras instead of horses, it may well have been the (now failed) hard drive. I will give it a shot again.

---

### Post by warfacegod on 2010-04-26
> **FrancesL said:**
> Thanks for the reply. When I last installed Ubuntu 9.4, the performance was so slow, I have to say it was frustrating. Thus the post here. But then, perhaps I am thinking zebras instead of horses, it may well have been the (now failed) hard drive. I will give it a shot again.

I'd have to say that the HDD failing is the most likely culprit. Your hardware, while not of hotrod caliber, is fairly decent and well above the recommended minimum requirements for Ubuntu. Don't expect Ludicrous Speed but it should be able to cruise along.

If you still have issues with speed and you've exhausted all of the software "tweaks" available (first place to look is Startup Applications) then I'd take a look at that Intel video card. Intel's video driver support is absolutely abysmal. A mid-grade nVidia 256 MB can make all the difference in the world.

---

### Post by Jon Monreal on 2010-04-26
> **FrancesL said:**
> it may well have been the (now failed) hard drive

That thought came to mind, but wasn't there something on there before you tried installing Ubuntu the first time? That would have been slowed down too.

At any rate, just trying can't hurt.

---

### Post by Kellemora on 2010-04-26
Hi FrancesL

We had several very old computers stuck in a closet here!
Each of them had something wrong with them (as far as running the DOZE) is why they were retired.
After my first taste of Ubuntu, and as a learning experience, I pulled these old beasts out of the closet and loaded 8.04 Hardy onto them.

NOW, they are ALL up and running and used every day!
None of them would I say are slow!
Just installed LAMP on one of the oldest so I can learn to write PHP and JavaScript.

We completely retired the really old Win95 computer that required a CGA monitor, and of course the older 386's with Win3.11 on them, hi hi.....
Sorta wish I would have tried a Light Ubuntu on them, just out of curiosity.

TTUL
Gary

---

### Post by FrancesL on 2010-04-26
Thanks Warfacegod!

---

### Post by FrancesL on 2010-04-26
Thank you Kellemora. By the sounds of all the responses here, there is no reason not to try again. Which puts a smile on my face!

---

### Post by FrancesL on 2010-04-27
Thanks Jon Monreal, yes it hass Win XP home, and it was slowing down post SP3..which was when I decided I wanted out of MS..but that is past history, will see how I go! Again, thanks.

---

