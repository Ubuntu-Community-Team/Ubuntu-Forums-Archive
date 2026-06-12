---
title: "Bluetooth cannot be turned on after I turned it off"
date: 2009-11-13
forum: New to Ubuntu
---

### Post by tduccuong on 2009-11-13
Hi all,

I am newbie and I just installed ubuntu 9.10 on my Lenovo IdeaPad S12. Everything works fine until today I accidentally turned the bluetooth off, and could not turn it on after that. I am using Blueman from Repo. I have tried every possible ways including remove bluetooth all and reinstall gnome-bluetooth. But nothing works. On a new restart, the bluetooth icon is there but greyed out. I did not find any means to turn it on...

Any suggestion is very much appreciated. 
Thank you all!

---

### Post by walmis on 2009-11-13
Install blueman from PPA. Open up software sources and add **ppa:blueman/ppa**
This bug will be fixed after that. And don't forget to restart your session after upgrade.

---

### Post by tduccuong on 2009-11-13
Thank you walmis for your quick reply. I did as you said. I restart the computer but the blueman icon does not show up. In a terminal, I type "blueman-applet" and it says "there is an instance already running"!

What do I do now?

updated:
I am now with my office laptop which is an Ubuntu 9.10 box and bluetooth has been great so far. Just now I got a request for few updates from update-manager. After the update is done, the bluetooth is disabled!!! So I guess it has something to do with some updated packages? Because I think I also did the same update on my home netbook (before the accidental turning off of the bluetooth)...

So any comments?

---

### Post by walmis on 2009-11-13
Could you enter *sudo bluetoothd -nd* in the terminal and check if bluetooth becomes available?
Also could you copy the output from *rfkill list* command

---

### Post by tduccuong on 2009-11-13
Never mind, I solved the prob! I dont know how! What I did is to reinstall gnome-bluetooth (which ofcourse remove blueman at the same time). After reboot the gnome-bluetooth icon shows up disabled. However it gives me an option to enable bluetooth this time. I enabled it and it works! After that, I reinstall blueman again (which removes gnome-bluetooth) and restart the computer. Guess what, things are back to nomarl except that the new blueman icon looks very nice, and it does have few more features compared to the previous one :)

Thank you walmis very much! You saved me a lot of time (I intended to freshly reinstall ubuntu after hours searching on the Internet without luck). Ubuntu community is great, I love Ubuntu!

---

### Post by Tekmoor on 2009-11-14
I'm having the same problems, I even tried the blueman daily ppa (which says that this bug is fixed...) but the bug was still there. I've tried to revert back to bluetooth-applet but now it isn't working properly either... lols...

---

### Post by WitchCraft on 2009-11-14
> **Tekmoor said:**
> I'm having the same problems, I even tried the blueman daily ppa (which says that this bug is fixed...) but the bug was still there. I've tried to revert back to bluetooth-applet but now it isn't working properly either... lols...

you can always use:
```

apt-get remove --purge <packagename>

```

for whatever package you altered
and install the package again.

Another way is:
```

apt-get install --reinstall gnome-applets

```

---

### Post by Tekmoor on 2009-11-14
Thanks for the tip, I did a reinstall of every bluetooth and gnome-applet related package, but the problem persists. #-o

---

### Post by walmis on 2009-11-15
What do *hciconfig -a* and *rfkill list* return?

---

### Post by Tekmoor on 2009-11-15
```
$ hciconfig -a
hci0:    Type: USB
    BD Address: 00:16:44:FE:45:A6 ACL MTU: 1021:8 SCO MTU: 64:8
    DOWN 
    RX bytes:721 acl:0 sco:0 events:27 errors:0
    TX bytes:359 acl:0 sco:0 commands:27 errors:0
    Features: 0xff 0xff 0x8f 0xfe 0x9b 0xff 0x79 0x83
    Packet type: DM1 DM3 DM5 DH1 DH3 DH5 HV1 HV2 HV3 
    Link policy: RSWITCH HOLD SNIFF PARK 
    Link mode: SLAVE ACCEPT 

$ rfkill list
0: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
```Any ideas?
Thanks

---

