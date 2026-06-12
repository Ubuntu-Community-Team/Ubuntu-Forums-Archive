---
title: "Sound device issue VIA VT1708B 8-Ch"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by digital-soul on 2010-08-27
Hi, I am having problem with my Ubuntu.
first when I start my pc sometimes my browser won't play any audio, or I can barely hear the sounds, but there is no issue with my player (Amarok) when I reboot my pc Amarok audio is very low and my browser audio is working fine, everytime I reboot it seems that the issue is sporadic, the other one might work fine but the other is not.

my sound card is built-in with my ASUS M3N78-VM (VIA VT1708B 8-Ch) and I am using alsa

cat /proc/asound/card0/codec#* | grep Codec
Codec: VIA VT1708B 8-Ch
Codec: Nvidia MCP78 HDMI

I wanted to use VIA VT1708B 8-Ch as default, is it possible? because if I open my alsamixer in terminal it says Chip: Nvidia MCP78 HDMI.

I don't know what I am doing really, I been googling it but haven't found any answers yet, as proposed I did uninstall pulseaudio..

Thanks for your help.
**

---

### Post by digital-soul on 2010-08-27
by the way, when I use another apps like bangshee or abraca it works fine for me, no problem at all with those apps and with my firefox, audio is working fine..

---

