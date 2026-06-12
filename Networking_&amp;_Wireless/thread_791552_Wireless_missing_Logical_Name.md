---
title: "Wireless missing Logical Name?"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by kappes on 2008-05-12
Hey everyone,

I have been using ubuntu 7.10 (Gutsy) since it's been released and just the other day I have come across a problem with my wireless pcmcia card in my laptop(inspiron 6000). Basically the built in card went bad about a year ago, so I replaced it with a Dlink 650+ wireless card and ubuntu picked it up and installed it with no problems automatically. Just yesterday I booted up my laptop and it wouldn't pick up my wireless AP nor any other AP around my apartment. I did some further investigating and here is what I have found so far:

Running lshw -C network, identify's my onboard ethernet with logical name eth0, but the wireless card it says it's there but the logical name is blank? It used to be wlan0. I also ran ifconfig and only eth0 and lo show up under that. I tried to run ifconfig wlan0 up and it says wlan0 doesn't exist. I am at loss what to do next to troubleshoot this issue. I don't understand if the card is detected and functioning, why the logcial name would disappear?

Is there some way to set my wireless cards logical name(wlan0) manually to make it work? 

Thanks in advance for any help:)

---

### Post by Ayuthia on 2008-05-12
You might check dmesg to see if any error messages show up.  You might be able to see which logical name it is using by checking /etc/udev/rules.d/70-persistent-net.rules.  

Does lshw -C network show any drivers?  If so, have you checked to see if the module is loaded (lsmod)?

---

### Post by kappes on 2008-05-12
I see you asked if the module is loaded for the card. Now that I think about it, I was messing around with trying to get my laptop to bootup faster and I was disabling some startup programs and I remember disabling "Restricted drivers" from auto starting. Do the restricted drivers have to be running in order for this dlink card to work even if ubuntu installed it automatically out of the box? My laptop is at home so i can't confirm this ATM.

---

### Post by Ayuthia on 2008-05-12
Did you disable the program or the wireless?  If you disable the wireless, it looks like it might remove the firmware.  I have not tried it though.  If you just disabled the program, it should be fine.

---

### Post by chili555 on 2008-05-12
I think Ubuntu installed it automatically out of the box because it installed the restricted drivers. Your card, as far as I can tell, uses the acx111 chipset, which requires that firmware be loaded at every activation. The restricted modules package includes the proprietary firmware. I think if you re-enable Resticted Drivers, you will be up and going again.

---

### Post by kappes on 2008-05-12
Thank you all for the help on this subject it is now solved. I did have my restricted drivers disabled on startup and after reenabling them everything started to function properly. Hopefully thats all it was. Being fairly new to linux I thought that unless you manually installed the wireless driver yourself that restricted drivers weren't needed. Thanks for helping me solve my issue. This ubuntu community is awesome!:)

---

