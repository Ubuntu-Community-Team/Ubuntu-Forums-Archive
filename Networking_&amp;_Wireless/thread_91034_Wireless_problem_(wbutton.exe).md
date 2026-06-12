---
title: "Wireless problem (wbutton.exe)"
date: 2005-11-16
forum: Networking &amp; Wireless
---

### Post by lesiano on 2005-11-16
Hello,

I have a Tsunami notebook, and a Intel Pro/Wireless 2100 miniPci 3b.
I've tried to make it work via "modprobe ipw2100" and "ndiswrapper", but it just don't work...

The problem, i think, is the fact that my wireless is activated by sofware and noy by hardware. What I mean is that when i use it in windows, it has to have the process "wbutton.exe" running to activate...
I've already tried to run it using wine, but i can't...

Is there anyone with the same problem?
Is there any "wbutton.exe" to linux?


Tanks
Lesiano


PS I'm sorry for my bad English... :oops:

---

### Post by han_solo330 on 2007-04-17
Hello!

I have the same problem with my  Fujitsu-siemens amilo a 1655g notebook's Atheros AR5005G Wifi card.
My card's driver under Linux is Madwifi. I have already installed it but my card does not work.
Under windows I have a program called Launchap.exe wich manages the hotkeys of my computer.This program is in contact with wbutton.exe and I can turn on my card with this or another button combination.
Probably I need wbuttons's linux version.
Have anybody compiled it yet? Or can I download it from somewhere?

Thanks!

(I'm sorry for my bad english...):)

---

### Post by tturrisi on 2007-04-17
fyi, you do not need ndiswrapper for ipw wifi.  All you need is the linux driver and the firmware, which should already be included in ubuntu.

---

### Post by freak101 on 2007-05-02
> **han_solo330 said:**
> Hello!

I have the same problem with my  Fujitsu-siemens amilo a 1655g notebook's Atheros AR5005G Wifi card.
My card's driver under Linux is Madwifi. I have already installed it but my card does not work.
Under windows I have a program called Launchap.exe wich manages the hotkeys of my computer.This program is in contact with wbutton.exe and I can turn on my card with this or another button combination.
Probably I need wbuttons's linux version.
Have anybody compiled it yet? Or can I download it from somewhere?

Thanks!

(I'm sorry for my bad english...):)
You can try with acer_acpi, it worked for my amilo, take a look at this howto:
[http://ubuntuforums.org/showthread.p...s](http://ubuntuforums.org/showthread.p...s) s+acer_acpi
and
[http://ubuntuforums.org/showthread.php?t=247108](http://ubuntuforums.org/showthread.php?t=247108)

---

### Post by han_solo330 on 2007-08-30
> **freak101 said:**
> You can try with acer_acpi, it worked for my amilo, take a look at this howto:
[http://ubuntuforums.org/showthread.p...s](http://ubuntuforums.org/showthread.p...s) s+acer_acpi
and
[http://ubuntuforums.org/showthread.php?t=247108](http://ubuntuforums.org/showthread.php?t=247108)

Thank you, but I'm afraid, that I destroy my system with that installation ( I'm a quiet newbie)
And my card's compatible driver (madwifi  ath_pci) is originally installed to my kernel.
Should I have change it anyway? 
ok! I will try it, and tell the result.
thank's

---

