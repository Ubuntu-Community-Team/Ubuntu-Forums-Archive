---
title: "New to Ubuntu..."
date: 2011-09-05
forum: New to Ubuntu
---

### Post by Cyb3rPrince on 2011-09-05
Ubuntu 11.04
Dell 
N4030

the two problem:

bluetooth doesn't work for me i know thats all doesn't work! and i''ve downloaded it ati radeon from support.amd.com then i installed graphics card driver then restarted...i'm play a games but damn slow WTF..:( what to do? 
by the ways, i think terminal said need aticonfige but i dont know how to aticonfig :(

---

### Post by overdrank on 2011-09-05
Hi and welcome, I have moved your post to it's own thread. Moved to Absolute Beginner Talk :)

---

### Post by Cyb3rPrince on 2011-09-05
Oh alright, sorry for the wrong section ..and thanks for welcome :D

---

### Post by _d_ on 2011-09-05
As far as the graphics drivers go, ATI isn't the best thing in the world to be playing games with linux on, however ATI does beat Intel by far.

If you're looking for the best performance with linux gaming, you should consider nVidia as they have the best available linux drivers out of all the 3 major companies.

---

### Post by IWantFroyo on 2011-09-05
Remove the driver you downloaded (Forgot how to do this. Was it a Deb file?), and run Additional Drivers.
If your computer needs a driver, it should be there, and if it's there, it should work properly.

---

### Post by IWantFroyo on 2011-09-05
> **_d_ said:**
> As far as the graphics drivers go, ATI isn't the best thing in the world to be playing games with linux on, however ATI does beat Intel by far.

If you're looking for the best performance with linux gaming, you should consider nVidia as they have the best available linux drivers out of all the 3 major companies.

The Dell N4030 is a laptop. The OP can't open up the computer without breaking his warranty.

Besides, I have an ATI card, and it works perfectly fine. If you have one, there's really no reason to ditch it for nVidia.
Also, ATI cards are slightly better for Linux, since they're more likely to work well without a proprietary driver. On a free-as-in-freedom OS like Fedora, you can sometimes have slowed down nVidia cards.

---

### Post by _d_ on 2011-09-05
> **IWantFroyo said:**
> Remove the driver you downloaded (Forgot how to do this. Was it a Deb file?), and run Additional Drivers.
If your computer needs a driver, it should be there, and if it's there, it should work properly.

If it was from ATI driver website:

```
sudo sh /usr/share/ati/fglrx-uninstall.sh
```

---

### Post by Cyb3rPrince on 2011-09-05
> **_d_ said:**
> As far as the graphics drivers go, ATI isn't the best thing in the world to be playing games with linux on, however ATI does beat Intel by far.

If you're looking for the best performance with linux gaming, you should consider nVidia as they have the best available linux drivers out of all the 3 major companies.


Oh damn it, i'm a fan of ATI! i dont think so, i don't looking for! i'm play a game on windows its ok  :) i need complete my all driver on ubuntu! what to do :(

 i need your help, 

i downloaded version latest ati radeon driver from amd.support.com and i installed then when play video in slow motion WTF! i've uninstalled ati catalyst and driver both then again i open a additional > search for driver > i clicked activate then reboot! now it work i'm tired this all da time i dont know why

> **IWantFroyo said:**
> Remove the driver you downloaded (Forgot how  to do this. Was it a Deb file?), and run Additional Drivers.
If your computer needs a driver, it should be there, and if it's there, it should work properly.

i also using laptop and not computer lol, ok and yes i've installed deb.file and but play slow motion :( by the ways, i dont know how to aticonfig :( u know howto??

thanks guys for your reply :) 
Sorry for my bad english

---

### Post by alphacrucis2 on 2011-09-05
> **Cyb3rPrince said:**
> Oh damn it, i'm a fan of ATI! i dont think so, i don't looking for! i'm play a game on windows its ok  :) i need complete my all driver on ubuntu! what to do :(

 i need your help, 

i downloaded version latest ati radeon driver from amd.support.com and i installed then when play video in slow motion WTF! i've uninstalled ati catalyst and driver both then again i open a additional > search for driver > i clicked activate then reboot! now it work i'm tired this all da time i dont know why



i also using laptop and not computer lol, ok and yes i've installed deb.file and but play slow motion :( by the ways, i dont know how to aticonfig :( u know howto??

thanks guys for your reply :) 
Sorry for my bad english

The Catalyst/fglrx version downloaded from AMD will be newer than the one installed via additional drivers. Can you please open up a terminal window and type:

```
sudo lshw -C display
```

and paste the output back here.

---

### Post by Cyb3rPrince on 2011-09-06
>   *-display               
       description: VGA compatible controller
       product: Manhattan [Mobility Radeon HD 5430 Series]
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:48 memory:c0000000-cfffffff memory:fbe20000-fbe3ffff ioport:e000(size=256) memory:fbe00000-fbe1ffff


ok then?

---

### Post by j*tech on 2011-09-06
[LEFT]Welcome to the forums and Ubuntu community ):P...
[/LEFT]

---

### Post by migs73 on 2011-09-06
About your Bluetooth;
I had issues trying to get it to work on a Dell D830 but eventually found I had to enable it in windows first??. Logged out and back into Ubuntu and I could then enable/disable it. Don't know if this an issue with the way it is enabled or whatever, but try also checking your BIOS settings to see if it is enabled on boot.

Mike

---

### Post by nipunshakya on 2011-09-06
> **migs73 said:**
> About your Bluetooth;
I had issues trying to get it to work on a Dell D830 but eventually found I had to enable it in windows first??. 


I don't think enabling or disabling your bluetooth device can be really helpful...
if OP is in 11.04, then he must probably have the "additional drivers" software installed in your ubuntu(even if u don't you can have it installed from Ubuntu Software Centre) so what i suggest is let the software diagnose available hardwares on your laptop and search for drivers itself....that might find you a way our OP...best f luck...

Regards, NeptuneTech

---

### Post by Cyb3rPrince on 2011-09-07
> **j*tech said:**
> [LEFT]Welcome to the forums and Ubuntu community ):P...
[/LEFT]


Thanks you ;)..

> **migs73 said:**
> About your Bluetooth;
I had issues trying to get it to work on a Dell D830 but eventually  found I had to enable it in windows first??. Logged out and back into  Ubuntu and I could then enable/disable it. Don't know if this an issue  with the way it is enabled or whatever, but try also checking your BIOS  settings to see if it is enabled on boot.

Mike

but i know that, i have dual boot windows and ubuntu...my bluetooth  software does work on windows and but doesn't work on ubuntu :(...i  was checked something all enable :(..thanks for your reply..

> **WinuxUser said:**
> I don't think enabling or disabling your bluetooth device can be really helpful...
if OP is in 11.04, then he must probably have the "additional drivers"  software installed in your ubuntu(even if u don't you can have it  installed from Ubuntu Software Centre) so what i suggest is let the  software diagnose available hardwares on your laptop and search for  drivers itself....that might find you a way our OP...best f luck...

Regards, NeptuneTech

well, i just checked that..there is no bluetooth driver :(...i think ubuntu doesn't supported all bluetooth?

---

