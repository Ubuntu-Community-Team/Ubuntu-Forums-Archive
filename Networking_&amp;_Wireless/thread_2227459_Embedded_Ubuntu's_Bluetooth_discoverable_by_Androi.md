---
title: "Embedded Ubuntu's Bluetooth discoverable by Android but not iOS"
date: 2014-06-02
forum: Networking &amp; Wireless
---

### Post by (O) on 2014-06-02
I have a system running Ubuntu. The Bluetooth device (hci0) is POWERED, DISCOVERABLE, PAIRABLE, and SCANNING(DISCOVERING). It can discover all devices in the area, Android and iOS. Multiple Android devices can discover and pair to it. However, no iOS devices (iPods and iPhones from multiple generations) can find the Ubuntu's Bluetooth. I have tried to search for this, but all the solutions say "restart your iPod." I've done that many times, I have restarted the Ubuntu system, powered on/off the Bluetooth, toggled its discoverable and discovering modes, etc.

Are there any known issues for this? Is there a setting in the iOS that won't allow it to see certain devices? The iOS devices can see my Ubuntu laptop, running the same version of BlueZ (5.0).

---

### Post by bapoumba on 2014-06-02
Well, I never use Bluetooth.. Just tried with an iPhone 4S, and got it paired with no problem. I choose a custom passphrase and trusted the device. Now I'm not sure what to do with that :)

---

### Post by (O) on 2014-06-03
Thanks for the response, Bapoumba.

> **bapoumba said:**
> Just tried with an iPhone 4S, and got it paired with no problem.

Did you find the Ubuntu system from your phone, or vice versa?  I can pair my device as well, but only from the command line.  I want to initiate pairing from my iOS device because I'm running Ubuntu on a headless system.  Everything also works fine on my laptop, which is also running Ubuntu.

---

### Post by bapoumba on 2014-06-03
> **(O) said:**
> Thanks for the response, Bapoumba.



Did you find the Ubuntu system from your phone, or vice versa?  I can pair my device as well, but only from the command line.  I want to initiate pairing from my iOS device because I'm running Ubuntu on a headless system.  Everything also works fine on my laptop, which is also running Ubuntu.

I found the phone from the GUI on my laptop. Have not tried from command line, I'll have to look how to do that :)

---

