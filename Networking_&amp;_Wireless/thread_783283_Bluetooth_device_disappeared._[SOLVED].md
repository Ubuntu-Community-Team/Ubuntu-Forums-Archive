---
title: "Bluetooth device disappeared. [SOLVED]"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by oiper on 2008-05-05
I hope this can help someone. My bluetooth was simply gone this morning with Hardy.

Finally I ran:

```

sudo -i
echo "enabled" > /proc/acpi/ibm/bluetooth

```

Some people accomplished the same by booting into Windows and using their bluetooth utility to turn the device back on. If this other way works, you'll feel a little less slutty. I have no idea why it turned off. The physical switch, a reboot, a complete power off/take battery out, /etc/init.d/bluetooth, rmmod bluetooth/rfcomm/l2cap, nothing helped but the proc enable.

Thinkpad Lenovo T61

---

### Post by Gumm on 2008-05-12
I had the same issue on my Dell M6300. Bluetooth dead as a doornail until I enabled it in Windows. Now all is rosy again. Thanks for this post. I don't know where or how to do this the 'Ubuntu way" tm.

---

### Post by oiper on 2008-05-13
The command above should work. (I had to edit it just now) I also found that the FN+bluetooth button on my Thinkpad will turn it back on. Never thought to try it before. Though if I use that button to turn off bluetooth, my wireless dies.

---

### Post by guntbert on 2008-05-22
> **oiper said:**
>  I also found that the FN+bluetooth button on my Thinkpad will turn it back on. Never thought to try it before. Though if I use that button to turn off bluetooth, my wireless dies.

On my T60 FN+F5 ist a 4 step walkaround: WL on/ BT off - WL off/BT on - WL on/BT on - WL off/BT off

---

### Post by terrybbarton on 2011-02-11
I am also having the problem that my bluetooth disappeared and I don't even know why. I want to get it working again. I went to the Ubuntu Software Center and installed it "Bluetooth" so it is once again found in system>preferences however the icon is not back in the is it called a "tool tray"? When I pair my phone and then choose my computer from my phone's bluetooth menu I get "This device has no supported service" and it used to work before my computer lost it's bluetooth.

Any help is appreciated. I am desperately trying to get away from a proprietary OS developed by a nameless company that treats their legitimate paying customers as though they were their enemys. However I have built up years of expertise so problem solving is so much more difficult for me in Ubuntu as a newbie that doesn't know anything, rather than an OS whose lineage I have used for thousands of hours over decades.

---

