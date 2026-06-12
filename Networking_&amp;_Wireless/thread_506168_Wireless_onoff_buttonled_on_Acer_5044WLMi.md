---
title: "Wireless on/off button/led on Acer 5044WLMi"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by karhulitos on 2007-07-21
I'm hoping someone could help me get that Acer's orange wireless button to work so I could disable wlan when I don't need it.

I have wireless (Atheros AR5005G) working just fine.

Pressing wifi button produces
```
[16547.696000] atkbd.c: Unknown key released (translated set 2, code 0xd5 on isa0060/serio0).
[16547.696000] atkbd.c: Use 'setkeycodes e055 <keycode>' to make it known.
```

I have acer_acpi installed (for emailled) so I can
```
echo enabled: 1/0 > /proc/acpi/acer/wireless
```
to enable/disable it on terminal

Now, I figured this cannot be a big thing to make the button known so that it would run a script when I press it.
I think I can do the shell script on my own (unless someone has this already at hand) but what is mystery to me is how configure system to run a script when wifi button is pressed.

Please help!

---

### Post by karhulitos on 2007-07-23
Anyone? I thought this would be a piece of cake for someone more expert..

---

### Post by rojanu on 2007-07-24
hav you got something working yet for your switch?

---

### Post by karhulitos on 2007-07-29
Unfortunately not. I just cannot figure out how to convert that button pressing event into a shell script.. :(

---

### Post by isaacj87 on 2007-07-29
Hey, I saw your post...Maybe this can help.

I've got an Acer Aspire 1642WLMi and I noticed that my wifi led didn't working after installing Fiesty...
I found this fix on LaunchPad that worked PERFECT for me...

[Wifi LED Fix]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/26464")

> 

i've got a simple solution to this if you adds a text file (/etc/modprobe.d/ipw2200)

and puts in it the following:

options ipw2200 led=1

Which sends a command to turn the light on when the module is loaded and it works after this. Can this file be put there by default?? Someone please reply...


That quote was taken from the page. Credit goes to that guy.

---

### Post by karhulitos on 2007-07-30
> **isaacj87 said:**
> Hey, I saw your post...Maybe this can help.

I've got an Acer Aspire 1642WLMi and I noticed that my wifi led didn't working after installing Fiesty...
I found this fix on LaunchPad that worked PERFECT for me...
[Wifi LED Fix]("https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/26464")
That quote was taken from the page. Credit goes to that guy.

Hei, noticed your Skype call afterwards while I was already away from the net, sorry! I must have closed the lid at the very same moment you called me, bad luck.

I also saw that fix earlier but I guess it's for Intel wlan chip while I have one from Atheros here in this 5044WLMi.
My led is lit whenever wlan is acivated so that part is ok here. I rather seek for turning an unrecognized button (wlan button) event into running a script (echo enabled: 0 > /proc/acpi/acer/wireless) so I can save power if I don't need/have wlan around.

But, thanks anyways!

---

