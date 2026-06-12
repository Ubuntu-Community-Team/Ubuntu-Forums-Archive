---
title: "Inspiron 5150 Broadcom Wireless &amp; Feisty"
date: 2007-04-19
forum: Networking &amp; Wireless
---

### Post by AnthoMacP on 2007-04-19
I upgraded to the official release of Feisty today but decided to do a fresh install as to avoid any possible driver conflicts with my beta videocard drivers etc. I installed Feisty but my wireless isn't working. It's a Broadcom Wireless 1350 (802.11b/g) WLAN miniPCI Card #4306 wireless card. From previous installs (back since 5.04) I've been using ndiswrapper to install my wireless driver but that doesn't seem to be an option anymore. The card itself attempts to activate but fails when trying to connect on manual settings, and when set on roam, it doesn't detect any networks which my windows partition has no problem connecting to. Any suggestions on getting this working would be great. Thanks

---

### Post by manalishi on 2007-04-20
Having the same problem in that I can't see any networks available :(

---

### Post by Olmen on 2007-04-20
Same problem here as well. I have a bcm43xx series. No available networks are shown, neither with the built in network manager in feisty nor with e.g. wifi-radar :( Another weird problem is that Ndiswrappers GUI shows "Hardware present: NO" after I tried installling the driver using it. Very strange. Anyone who knows what's going on?

---

### Post by Nrbelex on 2007-04-20
> **Olmen said:**
> Same problem here as well. I have a bcm43xx series. No available networks are shown, neither with the built in network manager in feisty nor with e.g. wifi-radar :( Another weird problem is that Ndiswrappers GUI shows "Hardware present: NO" after I tried installling the driver using it. Very strange. Anyone who knows what's going on?

Ditto on a Broadcom 4303 - I also have a pending thread open before I realized this existed...

~ Brett

---

### Post by Krymore on 2007-04-20
I've got a Broadcom 4309 and I'm having the same problem.  I could never figure out how to get it working in Edgy but I figured it'd be easier in Fiesty, but it's still not working.

---

### Post by Nrbelex on 2007-04-20
Jordan_U on the Ubuntu IRC channel was enormously helpful. Here's what I did to solve the problem:

Install the package named "bcm43xx-fwcutter"

or run ```
sudo apt-get install bcm43xx-fwcutter
```

then either restart the computer or run 

```
sudo modprobe bcm43xx
```

Problem solved!

~ Brett

---

### Post by manalishi on 2007-04-20
Does "bcm43xx-fwcutter" do anything to the actual WiFi card's firmware and is there any risk involved?

Apologies for the scepticism...

---

### Post by Nrbelex on 2007-04-20
The term I've seen used is "extract" firmware which sounds like it shouldn't change anything in the firmware itself... but I can't be sure. The computer I'm using is now a permanent Linux box so I didn't worry too much about that.

~ Brett

---

### Post by manalishi on 2007-04-20
Aye, that be what I saw as well. Assume it doesn't change the firmware but was just looking for some confirmation..

Thanks.

---

### Post by Krymore on 2007-04-20
I assume you need to be connected to the internet through a wired connection for this magic code thing to work?

---

### Post by Greg2 on 2007-04-20
> **manalishi said:**
> Does "bcm43xx-fwcutter" do anything to the actual WiFi card's firmware and is there any risk involved?

Apologies for the scepticism...I can assure you that it will not change or modify your Broadcom firmware. :-)

---

### Post by Nrbelex on 2007-04-20
> **Krymore said:**
> I assume you need to be connected to the internet through a wired connection for this magic code thing to work?

Indeed, as is the case with most packages. Alternatively, you could download it on another computer and bring it to the Linux one via disk.

~ Brett

---

### Post by manalishi on 2007-04-20
> **Nrbelex said:**
> Jordan_U on the Ubuntu IRC channel was enormously helpful. Here's what I did to solve the problem:

Install the package named "bcm43xx-fwcutter"

or run ```
sudo apt-get install bcm43xx-fwcutter
```

then either restart the computer or run 

```
sudo modprobe bcm43xx
```

Problem solved!

~ Brett

Solved indeed!

The modprobe did not work but it was fine after the restart.

Thank you.. :) 

[QUOTE=Greg2]
I can assure you that it will not change or modify your Broadcom firmware. :)
[/QUOTE]

And thank you for the reassurance :D

---

### Post by Olmen on 2007-04-21
> **Nrbelex said:**
> Jordan_U on the Ubuntu IRC channel was enormously helpful. Here's what I did to solve the problem:

Install the package named "bcm43xx-fwcutter"

or run ```
sudo apt-get install bcm43xx-fwcutter
```

then either restart the computer or run 

```
sudo modprobe bcm43xx
```

Problem solved!

~ Brett

Wow! Worked beautifully! Now one can truly start using Linux :D Thanks a lot, mate!

---

### Post by quantumcheese on 2007-04-27
I have done the above steps several times; the only difference is that now the networking icon next to the clock has an un-selectable "Wireless Networks" option below the Wired Network radio button.

$ lspci | grep Broadcom\ Corporation
02:02.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

Any suggestions?

---

### Post by juano816 on 2007-04-27
> **manalishi said:**
> Aye, that be what I saw as well. Assume it doesn't change the firmware but was just looking for some confirmation..

Thanks.

the fix given above works like a charm. i dont think that it changes the firmware. extract, unpack are terms generally used when reading archives like .zip or .rar. you can also look inside of exe files. so what i guess is that the fix mearly refrences the firmware to patch it and make it work.

p.s. if you tried to use the ndiswrapper you have to make sure the you take the original driver installed by ubuntu off the blacklist.
blacklist item: bcm43xx

check out the this link to see what i mean. [click here]("http://www.linuxquestions.org/linux/answers/Networking/NdisWrapper_The_Ultimate_Guide/")

im new at all this so pardon any mistakes with my terms and my english. in the end my wireless works

thanks all

---

### Post by undfined on 2007-05-16
I've gone around a buncha times between the bcm43xx driver and ndiswrapper.

bcm43xx and the instructions in this thread didn't work.  The device appears active but won't scan or attach to any networks.

I followed the instructions here: [http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/](http://www.seungpyo.com/stacksandpiles/2006/07/02/broadcom-wireless-in-ubuntu-dapper-606/).  I customized the commands for Feisty and the appropriate directories and scanning worked.

I can see my wireless networks (I set up 2 [1 open 802.11b and 1 WPA 802.11g) but I still can't connect to either of them.  On the wide open 802.11b I can't acquire an IP address and on the WPA network I get prompted for the passphrase and I see packet transimission but I can't pull an IP address.   Keyring Manager never kicks in either.

This is with a Dell Inspiron 5150 with a Dell Truemobile 1350.

<command>iwlist wlan scan </command> sees the networks and the Gnome Network Manager sees them too.  Just can't connect. 

This thread has been used too: [http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902) , with no luck.

WPA Router is a Buffalo Airstation.  Model: WHR-HP-G54

802.11b (wide open) router is a Linksys WRT54G

Any ideas appreciated.


EDIT3: After a couple reboots the wide open linksys network worked.  I switched back to the bcm43xx drivers and it's good there too.   When I enable WPA and/or WEP I cannot connect.  I've tried wpa_supplicant, wifi-radar, manual WPA config in /etc/network/interfaces, and Wicd without any luck.

---

