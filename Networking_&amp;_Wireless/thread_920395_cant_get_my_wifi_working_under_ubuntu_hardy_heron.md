---
title: "cant get my wifi working under ubuntu hardy heron"
date: 2008-09-15
forum: Networking &amp; Wireless
---

### Post by mav3r1ck on 2008-09-15
i have a intel PRO wireless adapter 3945ABG i have the windows wireless driver package installed on ubuntu, and i have found what i think is the driver needed, w39n51.inf and the folder and files holding it named "Drivers" i can install the driver with the program in ubuntu, it finds the hardware, and immediately locks the computer up and my caps lock light keeps blinking, i can hold FUNCTION and f2 that usually turns off my laptops wifi card as i bot up, and thus turn it off, and the system boots up perfectly fine, until i try to turn it on again. i even went to the intel site for my drivers and i got the same driver set. and im dual booting windows and i have already unchecked the option in power management that allows windows to turn off my wifi card, and still nothing.

if it helps any my laptop is a gateway model cx2724.

more so i have an aircard that i would prefer to use, its the 595u aircard thru sprint, and i need a way to install its drivers and programs, unless theres an alternative of some kind?

im very green on linux, this is the first time ive ever installed it let alone used it or even looked at a linux desktop, any help is greatly appreciated. thanks in advance!

---

### Post by Squish on 2008-09-15
Rumour has it that the next version of ubuntu focuses on wireless usability. Lets hope so, because wireless has been an Achilles heel for linux for a long time...

Anyways, I am a bit surprised, that wireless card is supposed to work out of the box as far as I know. Did you check your restricted drivers utility? Because you might have installed the ndiswrapper one for no reason.

:KS < Happy Star

---

### Post by gnusci on 2008-09-15
Here some details about your card:

[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsIntel)

Note that if you use 802.1x and WPA1/2 Enterprise you may need to install linux-backports-modules-hardy.

---

### Post by mav3r1ck on 2008-09-15
it says in the chart that the driver for my card is iwl3945, but when i went to the intel site and looked up my card, it gave me the w39n45 drivers. and if i installed the ndis uneedingly then wouldnt _uninstalling it be a fix to my issue then?_
i tried uninstalling the ndiswrapper, did me no good. hhmmm...

and no i havent, i dont know how to check the restricted drivers, where do i find that? also, i just did a google for the iwl3945 driver and i came up with this page [http://www.intellinuxwireless.org/?p=iwlwifi&n=downloads]("http://www.intellinuxwireless.org/?p=iwlwifi&n=downloads")

is this what i need? if so how do i install it?

---

### Post by Squish on 2008-09-15
System > Administration > Hardware Drivers

If it were me, I would boot up the live CD, and see if the wireless is detected and such. If it is, then I would know that I screwed something up in my installed ubuntu. 
On the top right corner there should be a bunch of symbols. The Green PCI Card represents the hardware drivers. Clicking on that SHOULD bring up your wireless card.

Again, the forums I have checked say that this card works out of the box. I think my laptop has it too. You might have just tried to over complicate things~
Hope this helps ~

---

### Post by mav3r1ck on 2008-09-15
ok, i booted the live cd, and it automatically gave me a caution symbol instead of an x on my network icon, i checked, and it automatically gave me a wireless network connection in my manual configuration tab. so, where should i go from here? reinstall and make a clean slate? if so i went into the instal steps anyway, and went to my step 4, the partitioner, and it was all screwy, the first option shows me something similar to 

          |ubuntu 8.04 2.1GB| |ubuntu 4.7GB|

how do i just erase my old ubuntu installation prior to reinstalling?

otherwise, would it be simpler to run through my current installation and fix what ive done already?

---

### Post by mav3r1ck on 2008-09-16
ok nevermind, i reformatted and reinstalled ubuntu, and now it acts like the live cd. i get to where it auto scans for wifi, and finds my router i hooked up just to test it, it finds it and when i tell it to connect, it tries to work, but i think because the router isnt connected to anything else it isnt getting a finalized response, just a "connecting..." but this is definantly a step forward, the router is a linksys befw11s4, is it the router or it that its just not connected to anything?

---

### Post by Squish on 2008-09-16
ah, good stuff man, you seemed to figure it out.
If you suspect it being the card, try connecting to another network that you know works. Usually linksys is fairly good with Linux, and routers should work cross platform. 

Sometimes the routers settings just need to be reworked, or defaulted. If you have some weird setup with it, with mac addresses and allowances, then it might be a pain. Otherwise, I dont understand why it wouldnt be working. When I have network problems, allot of the time, just pushing the little button on it to reboot it does the trick. I searched to see if anyone was having any problems with it and linux, and there doesnt seem to be any relevant ones. 
Once you are connected, you should get a stair of blue bars indicating your strength of signal. Even if its not connected to the internet, you should still be able to connect to the router.

---

