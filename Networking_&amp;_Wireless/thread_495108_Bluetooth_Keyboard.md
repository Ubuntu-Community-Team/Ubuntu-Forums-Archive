---
title: "Bluetooth Keyboard"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by osarusan on 2007-07-07
Hi, I use a bluetooth keyboard on my tablet PC running Feisty.

I can get the keyboard to connect if I user another keyboard type in sudo hidd --search, but its kind of hard to type before the keyboard is connected!

Is there some way to search for bluetooth devices without having to type a command in the terminal?

Thanks! :-)

---

### Post by linuxwizard on 2007-07-07
Not sure if this will help you

[https://help.ubuntu.com/community/BluetoothSetup](https://help.ubuntu.com/community/BluetoothSetup)

---

### Post by osarusan on 2007-07-07
Well, that helped me in so much as it told me how to connect the keyboard. It was useful, but it doesn't tell me how I can connect it without having to use a terminal. Since it's a tablet pc, I wont be able to lug a keyboard with me wherever I go, so I'd really like a method of doing it that doesn't requre typing. Any other options?

---

### Post by jackocleebrown on 2007-07-08
Hi,
Are you feeling brave?
You might be able to create a udev rule so that when you plugin the keyboard the required command is automatically executed by the "hotplug" system. I managed to do a similar thing - I wanted to automatically mount a usb HD when the my sever was turned on, normally external HDs are only mounted when you login which is a pain in the **** on a server.

My solution is here [http://ubuntuforums.org/showthread.php?t=339178](http://ubuntuforums.org/showthread.php?t=339178) along with some links to manuals explaining how to write udev rules.

Good luck!

---

