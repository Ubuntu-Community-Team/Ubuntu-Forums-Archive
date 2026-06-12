---
title: "Bluetooth not working"
date: 2020-07-28
forum: Networking &amp; Wireless
---

### Post by odepde on 2020-07-28
Hi,

I have a Lenovo Z570 with Ubuntu 16.04 and, while wireless works, Bluetooth doesn't.

The manufacturer's guide shows the following Bluetooth specs:

"BT2.1 + EDR CyberTan/USI module"

and

"Bluetooth card, BT2.1 + EDR, Fcn BCM92070 BT2.1 EDR Flash U NB".

the Bluetooth manager says "No Bluetooth adapters found".

Thanks for your help.

p.s. below is the output of diagnostic commands requested on a similar thread:

$dmesg | grep iwl

[2300197.571637] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2300197.696524] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2305224.813926] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2305224.945451] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2307518.909640] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2307519.036107] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2316072.495594] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2316072.598281] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2316707.297154] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2316707.439778] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2321118.241231] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2321118.349854] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2324100.312930] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2324100.437726] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2328723.912056] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2328724.006346] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2338262.099091] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2338262.201905] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2340534.630108] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2340534.728288] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2345075.997411] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2345076.113351] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2347665.015294] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2347665.157422] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2367808.452313] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2367808.583890] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2368013.208517] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2368013.312736] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2370460.035865] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2370460.164050] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2374833.398401] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2374833.570738] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2379774.865277] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3
[2379774.959850] iwlwifi 0000:02:00.0: Radio type=0x0-0x0-0x3

$rfkill list all:

0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by durexlw on 2020-07-29
Have you tried looking for a driver? Any reason you chose to go with 16 if 20 is available?

---

### Post by odepde on 2020-08-08
the laptop is 8 years old, & I'd rather not upgrade to Ubuntu 20 as newer releases typically require more RAM & CPU for optimal performance.

at this point, I'd like to find out why the Bluetooth hardware isn't even being detected, or appears to not be detected.

---

