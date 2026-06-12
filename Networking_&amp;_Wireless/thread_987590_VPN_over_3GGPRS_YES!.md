---
title: "VPN over 3G/GPRS: YES!"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by RMOP on 2008-11-19
I connected my 3G Nokia phone to my eee PC via USB cable instead of Bluetooth. I placed the phone in PC Suite Mode and Ubuntu recognized it as a Mobile Broadband device, configured it (CORRECTLY!) and connected. I then checked, and my VPN option was available. It connected, and I mounted my SMB shares over my VPN. Nice.

Now, the ironic thing is that this VPN is running over what is essentially the SAME connection as I use with Bluetooth. The only difference is the interface to the phone/modem. But it's still a modem connection.

If there is some way to redirect the Mobile Broadband connection from the expected USB device to the same device but over BT, that would be nice. I keep thinking there must be a way to get Network Manager to "see" a BT phone/modem connection so it can be used for a VPN as well.

---

### Post by RMOP on 2009-12-28
And here I am after over one year. I just switched to Ubuntu 9.10 and am sad to report, no VPN option is available to me when I connect via Mobile Broadband (it's greyed out). This is really rather annoying -- it worked under 8.04.

Any suggestions, please? Thanks.

---

### Post by RMOP on 2009-12-28
Almost as if to embarrass me. After yet another reboot, the VPN option returns with the Mobile Broadband connection. As does the indicator showing the MBB connection active on the panel (it was missing before the second reboot). So, yes, it's there.

Now, if only someone could tell me how for get NM to make the VPN available when the connection is via Bluetooth to 3G phone...

---

### Post by RMOP on 2009-12-29
...sort of. With the connection set to Auto, the 3G/GPRS data connection with my Nokia is established immediately upon plugging in the USB cable. It's fast, stable and permits use of the PPTP VPN configured under Network Manager. ***Except when it doesn't work.***

Right now, Mobile Broadband connects after a reboot. Otherwise, it triggers some ineffective activity between Ubuntu and the Nokia. The phone prompts me to select the type of connection (as usual), but upon selection, the Ubuntu Network Manager animated connection icon on the panel spins at double-speed w/o ever making a data connection. (It also doesn't time-out, so it seems stuck in some kind of loop.)

I deleted the Mobile Broadband connection and used the wizard to create a new one. All of the correct settings were there (nice touch). But, I still get the double-speed "connecting" animation w/o any connection. Until I reboot. Again.  Did I also try deselecting "Auto" in the configuration? Can't recall, but I'll try that when I get home.


Help for this one? I hope I won't be answering my own posts any further (unless to post the answer!). Thanks.

---

