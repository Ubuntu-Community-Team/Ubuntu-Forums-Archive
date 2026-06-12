---
title: "Add an atheros card after install"
date: 2007-06-18
forum: Networking &amp; Wireless
---

### Post by Mike Easter on 2007-06-18
I want to add a wireless pci card function to an existing install.

When I installed Feisty, I was using a wired ethernet integrated with mobo and there was no wireless card.  Later I added a wireless card which is an Airlink 4130 which is the Atheros 5212 wchipset which is madwifi supported.

I don't know how to get Ub to recognize the card.  The network manager is no help.  I don't know how to enable the card as an ath0.  If I sudo modprobe ath_pci I get:
FATAL: Module ath_pci not found.

I used synaptic to install the madwifi tools, but that didn't help.  If I use hardware information, I can see the AR5212.  If I boot up with the Ub Feisty install CD, I can optionally connect with the wireless by using restricted drivers, but the hdd install has no such option.

This computer has an optional boot with Linspire which uses kde utilities.  With the linspire's kde tools I was able to see the wireless card as well as the wired resources and choose which card I wanted to be the default.  The linspire kde network utility is much more useful here than the ub/gnome network manager, which gives me no help whatsoever.  It doesn't even have a place that shows eth0 or give me access to any kind of ath0.

Is there a commandline I can use to get the atheros drivers?  Is there anything I can do with the install CD or syaptic?

Mike Easter

---

### Post by Mike Easter on 2007-06-18
I decided to use the script at stchman.com named madwifi.sh

Unfortunately, after the script, I couldn't logon to the install anymore.  So I decided it would be easier to just reinstall Ub hoping that the proper drivers would be accessible if I installed with both the wired and wireless hardware operating.

---

### Post by stchman on 2007-06-18
> **Mike Easter said:**
> I decided to use the script at stchman.com named madwifi.sh

Unfortunately, after the script, I couldn't logon to the install anymore.  So I decided it would be easier to just reinstall Ub hoping that the proper drivers would be accessible if I installed with both the wired and wireless hardware operating.

Were there any messages from the terminal?  This procedure worked for me in the past.  Did you use this script on Edgy?  The script makes backups of the following files:

/etc/modules
/etc/network/interfaces

The backups have a .bak as the extension.  Boot up into recovery mode and type the following:

sudo mv /etc/modules.bak /etc/modules

sudo mv /etc/network/interfaces.bak /etc/network/interfaces

These commands will rename the files back to their original names and you should be able to login again.

What Ubuntu are you using?  If you are using Feisty then delete the lines 

# Enable WEP, WPA. WPA2 via network manager 
to the end of the file.  Feisty already has network-manager installed.

This script was designed for Edgy not Feisty.  Feisty has the restricted drivers section to enable Atheros cards.

---

### Post by dannyboy79 on 2007-06-18
AR5212 is supported out of the box. I have never had problems with it. It should be a choice within the Linux Restricted Modules Manager which is under System, Admin.

---

### Post by stchman on 2007-06-18
> **dannyboy79 said:**
> AR5212 is supported out of the box. I have never had problems with it. It should be a choice within the Linux Restricted Modules Manager which is under System, Admin.

That is my thoughts exactly.  I have a 5006EG card in my Toshiba laptop that needed madwifi drivers under Edgy but worked out of the box on Feisty.  I was going to assume he was using Edgy or earlier.

---

### Post by Mike Easter on 2007-06-18
re 5212 working out of the box on Feisty...

Maybe I didn't make the problem I had clear.  In the beginning, I did a Feisty install with an integrated wired LAN which was properly recognized and configured and operational.

Chapter 2:  I wanted to make the box a rolling computer which would be in another room and would be using a wired connectivity to my wired/wireless router.  The rolling computer was 'retrofitted' with a PCI wireless card, and I began to configure the 3 OSes that were on it to accept the new hardware with drivers, Win98se, Linspire50, and the existing Feisty hdd install.

Chapter 3:  Linspire recognized the wireless card and gave me the chance to use the wirelss or wired interface.  Wonderful - linspire uses kde utilities for that.  Win98se recognzed the new hardware and I was able to install drivers, but that's another story not yet satisfactorily resove.  Chapter 3 closed with my inability to even find anything on the entire Ub Feisty file system which had anything to do with the necessary files such as ath_pci.ko.  That file was not to be found on the existing hdd install.  I realized that I was going to have to add the necessary 'structure' because it was absent, and I decided to use stchman's script to help me.

Chapter 4: I didn't know how to recover from not being able to logon after the script ran, and I had already tested the live CD and it recognized the wireless card, so I decided that the easiest way out was to reinstall.  The live CD recognized the wireless card, I installed into the same partition that didn't have any drivers on it, and the new install was properly configured for both wireless and wired.

---

### Post by Mike Easter on 2007-06-18
> **Mike Easter said:**
> Chapter 2:  I wanted to make the box a rolling computer which would be in another room and would be using a wired connectivity to my wired/wireless router..

Oops.  I meant I wanted the rolling computer to be using a *wireless* connectivity, so I added the wireless card.

---

