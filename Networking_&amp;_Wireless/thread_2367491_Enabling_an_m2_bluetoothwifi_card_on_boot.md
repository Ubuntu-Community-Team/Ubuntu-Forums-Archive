---
title: "Enabling an m2 bluetooth/wifi card on boot"
date: 2017-07-31
forum: Networking &amp; Wireless
---

### Post by mercenarycor on 2017-07-31
Hello!

First, let me explain that nothing is wrong.  There's no bug, and no issue to solve.  I'm trying to do something extra!

Ok, here's what I got. I'm running an ASRock H110M-STX motherboard with an Intel 7265 WiFi/Bluetooth M2 card.  I have created this little tiny machine that I can fit inside a small toughbox and take with me on deployments.  It has a ruggedized 5" screen, whole 9.  The problem is, to be really compact, I counted on bluetooth accessories.  Because I'm security-conscious (paranoid) I'm using the encrypted boot.  My bluetooth card isn't enabled until after I enter my encryption key.  It kinda defeats the purpose to have a big ol' usb keyboard just to enter my encryption key, so I'm trying to figure out how to enable the bluetooth card at boot, instead of with the OS.  I tried going into the BIOS, but I guess since it's not onboard it's not an option.  I tried going through startup applications, but since that is after the crypt, it didn't help.  I've tried a couple different code strings through terminal, but they all seemed aimed at enabling bluetooth at startup, instead of boot.  've looked at support documentation for the 7265, but it's aimed at Windows; and I've searched the forums.  Everything I found was to make the card do what mine is already doing.

So tech wizards of the ubuntu world.  How can I make a device be activated by the BIOS when it's not an option in the BIOS?

---

### Post by praseodym on 2017-07-31
Until 14.04 the boot option "text"/"textonly" booted into a console into an interactive mode *with* networking. If bluetooth ever worked with that: No idea

There is still this boot option available:

```
	rfkill.default_state=
		0	"airplane mode".  All wifi, bluetooth, wimax, gps, fm,
			etc. communication is blocked by default.
		[COLOR="#FF0000"]1	Unblocked[/COLOR].
```
[https://www.kernel.org/doc/Documentation/admin-guide/kernel-parameters.txt](https://www.kernel.org/doc/Documentation/admin-guide/kernel-parameters.txt)

---

### Post by jeremy31 on 2017-07-31
I doubt if it is possible to use a bluetooth keyboard at boot time especially since most bluetooth chipsets need firmware loaded to function.  It is possible that a Logitech wireless keyboard that has its own dongle might work as the computer usually just sees them as a USB keyboard

---

### Post by him610 on 2017-08-01
> Logitech wireless keyboard

Recommend Logitech K400.

---

### Post by mercenarycor on 2017-08-08
> **praseodym said:**
> Until 14.04 the boot option "text"/"textonly" booted into a console into an interactive mode *with* networking. If bluetooth ever worked with that: No idea

There is still this boot option available:

```
    rfkill.default_state=
        0    "airplane mode".  All wifi, bluetooth, wimax, gps, fm,
            etc. communication is blocked by default.
        [COLOR=#FF0000]1    Unblocked[/COLOR].
```
[https://www.kernel.org/doc/Documentation/admin-guide/kernel-parameters.txt](https://www.kernel.org/doc/Documentation/admin-guide/kernel-parameters.txt)

I've seen this command string before, wouldn't this go into effect after the secure boot cryptokey is entered?

---

