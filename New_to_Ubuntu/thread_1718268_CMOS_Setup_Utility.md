---
title: "CMOS Setup Utility"
date: 2011-03-31
forum: New to Ubuntu
---

### Post by aravot on 2011-03-31
I'm trying to setup a 500Gb Flash Drive to boot from.  When I go into American Megatrends CMOS I do not get the option to select the first boot device as "USB", or "Flash Drive", I only get "Boot from Other Device [yes]".

In other words, CMOS shows me this:

Boot Sequence
1st Boot Device    [CD/DVD:3m-HL-D]
2d  Boot Device    [HDD:PM-WDC WD2]
3d  Boot Device    [1st Floppy DRI]
4th Boot Device    [HDD:PM-WDC WD2]

Boot from Other Device [yes]

Being a newbie I'm afraid to take for granted that "Other Device" is my USB port.

What must I do to insure my USB port is selected first?
Thanks!!
Mike

---

### Post by deathadder on 2011-03-31
You can't cause any damage by setting "Other Device" to the first boot option and trying it out. Worst case is you'll need to reboot (Ctrl-Alt-Del) and change the boot option in the bios. As for what "Other Device" actually means, have a read of the motherboards manual. If you don't have it search on the net. 

To get the option to boot from USB it sounds like you'll need to flash you bios with a newer version. You shouldn't have any problems, but make sure you read everything you can about flashing a bios before doing it, because if you do it wrong you can wreck you're motherboard...

Before you do anything though, I would recommend searching the web for your motherboard make and see if it supports USB booting at all. There's no point grabbing the latests firmware and flashing the bios if it won't make a difference! :)

---

### Post by fabricator4 on 2011-03-31
> **aravot said:**
> Being a newbie I'm afraid to take for granted that "Other Device" is my USB port.


"Other Device" normally means a boot PROM on a network card or other device (sic).  It's generally looking for something programmable on the bus, not something in one of the USB ports.

With these BIOS's there's often a key press that you can use to trigger a boot menu, which will then list any devices it finds on USB ports.

The motherboard/BIOS manual is a good place to start if you're not sure, but it will often flash up a post message telling you what key to press.  This key is often something like <Esc>, F12, F1, or similar.  On my Asus Eee-PC it is <Esc>, and this is the ONLY way I can boot a USB device on this machine, and I only found this out by reading the manual.

Chris.

---

