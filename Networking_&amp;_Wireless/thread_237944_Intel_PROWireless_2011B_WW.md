---
title: "Intel PRO/Wireless 2011B WW"
date: 2006-08-16
forum: Networking &amp; Wireless
---

### Post by Dana on 2006-08-16
I've read a lot of threads re. wireless pc cards without really finding anything that really pointed me in a productive direction. Also have been reading O'Reilly's Ubuntu Hacks.

I have an old Intel Pro/Wireless 2011BWW pc card. I believe this is supposed to work with the Orinoco driver. I'm not having any success and I've never tried to set up any sort of networking in Linux/Ubuntu.

After the card did not seem to be recognized automatically I installed the ndiswrapper-utils and ndisgtk. I looked for the card driver in Windows, this seemed to be NETWLan5.inf. Installed the driver. I see no indication that the card is being recognized correctly. 

dmesg output is:

  dmesg
[4294886.598000] pccard: PCMCIA card inserted into slot 1
[4294886.598000] cs: memory probe 0xa0000000-0xa0ffffff: clean.
[4294886.605000] pcmcia: registering new device pcmcia1.0
[4294886.807000] orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[4294886.869000] spectrum_cs 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au>, et al)
[4294886.937000] spectrum_cs: Cannot find firmware: symbol_sp24t_prim_fw
[4294886.938000] spectrum_cs: Firmware download failed
[4294887.598000] hermes @ 00010100: Timeout waiting for card to reset (reg=0x0000)!
[4294887.598000] eth1: failed to initialize firmware (err = -110)
[4294887.598000] spectrum_cs: register_netdev() failed


iwconfig output is:


 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.

---

### Post by wieman01 on 2006-08-17
I am afraid you're right, your wireless card has not been recognized.

When installing the native Windows driver using "ndiswrapper" please make sure that ALL driver files (next to "NETWLan5.inf") are in one directory when deploying the *.inf file. I figured that this is necessary, otherwise "ndiswrapper" won't work.

---

### Post by Dana on 2006-08-17
I'm not sure what other files I am looking for. NETWLan5.sys would be the obvious one. Would there be anything else that you know of. Pretty sure this card will work if I get things done correctly.

Thanks,

Dana

---

### Post by wieman01 on 2006-08-17
I think usually these files are *.sys, *.inf, *.cat. But this may be different in your case.

---

### Post by Dana on 2006-08-17
Thanks, I'll check that out and see what I can do. I don't need this card to function at this very moment but I want get this settled for the time it is needed. I have more pressing problems with flaky acpi.

Dana

---

### Post by wieman01 on 2006-08-17
Good luck then. ACPI kept me busy for a while as well. Let us know if you need help.

Cheers / He

---

### Post by Dana on 2006-08-17
I just started rummaging through acpi threads here this morning. I have an older ThinkPad, A22M. Sleep/Suspend was working initially or seemed to. But lately I cannot wake it up more often than not. Power down sometimes fails as well, usually after shutting down LVM services as far as I can tell. 

If I don't pick up a useful thread on acpi I'll get around to starting my own.

Dana

---

### Post by wieman01 on 2006-08-17
Yeah, "suspend" does not seem to work on my end, either, and I have the same problem with the "power button" on my Sony Vaio VGN. Strange thing. Good luck & keep me posted on this one.

---

### Post by Dana on 2006-08-17
I spent several hours trolling the web tonight for a clue how to get this card working. Anything that appeared might be useful was "way" over my head. Unless I run across someone running this card I fear I won't get it working.
pcmcia services seem to be working okay. I don't understand what this means:

spectrum_cs: Cannot find firmware: symbol_sp24t_prim_fw
I also don't understand if the references to Orinoco and Spectrum in the dmesg output indicate these loaded upon detection of the card?

In my search Orinoco and Spectrum come up regularly. Drivers for this card are supposed to be in the kernel if I am understand what I've been reading.

orinoco 0.15rc3 (David Gibson <hermes@gibson.dropbear.id.au>, Pavel Roskin <proski@gnu.org>, et al)
[4294886.869000] spectrum_cs 0.15rc3 (Pavel Roskin <proski@gnu.org>, David Gibson <hermes@gibson.dropbear.id.au>, et al)
[4294886.937000] spectrum_cs: Cannot find firmware: symbol_sp24t_prim_fw
[4294886.938000] spectrum_cs: Firmware download failed

---

### Post by wieman01 on 2006-08-18
> **Dana said:**
> spectrum_cs: Cannot find firmware: symbol_sp24t_prim_fw

Oops... Doesn't look too promising. Appears to be a problem with the version of the native Linux driver you/the kernel are/is using. From what I have learned so far you'll need to disable/unload the Linux driver before you embark on "ndiwrapper". Otherwise it'll conflict.

Since I don't have the same card, I am at my wits' end. Sorry for this.

Another thought: Does the LiveCD recognize your card correctly? Can you connect to your router/network when booting from CD?

---

### Post by Dana on 2006-08-18
Quote:
Originally Posted by Dana View Post
spectrum_cs: Cannot find firmware: symbol_sp24t_prim_fw

This appears whether I let the kernel modules try to handle the card or install the drivers. So everything appears to revolve around symbol_sp24t_prim_fw. And the things I read about that tonight left my head spinning.

I never considered checking the pc card under the Live CD. Thanks for that suggestion.

Dana

---

### Post by wieman01 on 2006-08-18
It's really a version issue I suppose. Try to remove the driver or blacklist it. Then "ndiswrapper" won't be much of a problem (I know I shouldn't say that).

Keep us posted.

---

### Post by Dana on 2006-08-19
No luck with the Live CD. Research tonight is sobering. The card does not seem to be supported in Dapper, nor does ndiswrapper seem to support it. Think I will keep an ear to the ground, maybe hear of someone who was able to make it work. This goes on the back burner and I can begin to see if anything can be done about the flaky acpi standby. Sometimes it works great, other times it just won't wake up again. Power down sometimes hangs just after shutting down LVM. But that is another thread.

Thanks again for the suggestions.

Dana

---

### Post by wieman01 on 2006-08-20
Sorry to hear it. Perhaps keep me updated as far as ACPI is concerned. 

Guess all you can do now is to get yourself a new wireless adapater. Oh well, been through similar stuff as well as others. :-)

---

