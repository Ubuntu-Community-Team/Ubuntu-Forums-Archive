---
title: "ati radeon R5450"
date: 2011-03-27
forum: New to Ubuntu
---

### Post by Jyscal on 2011-03-27
Hey again all!

I finally managed to get a new video card :)

I was just wondering if there is a driver for it though? I have been to hardware drivers and it says i have no hardware installed. I tried up dating synaptic and searching for ati and radeon drivers but could only find the xorg package.

I have a very low resolution and a refresh rate of 0, so am worried this may not be good for the hardware.

I apologise if this is really simple but could any help with this?

Thanks alot!

---

### Post by rajeev1204 on 2011-03-27
> **Jyscal said:**
> Hey again all!

I finally managed to get a new video card :)

I was just wondering if there is a driver for it though? I have been to hardware drivers and it says i have no hardware installed. I tried up dating synaptic and searching for ati and radeon drivers but could only find the xorg package.

I have a very low resolution and a refresh rate of 0, so am worried this may not be good for the hardware.

I apologise if this is really simple but could any help with this?

Thanks alot!


Which version of ubuntu are you using ? Hardware drivers should have offered you the amd catalyst driver.Your card will work without it too using the default open source driver which is installed when you install ubuntu.

---

### Post by Jyscal on 2011-03-27
> **rajeev1204 said:**
> Which version of ubuntu are you using ? Hardware drivers should have offered you the amd catalyst driver.Your card will work without it too using the default open source driver which is installed when you install ubuntu.

9.10 I still have not managed to get a newer version as of yet, but am planning to asap.

Is there anywhere else i could download the same package or would updating the kernel help at all.

---

### Post by rajeev1204 on 2011-03-27
> **Jyscal said:**
> 9.10 I still have not managed to get a newer version as of yet, but am planning to asap.

Is there anywhere else i could download the same package or would updating the kernel help at all.

If you want to try the fglrx driver you can install it from synaptic directly.

or from command line sudo apt-get install fglrx or whatever it is called.
After it is installed , type sudo aticonfig -f --initial  

reboot.You should be using the proprietary driver on startup.You can go to preferences >catalyst control center and check if all is fine.

---

### Post by Jyscal on 2011-03-27
> **rajeev1204 said:**
> If you want to try the fglrx driver you can install it from synaptic directly.

or from command line sudo apt-get install fglrx or whatever it is called.
After it is installed , type sudo aticonfig -f --initial  

reboot.You should be using the proprietary driver on startup.You can go to preferences >catalyst control center and check if all is fine.

I tried downloading and installing but after trying the sudo aticonfig -f --initial, i get the error of no supported adapters detected.

I am googling like crazy to try find an answer but cant see anything. Dying to see the card in action!

---

### Post by rajeev1204 on 2011-03-27
Maybe you are using the onboard card , have you checked in bios if you have enabled PCI graphics as primary display?

I have a radeon 5750 myself.Where is your monitor plugged in.? To the onboard or the PCI express card?

---

### Post by Jyscal on 2011-03-28
Thanks for the help.

PciE is enabled by default and the cable is is connected. I read that the Xorg in 9.10 is not supported with my card. I try find a link to the site again. 

I tried 8.10 as well but same thing. Is there a ppa i could try?

---

### Post by mastablasta on 2011-03-28
you should try new Ubuntu version 10.10. It is more likely to support newer hardware than older version of the OS that were made when perhaps this hardware wasn't available or was just starting to be available.
 
Think about it! Windows 98 also wouldnt' support the new hardware (likely). You would probably only get VGA at best.

---

### Post by rajeev1204 on 2011-03-28
Yes i agree with masta, the 5000 series is much newer and you should upgrade to 10.04 for better support.

You can upgrade direct or from a cd or usb stick.10.10 should also offer better detection of hardware and offer you the AMD catalyst driver.

One last thing,the proprietary driver in ubuntu 10.10 is way way better in performance and quality than even the version in 10.04 which uses the catalyst 10.4 driver .



So final word: Go with the latest ubuntu version for best driver support for your card.

---

### Post by coffeecat on 2011-03-28
> **mastablasta said:**
> you should try new Ubuntu version 10.10.

Agreed. Or 10.04 as rajeev1204 suggests.

@Jyscal, your card is probably too new for  the default open source ATI driver in 9.10 and earlier to support it. The proprietary fglrx driver in 9.10 will also be older to be compatible with the older xserver in 9.10 - it may not support a Radeon 5450 either.

When I installed 9.10 on my laptop with a Mobility Radeon HD4200 (an older chipset than yours) the open-source driver worked OK but didn't give me 3-d for compiz. And the proprietary driver was a disaster. Since then the open source driver has got better and I was able to enable compiz in 10.04 and 10.10 (and 11.04 testing).

Try running the live CD for both 10.04 and 10.10. Don't install - simply choose "try Ubuntu" rather than "install Ubuntu". That may help you decide whether to use 10.04 or 10.10. You may find you get perfectly good performance with the default open source driver.

Ubuntu 9.10 will soon go end-of-life so you need to be thinking of using a newer release anyway. And you're wasting your time trying to get that card working in earlier versions.

---

### Post by Jyscal on 2011-03-31
Hey all thanks for the support.
 
I have decided to upgrade to 10.04 instead of downloading an iso and re-installing.
 
Could anyone please give me an idea on how large the upgrade would be? The reason im asking is because i unfortunately still only have a 3G USB Modem to connect with, and would have to purchase a sufficient data bundle to make sure i have enough for the upgrade. 
 
I think 1GB should be enough if the iso is 700mb? Though i could be severly mistaken!
 
Any help would be appreciated as i would like to start the upgrade straight after work:)
 
Thanks alot!

---

