---
title: "sl-modem (again)"
date: 2005-05-17
forum: Networking &amp; Wireless
---

### Post by recmar on 2005-05-17
Could anybody help me with configuration of my Intel 537 AC'97 modem.

I installed sl-modem-modules and daemon
sl-modem-daemon_2.9.9a-1ubuntu2_i386.deb
sl-modem-modules-2.6.10-5-386_2.9.9a-1ubuntu2+2.6.10-34_i386.deb, 

tried to reconfigure daemon

sudo dpkg-reconfigure sl-modem-daemon
Setting up sl-modem-daemon (2.9.9a-1ubuntu2) ...
Loading ALSA modem driver into kernel ... done.
Starting SmartLink Modem driver for: .
Creating /dev/modem symlink, pointing to: /dev/ttySL0.

but still have no luck. Pppconfig doesn't recognize /dev/modem as proper modem device.
Modem worked well with few other distros and sl-modem driver. Help!

---

### Post by conall on 2005-06-15
The same happened to me. No way of getting this modem to work :/ I tried to test it with wvdial, but the software can't detect the modem. Seems that the module must create a device at /dev/ttySL0, but it don't work. /dev/modem is linked (ln -s /dev/ttySL0 /dev/modem) to nothing, so it can't work. Anyone knows how to correct this problem?

---

### Post by foxiness on 2005-06-15
[QUOTE=conall]The same happened to me. No way of getting this modem to work :/ I tried to test it with wvdial, but the software can't detect the modem. Seems that the module must create a device at /dev/ttySL0, but it don't work. /dev/modem is linked (ln -s /dev/ttySL0 /dev/modem) to nothing, so it can't work. Anyone knows how to correct this problem?[/QUOTE]
 i have this slmodem and it work with me after i read on ubuntuguide.org

i dont know why it not work with you

---

### Post by conall on 2005-06-15
I made it work today, using ALSA instead of sl-modem-module. It was done by editing the /etc/default/sl-modem-daemon file at the line device. Changing auto for hw:0 (or hw:1, test both) you make alsa control the modem. By doing this I've made wvdial work with /dev/modem.
foxyness, the how-to at ubuntuguide.org did not worked to me.

---

