---
title: "Grub_hidden_timeout=0"
date: 2010-04-21
forum: New to Ubuntu
---

### Post by GMHilltop on 2010-04-21
[B]GRUB_HIDDEN_TIMEOUT=0

When I uncomment it and set the time to 10 I thought that it was supposed to hide the menu.

I've read that if the system can't determine if the 'shift' key has been depressed that it will display the menu by default.

Is there any way that I can determine if that is the case?

I've looked at the grub.cfg file after doing the sudo update-grub and I don't see anything in there that suggests that it has been entered into that file by doing the update.

What should I see in the grub.cfg file if I have set [/B][B]GRUB_HIDDEN_TIMEOUT=10 and done the sudo update-grub thing?

thanks
[/B]

---

### Post by GMHilltop on 2010-04-21
Is there a way to tell if it is detecting the keyboard?

---

### Post by kerry_s on 2010-04-21
> Is there a way to tell if it is detecting the keyboard?

look at /var/log/dmesg

i get a line:
> [    1.480362] input: Frexiss Flexis  USB Keyboard as /devices/pci0000:00/0000:00:1d.3/usb5/5-1/5-1:1.0/input/input3

---

### Post by drs305 on 2010-04-21
This is from my Grub 2 Basics thread regarding the "GRUB_HIDDEN_TIMEOUT" option:
> 
On computers on which Grub 2 recognizes multiple OS's:

    * This entry is ignored.
    * The menu will be displayed for the value designated in GRUB_TIMEOUT.
    * The hidden menu timeout option is not available, as it is bypassed by a conditional in /etc/grub.d/30_os-prober.
    * The system can still boot without displaying a menu by setting the GRUB_TIMEOUT value to 0, however a timeout delay with a blank screen is not available.
    * The keystatus check for SHIFT key usage is bypassed by the scripts. Holding down the SHIFT key during boot will not display the menu.
    * If the user of a multi-OS computer wishes to hide the menu while incorporating a blank screen timeout the scripts in /etc/grub.d/30_os-prober can be modified. Please refer to Grub 2 Title Tweaks.

A link to the Title Tweaks thread is available in my signature line (G2-Tweaks).

---

### Post by GMHilltop on 2010-04-21
Opps. :oops:

I kinda blew by the
[INDENT][COLOR=DarkRed]On computers on which Grub 2 recognizes multiple OS's:

    * This entry is ignored.
[/COLOR][/INDENT]...part.  Thanks.

---

### Post by drs305 on 2010-04-21
Just don't ask me why they built it this way...  ;-)

---

### Post by The Cog on 2010-05-01
Thank you, drs305. Your articles are something of a tour de force - excellent. I have a multiboot system but only use one for 99.9% of the time, so I want to hide the menu normally, as I did with grub1.

---

