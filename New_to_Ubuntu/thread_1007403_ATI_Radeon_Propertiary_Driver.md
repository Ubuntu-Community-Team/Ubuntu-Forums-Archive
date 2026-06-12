---
title: "ATI Radeon Propertiary Driver"
date: 2008-12-10
forum: New to Ubuntu
---

### Post by nike007 on 2008-12-10
I have a ATI Radeon graphics card X200 to be exact. So, when i boot up kubuntu tells me to activate the ATI Propertiary Driver for better performance, but when i click to activate nothing happens.

also, i have noted tha Kspread suddenly goes black when i select new blank spreadsheet from the startup wizard, however i can resize the window, but cant see anything coz its all black

sorry for the bad english am in a hurry

thanks
nike007

---

### Post by Michael.Godawski on 2008-12-10
> So, when i boot up kubuntu tells me to activate the ATI Propertiary Driver for better performance, but when i click to activate nothing happens.
Can you please be more specific? Nothing is being downloaded? No messages?
Can you please post the output from:

```
sudo lshw -C display
```

---

### Post by nike007 on 2008-12-10
> ATI/AMD propertiary FGLRX graphics driver

3D-accelerated proprietary graphics driver for ATI cards.

This driver is required to fully utilise the 3D potential of some ATI graphics cards, as well as provide 2D acceleration of newer cards.

this is the window i get when i go to hardware drivers thru k menu .. there is a activate button next to it .. n yea nothing is being downloaded

> Can you please post the output from:
  
Code:
sudo lshw -C display


so this is the output

> *-display UNCLAIMED
       description: VGA compatible controller
       product: RC410 [Radeon Xpress 200]
       vendor: ATI Technologies Inc
       physical id: 5
       bus info: pci@0000:01:05.0
       version: 00
       width: 32 bits
       clock: 66MHz
       capabilities: pm msi bus_master cap_list
       configuration: latency=64 mingnt=8


---

### Post by sydbat on 2008-12-10
Did you reboot after installing the proprietary ATI driver? You have to for it to complete its install.

---

### Post by Pythagoras on 2008-12-10
I remember having a similar problem when I did a fresh install of Ubuntu 8.10.  What I did instead was go to ATI's website, and downloaded the drivers they have for linux.  Brought my FPS up in WoW from 1 to 30.

---

### Post by waspbr on 2008-12-10
I would recommend you use envy, go to terminal and paste this

```
sudo apt-get install envyng-qt
```

it will isntall a program called envy, it will basically handle all the heavy lifting for you, once you installed it you will find it at: Applications>system tools.

good luck

---

### Post by nike007 on 2008-12-11
> **sydbat said:**
> Did you reboot after installing the proprietary ATI driver? You have to for it to complete its install.

reboot hmm. ..   but it never gives me a message saying that install is complete or to reboot

will try envy

thanks
nike007

---

### Post by nike007 on 2008-12-11
@waspbr

thanks envy worked perfectly and now Kspread is also fine

thanks again

---

