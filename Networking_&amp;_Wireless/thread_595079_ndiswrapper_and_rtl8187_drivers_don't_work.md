---
title: "ndiswrapper and rtl8187 drivers don't work"
date: 2007-10-28
forum: Networking &amp; Wireless
---

### Post by andrew.pope on 2007-10-28
I have installed the drivers for my RTL8187 USB Wireless card using the win 98 drivers and ndiswrapper. 
when i type
```

sudo ndiswrapper -l (lowercase L)

```

i get the message that it is installed and hardware present and driver present.

however my card does not seem to be in the list when i type

```

lshw

```

just my ethernet card which I do not use as i only use wireless.

then i press CTRL+ALT+F1 to go to the tty and then unplug my card. when i plug it back in i find the source of my error of not being able to detect my card:

```

ndiswrapper (usb_submit_nt_usb:625): usb_get_descriptor() = -110
nsidrwapper (ndis_init_one_usb:191): Windows driver couldn't initialise the device (C0010006)

usb 2-5.3: string descriptor 0 read error: -110

usb 2-5.3: string descriptor 0 read error: -110

usb 2-5.3: string descriptor 0 read error: -110

usb 2-5.3: string descriptor 0 read error: -110

usb 2-5.3: string descriptor 0 read error: -110

usb 2-5.3: string descriptor 0 read error: -110

usb 2-5.3: string descriptor 0 read error: -110

```

I only know a bit about linux - i followed instructions from another site to install and configure ndiswrapper - so all i know is that the device could not be started with the driver. as for the rest of the output i have absolutley no idea! so any help would be greatly appreciated!

also if somebody could tell me what the command

```

sudo

```

means as I can't figure it out!

( i am using Ubuntu Hoary Hedgehog - either 5.4 or 5.04 i forget which!)

thanks in advance for any help offered!

cheers

andy

---

### Post by cubdukat on 2007-11-01
Is the wi-fi card a true USB card, or is it the wi-fi in your laptop?

A lot of laptops that use the 8187 chipset use the 
B" variant, which is the same one as in the USB cards. 

What might help is if you type in iwconfig. If you see something that says wlanX, that means your card is working.

BTW, if I'm not mistaken, sudo comes from the the phrase "SUperuser DO." It's basically the Debian/Ubuntu version of the "su" command, which allows you to perform functions as an administrator. It's a good word--learn it, live it, love it :) If you treat it right, "sudo" is your friend...But only use it when you have to; you can seriously bork your entire system if you aren't careful.

---

