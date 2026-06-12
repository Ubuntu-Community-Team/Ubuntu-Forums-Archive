---
title: "Easiest way to connect to WiFi from Command line"
date: 2017-05-24
forum: Networking &amp; Wireless
---

### Post by daj_uk on 2017-05-24
[FONT=arial]Background:
I have a Raspberry Pi 3 running Ubuntu 16.04.  The Pi has a small LCD screen attached, and I have a small keyboard.  My idea was that I could someone connect to a wireless network using the command line.  So if I took the Pi to a new location I could start up the Pi, type in the apprpriate commands and then SSH after that from a desktop PC.

I've been searching for an easy way to connect but having no luck. 

Initially I thought

```
iwconfig wlan0 essid...
```

was my saviour, but I believe this only works for WEP keys, whereas most people are WPA now.

[/FONT][FONT=arial]I then look at using [/FONT][COLOR=#111111][FONT=Consolas][FONT=arial][FONT=courier new]wpasupplicant[/FONT] but this seems overly complicated. [/FONT] 

[/FONT][/COLOR][FONT=arial]Is there nothing where I can type one line command to connect to a known SSID?[/FONT]

[FONT=arial]I'd appreciate any thoughts from people who are far more savvy on this than me :)[/FONT]

---

### Post by TheFu on 2017-05-24
wicd-curses

---

### Post by CharlesA on 2017-05-24
> **TheFu said:**
> wicd-curses

This would probably be the easiest way to do it. I've used it in the past, but not on a Pi.

@OP: Have you checked here? I don't know if it will work with the latest version of Raspbian, but it might give you another direction if you don't want to use wicd.
[https://learn.adafruit.com/adafruits-raspberry-pi-lesson-3-network-setup/setting-up-wifi-with-occidentalis](https://learn.adafruit.com/adafruits-raspberry-pi-lesson-3-network-setup/setting-up-wifi-with-occidentalis)

---

### Post by cariboo on 2017-05-26
I had the same problem yesterday on my Pi zero W, I used this:

[https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md](https://www.raspberrypi.org/documentation/configuration/wireless/wireless-cli.md)

to get wireless working.

---

