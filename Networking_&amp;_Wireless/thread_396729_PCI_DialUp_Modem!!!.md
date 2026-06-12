---
title: "PCI DialUp Modem!!!"
date: 2007-03-29
forum: Networking &amp; Wireless
---

### Post by ManiDhillon on 2007-03-29
I have installed Ubuntu Edgy Eft and i'm unable to use my Dial Up connection through My Intex PCI 56K Modem! It doesn't even detect it via WVDIAL.
In our area we are still missing BroadBand or ADSL so the only way to connect is Dial Up. Help me to configure and detect my modem.

---

### Post by ManiDhillon on 2007-03-30
Please someone help me! I need it badly coz without it i can't download codecs for Totem and other players.

---

### Post by sirius0 on 2007-04-01
[Read the pppconfig option.]("https://help.ubuntu.com/community/DialupModemHowto/SetUpDialer#head-0769b0061bf81bfba710118540bd86223e815761")
Follow the link above.
I suspect that being a PCI modem that it is a win modem and you will need a driver. The link also talks about this.

One thing though is that I could not get pppconfig to work until i entered the settings from the failsafe terminal on boot up.
I am using an external modem and pppconfig works well.
Instead of using a terminal window to connect I have set up a launcher that has *pon* as the command and another that has *poff* to disconnect.

1. At the log in screen select options (bottom left of screen)
2. Select failsafe terminal radio button and log in.

3.at the prompt type in *sudo pppconfig*
You will need to know which ttyS* the modem is on.

---

