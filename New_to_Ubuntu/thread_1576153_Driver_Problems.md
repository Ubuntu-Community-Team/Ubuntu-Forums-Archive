---
title: "Driver Problems"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by itsvan on 2010-09-16
HI there,,im running Ubuntu Lucid, on a Nvidia Geforce 7800 GT.
It seems that when i install any of the hardware drivers on the list that it gives me they dont work,when i reboot the pc it takes me to a black screen resembling terminal, and i cant boot back into normal ubuntu. it seems it messes up the drivers and i cant find a way to restart x server successfully, so i have to completely reinstall ubuntu each time.:-k
i need a way to install a working driver, if not i cant run any effects or any of that cool stuff. HELP!!!!!!

these are the pre-set driver options it gives me ( Nvidia accelerated graphics driver version 173/93 and version current,recommended) none of them WORK! ):P

---

### Post by sandyd on 2010-09-16
> **itsvan said:**
> HI there,,im running Ubuntu Lucid, on a Nvidia Geforce 7800 GT.
It seems that when i install any of the hardware drivers on the list that it gives me they dont work,when i reboot the pc it takes me to a black screen resembling terminal, and i cant boot back into normal ubuntu. it seems it messes up the drivers and i cant find a way to restart x server successfully, so i have to completely reinstall ubuntu each time.:-k
i need a way to install a working driver, if not i cant run any effects or any of that cool stuff. HELP!!!!!!

these are the pre-set driver options it gives me ( Nvidia accelerated graphics driver version 173/93 and version current,recommended) none of them WORK! ):P
is it a GS, SLI or a GTX. Because the nvidia site does not have your card listed.

---

### Post by papibe on 2010-09-16
You don't have to reinstall Ubuntu every time that happens. You can tell X not to use the nvidia driver by removing (or renaming) the xorg file.

If you get a black screen, type Alt-Crtl-F1 to get a text screen. Login with your user. Then rename the xorg file:
```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.cong.old
```
Then kill the graphic UI:
```
$ sudo service gdm stop
```
(change gdm for kdm if you're using Kubuntu). Then restart:
```
$ sudo service gdm restart
```

Regards.

---

### Post by itsvan on 2010-09-17
@sandyd I read my card and it says only GT..so i don't know if maybe a GTX driver might work with it? i couldn't find it on the site either, it physically looks the same, if that helps...:p

@papibe ok il try that next time it happens thanks.....:D

any other recommendations?

---

### Post by papibe on 2010-09-17
> any other recommendations? 

Check how the card it's being recognized:
```
$ sudo lshw -class display
```

---

### Post by itsvan on 2010-09-17
*-display               
       description: VGA compatible controller
       product: G70 [GeForce 7800 GT]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list rom
       configuration: driver=nouveau latency=0
       resources: irq:16 memory:fb000000-fbffffff memory:d0000000-dfffffff(prefetchable) memory:fc000000-fcffffff ioport:bc00(size=128) memory:fd000000-fd01ffff(prefetchable)

---

### Post by Lateralis on 2010-09-17
Looks like you're using the Open source (noveau) driver.  When you go System -> Administration -> Hardware Drivers do you see the option of installing the proprietary driver? I see two packages in the main repo which with closed source Nvidia drivers: 

[nvidia-96]("http://packages.ubuntu.com/lucid/nvidia-96")
[nvidia-173]("http://packages.ubuntu.com/lucid/nvidia-173")

Unfortunately, I don't know if either, neither or both will work with your card, but both pages suggest they cover the GeForce 7 cards.  Also, looking through the documentation for my nvidia graphics driver (I *think* it is the 173 package, but documentation is unhelpfully called nvidia-current in /usr/share/doc so really who knows?!) the 7800 GT is supported.  

My guess then is to use the closed source nvidia driver.  If you aren't given the option to use it in the Hardware Drivers section, you could try installing it through Synaptic/Aptitude.  Probably start with nvidia-173 first.  If that doesn't work, then try the 96 package.

---

### Post by papibe on 2010-09-17
What Lateralis said:
> configuration: driver=**nouveau** latency=0

Make sure your /etc/X11/xorg.conf has a line like this:
```
Section "Device"
    ...
    Driver         "nvidia"
    ...
EndSection
```

Good Luck!

---

### Post by itsvan on 2010-09-17
Sorry im a bit confused, so what exactly do i do???](*,)

---

### Post by barney385 on 2010-09-17
Here's one option: [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)

---

### Post by sandyd on 2010-09-17
> **Lateralis said:**
> Looks like you're using the Open source (noveau) driver.  When you go System -> Administration -> Hardware Drivers do you see the option of installing the proprietary driver? I see two packages in the main repo which with closed source Nvidia drivers: 

[nvidia-96]("http://packages.ubuntu.com/lucid/nvidia-96")
[nvidia-173]("http://packages.ubuntu.com/lucid/nvidia-173")

Unfortunately, I don't know if either, neither or both will work with your card, but both pages suggest they cover the GeForce 7 cards.  Also, looking through the documentation for my nvidia graphics driver (I *think* it is the 173 package, but documentation is unhelpfully called nvidia-current in /usr/share/doc so really who knows?!) the 7800 GT is supported.  

My guess then is to use the closed source nvidia driver.  If you aren't given the option to use it in the Hardware Drivers section, you could try installing it through Synaptic/Aptitude.  Probably start with nvidia-173 first.  If that doesn't work, then try the 96 package.

> **barney385 said:**
> Here's one option: [http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/howto-install-nvidia-drivers-manually-on-ubuntu-10-04-lucid-lynx.html)
won't work.
his card is not listed as one of those supported by the Nvidia Drivers. The ones that ubuntu uses are the same drivers on the nvidia site. The nvidia site does not list his card as supported. Therefore, neavou is the only option.

you might wanna file a support ticket or something with nvidia to ask about this.

---

### Post by itsvan on 2010-09-20
so im pretty much screwed?? lol

---

### Post by papibe on 2010-09-20
If I were you, I'd go to the Linux section of the NV forum, and ask for a definitive answer whether it is supported or not. Being optimistic... may be just requires some special options on the xorg.conf file.

[INDENT][nV News Forums]("http://www.nvnews.net/vbulletin/")[/INDENT]

---

