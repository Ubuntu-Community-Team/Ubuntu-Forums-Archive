---
title: "connecting &amp; pairing bluetoth ubuntu 804"
date: 2008-05-26
forum: Networking &amp; Wireless
---

### Post by hadibn on 2008-05-26
Dear Ubuntu expert , 

    I just install dlink usb bluetoth ubuntu on eeepc , i use some guide :

[http://ubuntuforums.org/archive/index.php/t-640343.html](http://ubuntuforums.org/archive/index.php/t-640343.html)

I try connect manual to bluetoth MS mouse , connecting ok , after few minute the connection is break and i need reconnect manual again. When i reboot the laptop , the bluetoth mouse not auto connect .

    another guide said 

[http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html](http://www.ubuntugeek.com/howto-setup-bluetooth-keyboard-and-mouse-in-ubuntu.html)

If you have followed all the steps above and you find your mouse or keyboard don’t automatically reconnect, we can fix it. Run the following command in a terminal

sudo gedit /etc/default/bluez-utils

Find the following lines

HIDD_ENABLED=0
HIDD_OPTIONS=”…”

Change them to

HIDD_ENABLED=1
HIDD_OPTIONS=”--master --connect KEYBOARD_ADDR --connect MOUSE_ADDR --server”

    I try this guide , after reboot connecting to device ,but when i try reboot for second time ,the mouse not automatic connect to laptop .

    Does any body have idea to solve this problem ?


Thanks

Hadi

---

