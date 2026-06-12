---
title: "cant find NVIDIA Geforce 6100 nforce 430 drivers for ubuntu 8.10"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by zebanon on 2009-01-20
hiiiii frnds,
   I am a new to ubuntu.I have installed ubuntu 8.10 dual boot with XP.
To install my NVIDIA drivers i went to System>Administration>Hardware drivers.There were two options available:
1.NVIDIA accelerated graphics driver (version 173)
2.NVIDIA accelearted graphics driver(version 177) **[Recommended]**
  So,thinking that **version 177** drivers are recommended , i downloaded and installed them.When i saw its NVIDIA chipset support it was **Geforce 6150 SE nforce 430**.Mine chipset is** Geforce 6100 nforce 430.** Also my screen reso changed from 1280*1024 to 640*480
 Now i uninstalled **version 177** and installed **version 173** but then also same thing happened as before.Even this supports chipset Geforce 6150. I have also searched the forums but cannot get any answer.
 In suse i got the option of downloading NVIDIA drivers version 172 but i cant find them on net and dont know the method to install:(
plz help me
 thnkx in advance!!

---

### Post by andamaru on 2009-01-20
the 6100 is the same as the 6150 (mostly the same). The did you try opening administrator resolution configuration menu.

I hate an 6100 and that works with the 172, 177, 180 drivers

---

### Post by zebanon on 2009-01-20
i tried to change reso through system>Preferences>screen resolution
but there was no option of 1280*1024.Atleast 1024*768 resolution was also not available . Only two resolution were available
i.e 640*480 n other was even smaller
There is no problem with installaton but there is problem with resolution

---

### Post by TunaCanTommy on 2009-01-20
If you know how to open a terminal window, do that. Then type > sudo nvidia-settings, enter your password (you won't see the characters you type) and a window for Nvidia Settings will pop-up ( a GUI ) the selection of available resolutions can be made there.

---

### Post by zebanon on 2009-01-23
> **TunaCanTommy said:**
> If you know how to open a terminal window, do that. Then type , enter your password (you won't see the characters you type) and a window for Nvidia Settings will pop-up ( a GUI ) the selection of available resolutions can be made there.

yes i have tried that too.There is no option of 1280x1024 in X SERVER Display configuration. I want to change it manually now by editing the xorg.config but dont have step by step procedure to do so

---

### Post by FunkyFrank on 2009-04-11
Hi all,

I had the exact same issue, the 1280x1024 resolution option had disappeared after I went to Intrepid, the following article helped solve the prob 100%:
[http://ubuntuswitch.blogspot.com/2008/12/ubuntu-810intrepid-change-default.html](http://ubuntuswitch.blogspot.com/2008/12/ubuntu-810intrepid-change-default.html)

It's not the driver, it's in the monitor settings, so after making the change like this, it worked:
Section "Monitor"
Identifier "Monitor0"
VendorName "Unknown"
ModelName "___"
HorizSync 30.0 - 70.0
VertRefresh 60.0
EndSection

in my case
Section "Monitor"
Identifier "Monitor0"
VendorName "Samsung"
ModelName "SyncMaster 920N"
HorizSync 30.0 - 70.0
VertRefresh 60.0
EndSection

Boy, was I happy!!

:-\"
Cheers
Frank

---

