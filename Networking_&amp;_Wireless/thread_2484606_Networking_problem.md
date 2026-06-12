---
title: "Networking problem"
date: 2023-03-04
forum: Networking &amp; Wireless
---

### Post by babouchedlzozokk on 2023-03-04
Hello,i'm sending this message because a have a problem with my Ubuntu, when i connect to my wi-fi i didn't have any connection,i don't understand wjat happened because my wifi work well but i just don't have any connections,

Thanks you for reading this and maybe help me

---

### Post by aljames2 on 2023-03-04
Is your Ubuntu device the only device that does not connect to your wifi network?  Has this device ever connected to this network before?  Are all your other devices connecting without problem?

Do you do any MAC address filtering on your router?  If so, and this is the first time connecting to the network, then remember to add the new device MAC address to your router. Remember your MAC address seen by your router changes if you switched out your wifi adapter.

Once established their are no upstream issues with your network preventing the connection, then look closer at your device, installation, bios, etc.

Check that your laptop wifi radio is turned on. 

If your Wi-Fi adapter is a bleeding edge device, check the docs on it to see which Linux kernel supports it.  Which Ubuntu version are you using?

---

