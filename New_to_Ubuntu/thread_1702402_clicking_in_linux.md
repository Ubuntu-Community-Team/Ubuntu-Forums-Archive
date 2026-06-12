---
title: "clicking in linux?"
date: 2011-03-07
forum: New to Ubuntu
---

### Post by adduds on 2011-03-07
I have an acer aspire 5820TG and when i'm in ubuntu there's this weird clicking noise all the time but it doesn't happen in windows I've read it could be power management? or hd head parking? is there somewhere i can get more info on disabling or changing this?

has anyone had experience with this weird clicking?

My harddrive is a WD6400BEVT

just wondering why it doesn't happen in windows but does in linux??

edit: this is happening when i'm running on battery power btw :)

---

### Post by Sef on 2011-03-07
What are your system specs?

---

### Post by adduds on 2011-03-07
Ty for the prompt response!


Acer aspire 5820TG
i5 460m
Radeon HD5650
4gb DDR3
640GB HDD
64bit ubuntu

Here's directly from the website...

AS5820TG-7357 Genuine Windows® 7 Home Premium , 64 bit version, English/French OS (user must make one-time choice of language on first start-up); Intel® Core&#8482; i5-460M Processor (3MB L3 cache, 2.53GHz with Turbo Boost up to 2.8GHz, 35 W) ; 4GB (2/2) DDR3 SDRAM; 640GB hard drive; integrated Super-Multi drive; 5-in-1 card reader; 15.6" HD+ (1366 x 768), high-brightness (220-nit) TFT LCD; ATI Mobility Radeon&#8482; HD 5650 with 1024 MB of dedicated DDR3 VRAM, supporting Unified Video Decoder (UVD), OpenEXR High Dynamic-Range (HDR) technology, Shader Model 5.0, Microsoft® DirectX® 11; 802.11b/g/n WLAN, 10/100/1000 LAN, webcam, Bluetooth.

---

### Post by adduds on 2011-03-09
did these specs help or did you need more info??

---

### Post by 3177 on 2011-03-09
back when I used 9.10 I'd hear noises when I exited applications. Haven't heard it on anything newer though. Check compiz settings.

---

### Post by adduds on 2011-03-09
no it's constant click-click....10-15secs click-click.....only on batter power in linux......

---

### Post by Nytram on 2011-03-10
It might be the hard drive spinning down when idle, that used to cause a clicking noise on my netbook. You can try changing the option in **Preferences/Power Management.**

---

### Post by adduds on 2011-03-10
> **Nytram said:**
> It might be the hard drive spinning down when idle, that used to cause a clicking noise on my netbook. You can try changing the option in **Preferences/Power Management.**

yes i did do that thanks for the idea! but it didn't works i've read it might have to do with power saving and hard drive head parking (not sure what that is)

---

### Post by adduds on 2011-03-11
seriously this is soooo annoying having my hard drive click

---

### Post by HermanAB on 2011-03-11
Howdy,

If the machine is working properly, then stop the syslog daemon.  That will stop the clicking.

---

### Post by rowland on 2011-03-11
My HD clicks too, not very loud, but i consider it normal, and only when its "thinking" or working on something.

---

### Post by adduds on 2011-03-11
> **HermanAB said:**
> Howdy,

If the machine is working properly, then stop the syslog daemon.  That will stop the clicking.

i went to system moniter and could not find a syslog daemon? thanks to all helping!

---

