---
title: "strange wireless behaviour acer aspire"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by mathenge on 2008-04-12
I have an Acer Aspire 5040. Here's what happens. My question is at the end, so please read and see if you can help.

I boot the Gutsy (7.10) live-cd. There's no wireless at all but the restricted drivers panel shows that the Atheros Hardware Acess Layer (HAL) driver has been loaded.
I copy the acer_acpi module from my usb disk, compile, install. This creates the entry:

/proc/acpi/acer/wireless.

I then type in the following two commands:

sudo chmod 777 /proc/acpi/acer/wireless
sudo echo 1 > /proc/acpi/acer/wireless.

The LED for the wireless on my laptop goes on. There's still no wireless entry for the card (an Atheros card).

I reboot the laptop back into the live-cd.

The LED is still on. Now I have wireless and I can connect to my SSID.

Second story, this time using Hardy (8.04), even stranger.

I boot using the live-cd. There's no wireless. The restricted drivers panel shows two drivers have been loaded. The Atheros Hardware Access Layer (HAL) and Support for Atheros 802.11 wireless LAN cards. I also notice that acer_acpi is already installed and loaded (so no need to install as in 7.10)

I open a console and type:

sudo chmod 777 /proc/acpi/acer/wireless
sudo echo 1 > /proc/acpi/acer/wireless

The LED for the wireless card comes on.

I reboot the machine back into the live-cd and, voila, I have wireless networking.

My question:

Is there any way to wake up the hardware, force Linux to recognize it without the reboot?

---

### Post by rad_sci_guy on 2008-04-12
I have a similar problem with my aspire 5040 as well.  I dual boot with windows xp.  When i fresh boot with ubuntu the wireless card light is on but Network Manager does not show me a wireless option.  I then reboot the computer without turning it off and then the wireless option is available and ubuntu even automatically connects to my home network.

Its as if the network manager does not check for wireless after the wireless card has been turn on.  I'm wondering if there is a trick to get Network manager to check for a wireless netowork after the card is turned on or if there's a way to delay network manager's search for a wireless connection during the initial boot up.

This process is repeated each and every time the laptop is completely turned off.  I have search the forums for months for a solution but no one seems to have come up with one.  I even posted once before with this problem by my post went unanswered.

I'm praying it's been fixed in Hardy Heron.   I have a thinkpad laptop as well with a d-link pcmcia card which always starts up without reboot even if I plug the card in after I've already started the computer so that makes me even more puzzled.:confused:

---

### Post by Starcrafter on 2008-04-12
I had some wireless trouble with an Acer Aspire 1360. Got the drivers working via ndiswrapper but it wouldn't start automatically. Not sure how related this is to your problem but this thread has the answer that fixed mine:

[http://ubuntuforums.org/showthread.php?t=576238](http://ubuntuforums.org/showthread.php?t=576238)

Now it starts up perfectly.

---

### Post by rad_sci_guy on 2008-04-13
Starcrafter 

Thanks for the suggestion.  I tried commenting out that line in that script but unfortunately I still have the problem of needing to reboot the laptop so that the wirless networking is available in Network Manager.

:(

---

### Post by mathenge on 2008-04-13
Since I'm using the live-cd, commenting the line out won't help. I should really install but I've tried that before and had to revert to Windows since I really need wireless on that laptop.

I'm probably going to go ahead and install it since I know that the reboot option is a viable workaround. However, I'm still going to wait for Hardy release since I don't really have to do anything other than reboot. In fact. I might find a way to turn on the wireless card before networking wakes up, or add some code in /etc/init.d/networking to wake up the card before it starts running the ifup/down scripts.

Thanks for the suggestion anyway.

---

### Post by rad_sci_guy on 2008-04-27
Just and update on my situation

I installed Hardy on the acer and I still had the same problem.  I then tried Kubuntu and it was able to connect to the wireless network on first boot.  So I reinstalled ubuntu and this time I installed the Knetworkmanager from synaptic.  After configuring acer-acpi I was able to get ubuntu to connect to the wireless network on first time boots.

I hope this solution will help others with a similar problem.  I've been working on this problem since Fiesty Fawn came out with no luck until now.:KS

---

