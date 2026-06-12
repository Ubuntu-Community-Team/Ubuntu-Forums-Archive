---
title: "Xubuntu Network Manager inputs wrong WPA passkey"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by Zeedok on 2007-10-23
I had a problem with the wireless setup on my Xubuntu laptop after upgrading to Xubuntu 7.10.

With my Feisty Xubuntu I had some trouble setting up the network, so I used WICD which is a great program for setting up wireless networks etc. It seems to be easier and better featured than the Ubuntu (and now Xubuntu 7.10) network manager which has just been included in Xubuntu 7.10.

Once upgrading my wireless network was not working, though I quickly realised (through System -> Network) that my WPA passkey was not recorded. After entering this the network is fine.

The only problem I have is that the password is replaced by an incorrect one every time I reboot. This means I have to re-enter it everytime . . . It reminds me of dial-up!!

Does anyone have a solution for this glitch?

---

### Post by Zeedok on 2007-10-24
I've solved my own problem . . . though not with Network Manager.

After trying to manually configure my [HTML]/etc/network/interfaces[/HTML] file by entering my WPA passkey (with the Hex converted format) but something didn't work. Each time I booted, I had to re-enter my passkey.

Finally, I gave up and uninstalled network manager and reinstalled WICD through synaptic.

(just added [deb http://apt.wicd.net gutsy extras](deb http://apt.wicd.net gutsy extras) to my sources list and then installed wicd - synaptic automatically removed network manager)

I find wicd easier to configure and use, and  . . . it just works.

Hope this helps anyone who comes across the same problem.

---

