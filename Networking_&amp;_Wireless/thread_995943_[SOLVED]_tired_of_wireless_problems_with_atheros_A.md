---
title: "[SOLVED] tired of wireless problems with atheros Atheros AR242x"
date: 2008-11-28
forum: Networking &amp; Wireless
---

### Post by inxygnuu on 2008-11-28
Hello, I have been using Ubuntu for a couple of months now, and have only 1 problem. My wireless. I tried madwifi, and this is my problem: (I tried this on Ubuntu hardy and intrepid, 2 different installations) I install madwifi, and reboot. after the reboot, everything works fantastic! then, after another reboot, it won't even do anything. hat am I doing wrong? I have an Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter [168c:001c] (rev 01).

Thanks in advance,
Evan;)

---

### Post by Racer-X on 2008-11-28
I have the same card.

If your laptop has it, have you tried pushing the seemingly useless wireless button on keyboard? Mine's usually orange and, based on it being blue while 'on' in Vista, I figured it was useless.

I've been having the same problems as you, and found that the button seems to have functionality after all.  Open up your system logs and watch for any changes when you hit - I found the gui version in System -> Admin -> System Log to be great as logs that have activity are enboldened.

Anyway, from stock, I'm only running the latest madwifi drivers at [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3875-20081105.tar.gz).

Make sure you disable the stock atheros madwifi drivers in System -> Admin -> Hardware Drivers.

Install the new madwifi package

Add ath_pci and wlan_scan_sta to /etc/modules

Reboot

See if you get anything, and, if not, try hitting the button and waiting 20-30 seconds...

The button seems to have functionality afterall...

---

### Post by inxygnuu on 2008-11-29
Thank you, but it didn't work. and i don't have a button, it is a switch.

---

### Post by inxygnuu on 2008-11-29
ok. thats it.:mad: I have tried everything!:mad:

---

### Post by kaffeboy on 2008-11-30
dudes! take it easy... get on ethernet

Note: You should be on 8.10 Intrepid Ibex:
what you need to do is the following...go to System -> Administration -> Synaptic Package Manager.

When it opens, look for the searchbox and type: 

**linux-backports-modules-intrepid-generic**
After downloading and installing...reboot.
Then go to HAL (System->Administration->Hardware Drivers) and disable the Atheros 802.11 card support and reboot again.

Voila! You now have wireless on your machine!:KS

---

### Post by inxygnuu on 2008-11-30
thank you all, but I think i may have it!:):popcorn::KS

this is where i got my info:[ my source]("http://madberry.org/2008/08/how-to-get-atheros-ar242x-wireless-to-work-2/")

I will try a couple more days and see if this works. I know that it wont work when the kernel is updated and i will have to repeat the process.

Be cool,
3v4n

---

