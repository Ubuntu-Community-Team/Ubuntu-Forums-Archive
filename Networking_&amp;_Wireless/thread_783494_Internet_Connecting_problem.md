---
title: "Internet Connecting problem"
date: 2008-05-05
forum: Networking &amp; Wireless
---

### Post by thebrokenbox on 2008-05-05
So I have just installed Ubuntu with the use of Wubi. I go to connect to the internet on my first boot up and I can't connect. I go to my network options and it seems a though it doesn't even recognize my modem. I have fine internet connections on my Vista but when I go to ubuntu it doesn't want to connect. I have read over lots of other threads but none of them are working. I can't really find where to see what my driver is since it came with my laptop so I have no idea what to do. argh I want to get this working. My computer is a Toshiba laptop. I'm a complete noob with Ubuntu so all help is appreciated. Hopefully someone can point me in the right direction :D Thanks

Edit: My driver is Atheros AR5007EG, at least I think. Still waiting for some help on this one.

---

### Post by Ayuthia on 2008-05-05
You can go into the terminal and type lspci -nn.  It will list your PCI cards along with their id numbers.  Look for Network Controller, Ethernet Controller, or wireless.

If it is an Atheros card, you can try this link:
[http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html](http://www.ubuntugeek.com/atheros-ar5007-wireless-with-madwifi-on-ubuntu-804-hardy-heron.html)

---

### Post by thebrokenbox on 2008-05-10
I tried that but it still hasn't worked. I'm about to give it a go by putting the inf and sys files for the driver on my pen drive then just reboot and install them from my pen drive. I am really confused and that's basically my last idea to fix this. Any other suggestions would be GREATLY appreciated.

---

### Post by thebrokenbox on 2008-05-10
ok so I just reboted and tried to do it again but I got an error message. Now I think it was just ndiswrapper issues but I don't really know. So I just downloaded thelatest ndiswrapper and I guess I will try again.

---

### Post by thebrokenbox on 2008-05-10
can anyone help me?

---

