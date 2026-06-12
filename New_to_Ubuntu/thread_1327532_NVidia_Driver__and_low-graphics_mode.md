---
title: "NVidia Driver  and low-graphics mode"
date: 2009-11-15
forum: New to Ubuntu
---

### Post by Antedeluvian on 2009-11-15
When I open System>Administration>NVIDIA  X Server Settings, this is the message I get
" You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. "

When I try to do this, I get the following message on a black screen "Ubuntu is running in low-graphics mode. Your screen and graphics card could not be detected correctly. You have to configure the display yourself"

Then I do this and no changes are effected. In addition I no longer have sound. Would this be related to the Nvidia card?

I use Ubuntu 8.4 on a rebuilt Dell from Freegeek Vancouver. I would appreciate help working this through step by step

---

### Post by themusicalduck on 2009-11-15
First just to check, can you look under System > Administration > Hardware Drivers to check the driver is in use?

Or did you install the drivers another way?

---

### Post by Antedeluvian on 2009-11-15
> **themusicalduck said:**
> First just to check, can you look under System > Administration > Hardware Drivers to check the driver is in use?

Or did you install the drivers another way?

I found that it was not in use  and enabled it, thanks to your suggestion. I entered the command for the Nvidia Server Settings and  rebooted.  The Nvidia Server Settings now read as they should. 

Now the problem to be solved is the Sound. I have no sound at all. Any advice  what to check for sound?

---

