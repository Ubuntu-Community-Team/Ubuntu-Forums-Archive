---
title: "Wireless not working in Feisty!"
date: 2007-05-29
forum: Networking &amp; Wireless
---

### Post by philbo on 2007-05-29
I finally did it, have just upgraded to Ubuntu Fiesty, and said goodbye to Windows XP. BUT! I am regretting it, I can't get my Dvico Fusion hybrid DVB-T card to work and my wireless cards (Dlink DWL-G520 & DWL-G132) don't work either!

I have trolled the ubuntu forums and exhausted their solutions, they all say the the DWL-G520 uses the Atheros chipset which should be built in and load automatically (yeah right!). Whilst the DWL-G132 is a USB card and not supported!!!

Obviously I'm a relative noob! and my background is in windows hence I'm starting to regret my decision, as everything worked in XP.

I have to get the wireless working (due to the physical layout of my house!) so I am wondering whether anyone can point me in the right direction. I previously used OpenSUSE (which also loaded the DWL-G520!) and I could access the YAST control centre to load the drivers through. However I can't find any such 'control centre' in Ubuntu.

Help me please!!!

---

### Post by holihue on 2007-05-29
You could try [ndiswrapper.]("http://ndiswrapper.sourceforge.net/joomla/")

Just download a driver for windows(not .exe but with a .inf file) and try to find a tutorial for installing driver for Windows.


I recommand [THIS.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")

---

### Post by philbo on 2007-05-30
> **holihue said:**
> You could try [ndiswrapper.]("http://ndiswrapper.sourceforge.net/joomla/")

Just download a driver for windows(not .exe but with a .inf file) and try to find a tutorial for installing driver for Windows.


I recommand [THIS.]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29")

Nah no go!

the DWL-G520 uses the atheros chipset which supposedly is integrated into the kernel (I've been told) using the restricted kernel.

I have also tried to install the MADWIFI package and it showed up in 'restricted drivers' but didn't show up in Network manager. I then tried the Ndiswrapper but again it didn't show up in the Network manager.

I am at a loss what to do next!

---

### Post by Anonymous4chan on 2007-05-30
same problem here, which is why i came here. NDISwrapper installs but it says hardware not detected. oh yay i'll try that link. thanks a lot

---

### Post by philbo on 2007-06-07
> **Anonymous4chan said:**
> same problem here, which is why i came here. NDISwrapper installs but it says hardware not detected. oh yay i'll try that link. thanks a lot

Does anyone know what's going on with wireless and feisty???

I have been ferreting through the various forums and the question is the same, it worked in 6.10 but no longer in 7.04!!!

I now have two wireless adapters sitting useless (DWL-G132 & DWL-520) I am ready to return to XP cause at least they worked. How can I promote linux over M$ when not everything is compatible.

Look I know it's early days and support will eventually come but, unfortunately if I needed something done for the devices working on XP, it would be done!

Sorry I'm just having a whinge as I am frustrated with not being able to get my desktop back up and running.:(

---

### Post by kevdog on 2007-06-07
Can you post the output of lspci and you /etc/network/interfaces file???  Hopefully a step in the right direction :)

---

### Post by kevdog on 2007-06-07
I looked up the Dlink DWL-G520 card on the dlink website and there are multiple revisions of the card.  Supposedly according to the info on the website, each has a different chipset.  You need to be more specific about the card you have.

---

### Post by philbo on 2007-06-11
> **kevdog said:**
> I looked up the Dlink DWL-G520 card on the dlink website and there are multiple revisions of the card.  Supposedly according to the info on the website, each has a different chipset.  You need to be more specific about the card you have.

The card I am using is the DWL-G520 hw/ver B3. I thought I'd try one last thing and that was to swap PCI slots and get Ubuntu to re-detect the card. And it found it! It is using the Madwifi atheros driver, however it didn't load 'smoothly'. At first is identified the card and so I disabled the ndiswrapper driver (which is appeared to confict with). Then after rebooting it detected the card but because I have a manual ip it didn't connect. I changed the config and rebooted however it didn't seem to connect to my wireless AP (even if I ifdown'd my eth0 and checked iwconfig to ensure that the wep key was registered and card identified- which it was). I almost gave up and after another reboot I connected. I don't know what I changed but it is working!

I still only see the eth0 NetworkManager applet and don't see the wireless (I've added the Network Monitor applet so that i can verify the signal strength whilst in gnome). 

So I guess my issue is resolve! sort of! I don't get the full 108Mbs connection but I am happy I'm connected, I am going to continue to monitor it to see if it continues to 'hold', lets hope in the mean time the bugs are ironed out in Ubuntu's networking!

Philbo

---

### Post by josephh on 2007-06-13
I am running on a Dell E1505 laptop.  my router is Linksys basic (wireless g); my laptop has broadcomm (BCM4401-B0).  I already did the ndiswrapper thing, but the dhcp fails.  I get no wireless detection.

Any help?

---

