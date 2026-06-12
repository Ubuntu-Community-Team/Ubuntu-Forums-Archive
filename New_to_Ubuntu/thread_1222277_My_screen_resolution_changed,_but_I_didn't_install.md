---
title: "My screen resolution changed, but I didn't install anything"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by Dayo6 on 2009-07-24
It just changed from 1280x800 to 1024x768... I don't know why, I just rebooted it.

Any ideas how I can change it back?

I'm pretty fail at ubuntu, xD

Thanks

---

### Post by wojox on 2009-07-24
Did you try System > Prefrences > Display?

---

### Post by Dayo6 on 2009-07-24
> **wojox said:**
> Did you try System > Prefrences > Display?

Yeah, there's only two choices, 800x600 and 1024x768.

---

### Post by LookTJ on 2009-07-24
Did you change your video card or plug the monitor into the wrong card?

---

### Post by Dayo6 on 2009-07-24
> **LookTJ said:**
> Did you change your video card or plug the monitor into the wrong card?

No, and what do you mean by plugging the monitor into the wrong card?

---

### Post by LookTJ on 2009-07-24
> **Dayo6 said:**
> No, and what do you mean by plugging the monitor into the wrong card?
There could be a integrated card(motherboard) and a dedicated chipset(Nvidia/ATi) 

did you receive any updates recently?

---

### Post by Dayo6 on 2009-07-24
> **LookTJ said:**
> There could be a integrated card(motherboard) and a dedicated chipset(Nvidia/ATi) 

did you receive any updates recently?

Nope, but I have an integrated intel.

---

### Post by Dayo6 on 2009-07-24
Bump, there's no easy way to fix this?

---

### Post by LewRockwell on 2009-07-24
sounds like when you started your machine ubuntu didn't "see" your monitor properly so it just used a default

you'll need to do a little investigating and troubleshooting to figure out exactly what's going on

I've solved your problem once or twice by just unplugging and replugging the monitor several times

.

---

### Post by Jim, Canberra on 2009-08-01
Try:
(i) System -> Administration -> Software Sources 
and ensure you check (allow) Proprietary drivers for devices
(ii) Right click on desktop, select Change Desktop Background, Select Visual Effects tab, then if None is selected, you may be in luck
check Extra or even Normal ; this may kick Ubuntu into searching for a driver 
With any luck it will download and install the exact driver you need

(iii) In my case that is the Nvidia driver.
To run it as root and therefore be allowed to save changes, including screen resolution, twin monitors and so on, I set up a screen shortcut with this property
sudo nvidia-settings

Good luck

---

