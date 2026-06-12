---
title: "Synaptic crashed during update, now there is no network and can't shutdown"
date: 2014-12-07
forum: Networking &amp; Wireless
---

### Post by BigBaka on 2014-12-07
Yesterday I was conducting a general update of Ubuntu 12.04 using synaptic and then it crashed and I had to force restart. Now there are multiple problems, trackpad doesn't work, I can log into the user and run everything but there is no network icon, when I go to system settings and click on network, and error comes up saying "The system network services are not compatible with this version". Also I can't seem to shutdown or restart, when I try the computer simply logs out.

Help! Any advise would be greatly appreciated.

Regards,
BB

---

### Post by Bucky Ball on 2014-12-08
Hello from another BB! ;)

Can you plug a cable in and get online? I suggest ctrl+alt+F1 which will get you to a CLI. If you get that far, and you can get online, then:

```
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo reboot -h now
```

How were you updating with Synaptic? Do you remember at what point it crashed?

One other suggestion. If you can reboot, perhaps by using 'sudo reboot -h now' in the CLI, try booting into the recovery kernel and 'fix broken packages' when you get to the option screen. Take note of any errors you see on the way there. They will flash past fairly quickly, though.

Good luck.

---

### Post by BigBaka on 2014-12-08
Hi Bucky Ball,

Don't have a LAN cable at the moment, but might be able to get one later. Just to let you know, typed in 

sudo apt-get autoremove and got this response

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem

Typed in sudo dpkg --configure -a and got a long read out that included some interesting errors including possible missing firmware etc.

Alas I couldn't get the readout off the computer to post here because the usb flash drive couldn't be read.

---

### Post by Bucky Ball on 2014-12-08
> **BigBaka said:**
> 

Alas I couldn't get the readout off the computer to post here because the usb flash drive couldn't be read.

Hmm. Makes it tricky to diagnose. Hopefully the cable will work if and when you can get one. 

Was there any tidbits of advice at the end of the long readout?

---

### Post by BigBaka on 2014-12-08
Quick update. 

after sudo apt-get autoremove, was able to restart and everything fixed!

Thanks Bucky Ball

---

### Post by Bucky Ball on 2014-12-08
Great news! Thanks for marking as solved and glad to be of help. Enjoy and good luck. ;)

---

