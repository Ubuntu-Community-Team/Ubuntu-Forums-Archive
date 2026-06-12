---
title: "Ubuntu 17.1 HP Pav. hardblocked intel 7260HMW no wifi or bluetooth"
date: 2017-11-16
forum: Networking &amp; Wireless
---

### Post by lanceb-bud on 2017-11-16
I'll do my best to skip the back story. I have scoured the net on forums and pages to solve all my problems computers. I am by no means a veteran with linux but after combining various scripts not knowing what exactly I'm doing I have ended up with positive results. This one is different. I have been through various linux distros and will consider using almost any of them if it gets results. I should point out that this machine is basically an over the top Kodi box I do use it for a bit more though. so as long as I dont have to deal with openElec again I'll be satisfied. 

At this point I feel like I have tried everything. I will admit I have not gone through all the post on each forum or even this one for that matter but I have spent months on this issue with no success. The best thing I could hope for at this point is for someone to point out a simple solution that I have missed. 

Ok so things I have done (but am willing to do again if you think it will work) multiple linux distros, the original 7620 card that came with the machine, an Atheros AR9280 that I borrowed from my asus machine, even the original asus wifi card from that machine. I have reset, uninstalled, reinstalled,even to the point of trying exact same steps using different usb ports for my live usb. I have tried booting to a windows start disk with no luck at all I can't seem to make it turn on and I am going insane. And here is where I sit back, answer any questions you have for me and listen. Currently the installation of 17.1 is fresh other than some things I have tried on this forum before finally posting this. thanks and I apologize in advance if I have done some thing wrong other than rambling

---

### Post by jeremy31 on 2017-11-16
See the wireless script link in my signature and post results

---

### Post by lanceb-bud on 2017-11-16
I think this is what you are asking for

---

### Post by jeremy31 on 2017-11-16
Reboot, go into BIOS settings and reset to defaults, if that doesn't help shutdown, remove battery and power cord, then press the power button for 20 seconds.  Put it back together and boot it up

---

### Post by lanceb-bud on 2017-11-16
negative ghostrider the switch is still unchanged

---

### Post by jeremy31 on 2017-11-17
Try editing /etc/modules to remove hp-wmi and then ```
echo "blacklist hp-wmi" | sudo tee /etc/modprobe.d/hp-wmi.conf
```
Reboot

---

### Post by lanceb-bud on 2017-11-17
It's still the same. It shows wireless as an option in the network settings and allows me to click the on off selector but will not stay on.

---

