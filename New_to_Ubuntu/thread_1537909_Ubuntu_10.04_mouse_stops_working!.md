---
title: "Ubuntu 10.04 mouse stops working!"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by PWalton on 2010-07-24
After roughly 2-10 minutes. It's so annoying, and has made my other computer unusable, as you have to shut it down. I think the keyboard also stops working as ctrl+alt+delete doesn't work, so i have to turn it off by the power button on front.


Thanks for any help.

Kind of not keen on ubuntu at the moment...someone PLEASE HELP! So i can like it..

---

### Post by PWalton on 2010-07-24
Anybody?

---

### Post by pagarbuk on 2010-07-24
What kind of connector does your mouse use?  I was using a PS/2 mouse until it died recently.  Sort of died, it could still click things, but it wouldn't move.  After switching to USB mouse, I haven't had any problems *knock on wood*.

---

### Post by mkvnmtr on 2010-07-24
When I have mouse or keyboard problems the first thing I do is plug in another mouse or keyboard to see if it is a hardware problem. So far it has always been hardware.

---

### Post by PWalton on 2010-07-25
> **pagarbuk said:**
> What kind of connector does your mouse use?  I was using a PS/2 mouse until it died recently.  Sort of died, it could still click things, but it wouldn't move.  After switching to USB mouse, I haven't had any problems *knock on wood*.


Hey, thanks for the reply. I'm using a USB mouse.

Still no solution.

SOmeone help please!

---

### Post by nathan.osborn1 on 2010-07-25
I have the same problem with my Toshiba NB305....every five to ten minutes my keyboard and mouse just stop working. I don't use a USB mouse just the pad that is on my laptop. It dosen't matter what I do I cannot seem to figure out how to keep it from doing it. As long as I keep moving then its fine. I know its not my screensaver because it is set for two hours. Any ideas on a fix would be greatly appricated.

---

### Post by brodiewells on 2010-10-02
I have this problem also, any help would be great!  Thanks.

---

### Post by Flos Headford on 2010-10-08
Yep! Just did an OpenOffice update. After wrecking grub, mouse is now frozen in Ubuntu 10.04, working in Win2k.
Even did reinstalls - no luck.

Flos

---

### Post by owenll on 2010-10-08
> **PWalton said:**
> After roughly 2-10 minutes. It's so annoying, and has made my other computer unusable, as you have to shut it down. I think the keyboard also stops working as ctrl+alt+delete doesn't work, so i have to turn it off by the power button on front.


Thanks for any help.

Kind of not keen on ubuntu at the moment...someone PLEASE HELP! So i can like it..

This is a common problem - over a hundred pages of discussion on this thread:

[http://ubuntuforums.org/showthread.php?t=1478787](http://ubuntuforums.org/showthread.php?t=1478787)

---

### Post by hannaman on 2010-10-08
What other USB peripherals do you have plugged in?  When this happened to me, I tracked it down to my phone being mounted via USB.  Since I stopped plugging my phone into USB, I haven't had any mouse problems.

---

### Post by captain_rob on 2011-03-11
Same problem here with a logitech usb mouse. For the rest only a usb logitech keyboard is plugged in. 


**dmesg shows:**
............
[10259.720047] usb 2-2: reset low speed USB device using ohci_hcd and address 76
[10296.795656] usb 2-2: USB disconnect, address 76
[10297.182537] usb 2-2: new low speed USB device using ohci_hcd and address 77
[10297.403747] usb 2-2: configuration #1 chosen from 1 choice
[10297.411520] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/input/input188
[10297.411781] generic-usb 0003:046D:C03D.00BA: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-2/input0
[10397.689094] usb 2-2: USB disconnect, address 77
[10398.080048] usb 2-2: new low speed USB device using ohci_hcd and address 78
[10398.273182] usb 2-2: configuration #1 chosen from 1 choice
[10398.289606] input: Logitech USB-PS/2 Optical Mouse as /devices/pci0000:00/0000:00:13.0/usb2/2-2/2-2:1.0/input/input189
[10398.292488] generic-usb 0003:046D:C03D.00BB: input,hidraw0: USB HID v1.10 Mouse [Logitech USB-PS/2 Optical Mouse] on usb-0000:00:13.0-2/input0

And this goes on and on till the mouse totally freezes. After unplugging and plugging in the mouse works again for a while. 

What's the matter and how to solve this very annoying problem?

:(

---

