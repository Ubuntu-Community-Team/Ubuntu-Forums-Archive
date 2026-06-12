---
title: "wireless problems ubuntu 10.04"
date: 2010-09-30
forum: New to Ubuntu
---

### Post by Drenriza on 2010-09-30
The problem is that the wireless network is disabled on a laptop of mine. I found that the wireless card is a 
network controller: Atheros communications inc. AR928X wireless network adapter (pci-express) (rev 01)
 
But how can i install drivers for it?
 
Thanks on advance
Kind Regards

---

### Post by nothingspecial on 2010-09-30
Have you tried getting a wired connection and going System > Administration > Hardware Drivers?

---

### Post by coffeecat on 2010-09-30
> **Drenriza said:**
> The problem is that the wireless network is disabled on a laptop of mine. I found that the wireless card is a 
network controller: Atheros communications inc. AR928X wireless network adapter (pci-express) (rev 01)
 
But how can i install drivers for it?

You don't need to. I have a laptop with the AR928X Atheros wireless card and it works out of the box in Lucid (and Maverick) with the inbuilt ath9k driver - and very well too. There was a problem in Karmic (9.10) but that was easily fixed with the backported wireless modules.

Precisely what do you mean by the wireless network being disabled? You do not need to install any drivers.

You are running Lucid, aren't you? That's what your profile says.

---

### Post by Drenriza on 2010-09-30
> **coffeecat said:**
> You don't need to. I have a laptop with the AR928X Atheros wireless card and it works out of the box in Lucid (and Maverick) with the inbuilt ath9k driver - and very well too. There was a problem in Karmic (9.10) but that was easily fixed with the backported wireless modules.
 
Precisely what do you mean by the wireless network being disabled? You do not need to install any drivers.
 
You are running Lucid, aren't you? That's what your profile says.
 
The computer is running 10.04.
When clicking on the top right icon for networking. It says that wireless is disabled.
 
Also when using the command
sudo ifconfig wlan0 up it says that it cannot find the NIC or it gave me an siocsifflags unknown error 132

---

### Post by coffeecat on 2010-09-30
> **Drenriza said:**
> The computer is running 10.04.
When clicking on the top right icon for networking. It says that wireless is disabled.

Try these in the order given:

Right-click on the network manager icon. If the 'enable wireless' line is not ticked, tick it.

Make sure the wireless hardware switch is not in the off position. They're often on the front of a laptop and easily pushed into the off position by accident.

On my "other" laptop which also runs Vista, there is a desktop utility in Vista to disable/enable the network connections. This is not a Windows thing - it was a utility added by the manufacturer, in my case Sony. I once tried disabling the wireless in Vista with this and when I rebooted into Ubuntu there was nothing I could do to re-enable the wireless. I had to boot into Vista to enable it again after which it worked flawlessly in Ubuntu. Goodness knows how it could knock the wireless NIC out so effectively, but check that you don't have something the same in your version of Windows (if any). I've seen threads from other people who have experienced the same with other makes of laptop, so this is not confined to Sony.

---

