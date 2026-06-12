---
title: "Blue Tooth Disabled"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by Muttly on 2011-07-08
hi guys I wonder if anybody could give me some tips on how to get my Blue Tooth USB dongle to work?

I have installed Natty 64Bit on a A3TION-I mobo (Atom 330), and installed all current updates as of yesterday (7/7/11). In the top right hand corner the blue tooth applet is ghosted and when I click on it get two available options; Enable and preferences (disable is ghosted). When I click preferences I have the option to start the BT but nothing happens. Where do I go now with trouble shooting?

Thanks in advance.

---

### Post by jtarin on 2011-07-08
[Not much help but some.]("https://help.ubuntu.com/community/BluetoothSetup")

---

### Post by Muttly on 2011-07-11
> **jtarin said:**
> [Not much help but some.]("https://help.ubuntu.com/community/BluetoothSetup")

Tried this over the weekend but still no BT. I tried the BT Dongle out on my 10.10 32bit install (USB persistence drive) on another computer and still the same. I think I have a dodgy dongle :), USB stick I mean.
New belkin device now on order, fingers crossed.

---

### Post by mcduck on 2011-07-11
11.04 seems to have some troubles starting the bluetooth interface with some devices. Pop open a terminal (or press Alt-F2 to use the Run dialog) and execute this command:

```
sudo service bluetooth restart
```

If that doesn't enable bluetooth, then run "tail -f /var/log/syslog and plug the bluetooth dongle in & post here whatever messages appeared in the terminal. That should tell us more about the dongle and how the system recognizes it.

---

### Post by Muttly on 2011-07-16
I took the easy way out and ordered the new dongle. I did try the cheap CSR chip set one on my laptop with 10.10 32bit installed with the same result.
The new Belkin dongle was working straight away without any fuss! I have successfully paired this with a Microsoft notebook mouse 5000.

I believe there may be some compatibility issues with the CSR dongle in Ubuntu. The same dongle works on XP!

---

