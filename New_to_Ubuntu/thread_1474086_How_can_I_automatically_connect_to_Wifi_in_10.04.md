---
title: "How can I automatically connect to Wifi in 10.04?"
date: 2010-05-05
forum: New to Ubuntu
---

### Post by Mongoose088 on 2010-05-05
Hello everyone,

I am currently using Ubuntu 10.04. I connect to the internet by the following method:

Boot up Ubuntu with my wireless switch turned off.
Load up terminal, and use the command, "rfkill unblock all"
Turn on my wireless switch.

This is the only way I can get my wireless to connect. I feel like there is a proper way to correct this issue so it will connect automatically. Could you tell me how to automatically connect to wifi without playing with the switch and entering terminal commands?


As an aside, I use an Intel 5300 Card.

Thanks!

---

### Post by cgroza on 2010-05-05
> **Mongoose088 said:**
> Hello everyone,

I am currently using Ubuntu 10.04. I connect to the internet by the following method:

Boot up Ubuntu with my wireless switch turned off.
Load up terminal, and use the command, "rfkill unblock all"
Turn on my wireless switch.

This is the only way I can get my wireless to connect. I feel like there is a proper way to correct this issue so it will connect automatically. Could you tell me how to automatically connect to wifi without playing with the switch and entering terminal commands?


As an aside, I use an Intel 5300 Card.

Thanks!

OK, go to System, Preferences, Startup Applications and add your command there... Now you still have to do the same steps but skip that command because it will run itself at startup, just give it 3 second after the computer finished booting and then turn you wireless card on... All this saves you from opening a terminal each time you boot.

---

### Post by spydeyrch on 2010-05-05
Have you searched the hardware drivers for proprietary drivers? Go to System -> Admin -> Hardware. It will do a search for your hardware and if available, will give you a list of the drivers that your system could use to get better performance/activate/use a peice of hardware. Also, make sure that your wireless switch is turned ON prior to doing the search. Hopefully that helps.

This is how I did it for my friends laptop and now it can connect automatically every time to her wireless network.

Let us know how it goes.

-Spydey :lolflag:

---

