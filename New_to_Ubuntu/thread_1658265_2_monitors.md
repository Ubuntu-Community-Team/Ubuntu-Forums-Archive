---
title: "2 monitors"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by WrathofTux on 2011-01-02
Hi i have 2 monitors but they show the same thing and the mouse is in both monitors at the same time, is there a way to fix this or can you only have 1 monitor while using ubuntu(gnome) i have ATI radeon HD 5800 series if that helps.

sorry for the noob question :lolflag:

---

### Post by robbiemacg on 2011-01-02
I believe you should be able to solve this problem by navigating to System >Preferences >Display and unchecking the box marked "Same Image in all Monitors."

---

### Post by WrathofTux on 2011-01-02
Don't have a display tab in system->pref :<

---

### Post by Dragyrn1456 on 2011-01-02
if you go to System -> Preferences -> Monitor, there should be an option to deactivate same thing on all monitors. :D:D:D:grin::grin:

---

### Post by dominatorv8 on 2011-01-02
Hi I have the same setup as you. The way i did it was to install the ATI catalyst control center for linux it can be found here:

[http://support.amd.com/us/gpudownload/Pages/index.aspx](http://support.amd.com/us/gpudownload/Pages/index.aspx)

Then once the drivers are installed I ran the Admin version of the Catalyst control center. Go to Display manager and the screens you have connected should appear. Click on one of the down arrows on the top right of the screen icon, go to Multi-Display and click Single display desktop reboot and you should be good to go :) 

Paddy

---

### Post by WrathofTux on 2011-01-02
When i tried fix it directly in monitors they stopped working ill try to do as paddy said brb 50min

---

### Post by WrathofTux on 2011-01-02
ok the file is a .run file but it needs a program to open it, help?

edit: Nvm fixed it

---

### Post by dominatorv8 on 2011-01-02
Here is a nice guide to installing the ATI driver:

[http://www.overclockers.com/ati-driver-installation-linux/](http://www.overclockers.com/ati-driver-installation-linux/)

to execute your .run file, open a terminal navigate to the directory where your .run file is and execute the command sudo sh "file name" 

Paddy

---

### Post by WrathofTux on 2011-01-02
> **dominatorv8 said:**
> Here is a nice guide to installing the ATI driver:

[http://www.overclockers.com/ati-driver-installation-linux/](http://www.overclockers.com/ati-driver-installation-linux/)

to execute your .run file, open a terminal navigate to the directory where your .run file is and execute the command sudo sh "file name" 

Paddy
it works now but all windows and all webbbrowsers started to lagg :/ it also says that the monitors is unknown.

---

### Post by dominatorv8 on 2011-01-02
If your talking about System --> Preferences--> Monitors saying unknown thats fine mine is also doing that. The multi display setting is set in the Catalyst Control Center. I am not sure why it would be lagging perhaps someone more experienced can answer that the only thing i can think of is if you changed the settings in monitors first and also in the Catalyst Control center after and they are some how conflicting however thats a wild guess :p

Paddy

---

### Post by WrathofTux on 2011-01-03
Here i made a video so you can get what i mean, don't know why the screen turns black every 2sec tho(using istanbul)

Youtube block :/

---

