---
title: "Cannot detect wifi networks or obviously connect"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by tiger63 on 2010-12-02
Just got a Dell Inspiron 1545 laptop and installed Kubuntu 10.04 on it, so dual booting with Windows 7.  Went to the library to check out the wifi and Kubuntu couldn't detect any networks.  Rebooted into Windows and detected 7 networks, connected to two of them, then re-booted.  Went to System Settings->Network Settings and clicked on Network Connections, wireless tab, add and in the window that appeared, clicked on scan.  Nothing.  Detected no networks.  I didn't turn off the wireless card with the hotkey combo so I know that wasn't it...but tested anyway and no joy.  Any help for a newbie would be appreciated.

---

### Post by nm_geo on 2010-12-02
System -> Administration -> Hardware Drivers finds you the Broadcom STA proprietary wireless driver.

Can you connect directly to through ethernet cable?

You might do google search on :
dell inspiron 1545 ubuntu wireless driver

It appears the STA driver is your best shot.

---

### Post by tiger63 on 2010-12-02
> **nm_geo said:**
> System -> Administration -> Hardware Drivers finds you the Broadcom STA proprietary wireless driver.
Sorry, my menu doesn't look like that.  There is no "Administration" section or tab or anything like that.

> Can you connect directly to through ethernet cable?
Yeppers.

> You might do google search on :
dell inspiron 1545 ubuntu wireless driver

It appears the STA driver is your best shot.
Okey dokey.  I'll give it a shot.  Thanks for the reply.

---

### Post by MaxTakeoff on 2010-12-02
Hi, on my old Toshiba Satellite (1.7GHz P4), I used ndiswrapper along with the associated driver files - it doesn´t sound like your wireless card is being activated to me.  When you open your network connections window, I don´t think you have to ´add´ your card, it should appear if it is recognized and then you can edit the network connections.

I also had to blacklist some conflicting drivers.  ndiswrapper might be worth a try?

---

### Post by nm_geo on 2010-12-02
> **tiger63 said:**
> Sorry, my menu doesn't look like that.  There is no "Administration" section or tab or anything like that.


Yeppers.


Okey dokey.  I'll give it a shot.  Thanks for the reply.


Hmm.. yes Kubuntu

check here Applications -> System -> Hardware Drivers in Kubuntu

Maybe I am not on my Linux box so just guessing...

---

