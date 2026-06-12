---
title: "[SOLVED] WifiDocs/Driver/Ndiswrapper community"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by Mark_in_Hollywood on 2007-07-18
From 

WifiDocs/Driver/Ndiswrapper

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

[B]2.4. Disable Free Drivers

Dapper comes with the open source bcm43xx driver. If this driver doesn't work for you, then you should disable it, because it will conflict with ndiswrapper. To disable it, add blacklist bcm43xx to the modprobe blacklist.

echo 'blacklist bcm43xx' | sudo tee -a /etc/modprobe.d/blacklist

(Or just edit the /etc/modprobe.d/blacklist file and add blacklist bcm43xx to the end of the file.) Note: This only effects what is loaded at startup, so you will have to reboot to have the bcm43xx driver disabled. If you have an atheros based card, remember to blacklist not only ath_pci, but also ath_hal, since ndiswrapper won't work if ath_hal is still loaded. [/B]

I have an Atheros based card (WDA 2320), how do I black list ath_pci and ath_hal?

---

### Post by kevdog on 2007-07-18
```
gksu gedit /etc/modprobe.d/blacklist
```

Add to the bottom of the file:
```
blacklist ath_pci
blacklist ath_hal
```

---

### Post by Mark_in_Hollywood on 2007-07-18
Done, now for the next instruction:

2.5. Set up and install drivers

    *      /!\ Important: Be careful when using the drivers from the CD included with the wireless card. They may work and you can try them, but you could experience kernel crashes and other serious problems if the driver on your CD has not been tested with ndiswrapper.

    *      You should download a tested Windows XP driver which is suitable for your card from the ndiswrapper list.

   1.      Open a Terminal (Applications | Accessories | Terminal), type lspci and press the return/enter key.
   2.      Look through the output of the lspci command for an entry for your wireless card.
   3.      Once you have identified your card, note down the contents of the first column, which should look like 0000:00:0c.0.
   4.      Now, type lspci -n into the Terminal and press return.

when I lspci i get no mention of my pci bus based wda 2320 card. Do I need to reboot to get the blacklist up?

---

### Post by kevdog on 2007-07-18
I think the answer to your question is yes.

Although not included in your guide your reading, the best way is to type:
lshw -C network

This should bring up your device and possibly tell you the driver currently assigned to you network device.  If no driver is listed, no driver is currently assigned.

---

### Post by Mark_in_Hollywood on 2007-07-18
Running lshw -C network

causes a flash of words to run past

mark@lexington:~/
WARNING you should run this program as superuser

I can only make out the word: scsi

running as sudo does the same, there is nothing on the screen returned from the command except the command prompt

---

### Post by Mark_in_Hollywood on 2007-07-20
Bad card. once it was replaced, lspci shows it is on the bus. Thanks.

---

