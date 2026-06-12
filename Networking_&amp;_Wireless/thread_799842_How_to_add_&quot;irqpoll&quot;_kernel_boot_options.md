---
title: "How to add &quot;irqpoll&quot; kernel boot options?"
date: 2008-05-19
forum: Networking &amp; Wireless
---

### Post by Yiftos on 2008-05-19
I'm a new bee that started out with 7.04 and 7.10 with my wirless cards working fine. Now I've got a clean install of Hard Heron 8.04 with ndiswrapper 1.52 installed and of course my wirelss card is not working. known BUG: "Soft lockup detected on CPU0!"  
I am told that I need to configure the kernel boot options and add "irqpoll" which is suppose to resolve my RTL-8185 wireless driver from freezing the kernel.

:confused:Can anyone give me some suggestions?

---

### Post by Ayuthia on 2008-05-19
You can update it by going into /boot/grub/menu.lst:
```
gksu gedit /boot/grub/menu.lst
```
Look for lines that look similar to this:
```
title          Ubuntu hardy (development branch), kernel 2.6.24-16-generic
root           (hd0,5)
kernel         /boot/vmlinuz-2.6.24-16-generic root=UUID=8k4o3ilj-3fff-dfae-943j-4332lkj52kl43 ro quiet splash
initrd         /boot/initrd.img-2.6.24-16-generic
```

Add the irqpoll to the end of the kernel line:
```
title          Ubuntu hardy (development branch), kernel 2.6.24-16-generic
root           (hd0,5)
kernel         /boot/vmlinuz-2.6.24-16-generic root=UUID=8k4o3ilj-3fff-dfae-943j-4332lkj52kl43 ro quiet splash irqpoll
initrd         /boot/initrd.img-2.6.24-16-generic
```

and save the file.  You will need to reboot to have to be used.  Your title will be different than mine because I started before the final release of Hardy.

---

### Post by Yiftos on 2008-05-19
Thanks!
I will try it later tonight.
:)

---

### Post by Yiftos on 2008-05-20
I did edit the boot/menu.lst file and rebooted. It did not seem to make a difference. But I do apprecaite the help.:)

---

### Post by JMac82 on 2008-09-02
i second that - adding irqpoll did not help on bootup with ndiswrapper 1.53, hardy, broadcom drivers for wusb54gsv2 wireless usb adapter.

---

### Post by InternetDominus on 2010-03-07
```
gksu gedit /boot/grub/menu.lst
```

Hi,  I have installed Ubuntu 9.10 Karmic Koala on my laptop and wireless connection does not work.  When I use iwconfig, nothing is installed, so I am trying to add a line the menu.lst, but my menu.lst file is empty, so I don't know where to add the line.  Can anyone tell me why my menu.lst is empty?

Thanks!

---

