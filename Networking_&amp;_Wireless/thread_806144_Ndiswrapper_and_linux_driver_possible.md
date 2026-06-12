---
title: "Ndiswrapper and linux driver possible?"
date: 2008-05-24
forum: Networking &amp; Wireless
---

### Post by Jackie999 on 2008-05-24
I have two usb antennas.

The first, a Belkin F5D8053 (rt2870) runs fine with ndiswrapper. I couldn't get the linux driver to compile/install  so use the ndiswrapper.

Then I bought an Alfa AWUS036H (rt8187) which is supposed to be linux 'friendly' and I read it will also work with aircrack (which I'd like to try)

My problem is that I can't get the Alfa running without the ndiswrapper..if I rmmod ndiswapper - the wlan0 disappears. If I blacklist the ndiswrapper, the wlan0 doesn't show up . Is there anyway to make it use its own linux driver..or even the aircrack one without the ndiswrapper grabbing it?

I don't want to 'uninstall' the ndiswrapper completely since my other usb antenna needs it.

Any suggestions on what I can do?

---

