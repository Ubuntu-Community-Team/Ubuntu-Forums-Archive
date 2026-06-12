---
title: "bluetooth"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by skt.diaz on 2010-12-02
just cant get my bluetooth working. wifi is working perfectly. i installed gnomebluetooth, bluez, multisync, broadcom sta driver. but still it doesnt work

---

### Post by skymera on 2010-12-02
What are you trying to do with Bluetooth?

Transfer files or use Bluetooth headphones etc

I havrn't used Bluetooth with Ubuntu for years, but before when I plugged my USB Bluetooth dongle in, a icon appeared in the notification bar, I could right click that and send/receive files. Not sure if it's still the same though.

---

### Post by pricetech on 2010-12-02
What release / version are you using.

I'm using Ubuntu Lucid / Edubuntu Lucid and my TrendNet adapters are both working just fine out of the box.  The only thing I installed was bluetooth through Synaptic and I'm able to use my bluetooth earbud, transfer files to and from my phone, as well as other phones, etc.

I can't give you the precise model number since it's not here with me right now, but it does use a broadcom chip for which I did not need a driver.

---

### Post by skt.diaz on 2010-12-02
i hav embedded bluetooth and using ubuntu 10.1. The blueth icon on the panel shows  that blueth is on but cant send or recieve files. In bluetooth preferences thr is a huge 'turn on bluetooth' icon. When i click it nothng happens. My phone doent detect a blueth connect either.

---

### Post by Vege 4wd on 2010-12-07
I am having the same problems as the last post. I would not mind being able to use bluetooth. 

At first bluetooth worked really well with Lucid. After a little while I am having the same problems and no one seems to know why.

---

### Post by gandaran on 2010-12-07
> **skt.diaz said:**
> i hav embedded bluetooth and using ubuntu 10.1. The blueth icon on the panel shows  that blueth is on but cant send or recieve files. In bluetooth preferences thr is a huge 'turn on bluetooth' icon. When i click it nothng happens. My phone doent detect a blueth connect either.
post the output of this code so we can check if you need to install drivers or not.
```
lsusb
lspci
```
 'turn on bluetooth' this doesn't work for some adapters with the default gnome bluetooth, I recommend installing blueman from package manager, blueman does a better job enabling bluetooth power.

---

