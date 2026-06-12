---
title: "ATI drivers suck"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by I8NY on 2010-10-07
Well not all ati drivers. Okay i tried to install the ati driver from their website because the one you can get in ubuntu (at least it was easy to install) was having problems with desktop effects on but would cause ANY openGL games to lag.  So i tried to uninstall the ubuntu provided one and had a error "SystemError: installArchives() failed".  I have been getting that every time i try to uninstall it (this is my 4th time doing this) and install the ati driver from the web.  I installed ATI diver but it didn't work and reinstalled the ubuntu one. Problem is that it won't do dual screens or detect the CRTs.  I get both CRTs to display but one shows my original desktop and the other shows a different desktop with different icons. I can interact with both desktops (that means it is not cloned) but it is not stretched desktop like how it is suppose to be. The ubuntu ati driver works but there is no ATI control panel for the graphic now. How do i fix this this big mess up?

---

### Post by alphacrucis2 on 2010-10-07
> **I8NY said:**
> Well not all ati drivers. Okay i tried to install the ati driver from their website because the one you can get in ubuntu (at least it was easy to install) was having problems with desktop effects on but would cause ANY openGL games to lag.  So i tried to uninstall the ubuntu provided one and had a error "SystemError: installArchives() failed".  I have been getting that every time i try to uninstall it (this is my 4th time doing this) and install the ati driver from the web.  I installed ATI diver but it didn't work and reinstalled the ubuntu one. Problem is that it won't do dual screens or detect the CRTs.  I get both CRTs to display but one shows my original desktop and the other shows a different desktop with different icons. I can interact with both desktops (that means it is not cloned) but it is not stretched desktop like how it is suppose to be. The ubuntu ati driver works but there is no ATI control panel for the graphic now. How do i fix this this big mess up?

If you were trying to install the Catalyst 10.9 driver from the ATI website you will probably have trouble as it was borked by an incompatible kernel security patch. They have release a hot fix which worked for me:

[http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx]("http://support.amd.com/us/kbarticles/Pages/GPU83ATICatalystLinuxHotfix.aspx")

BTW which ATI graphics card are you using?

---

### Post by I8NY on 2010-10-07
i have 4850 HD,

I tried the driver and uninstalled the ubuntu one. (same uninstall error) The driver got installed but upon reboot the Ubuntu wouldn't boot and i had to do recovery mode and uninstall it.  Could i burn ubuntu 10.04 CD and choose repair ubuntu and will that wipe the drivers and configs? I just want the driver to work either one will do. thank for the reply.

---

### Post by seventhsamurai on 2010-10-07
ATI drivers, especially for older cards are the work of the devil when it comes to Ubuntu. I have tried so many times to get the full functionality of my ATI card on my Acer Extensa 4420 laptop and just cannot. I read instructions in all the forums and have attempted so many different things. Always ends up with some crazy error. So now I have just made my peace and have just accepted whatever Ubuntu configures by default upon installation.

On my other computers that have Nvidia cards, now THERE's something that works, and works superbly at that!

---

### Post by alphacrucis2 on 2010-10-07
> **I8NY said:**
> i have 4850 HD,

I tried the driver and uninstalled the ubuntu one. (same uninstall error) The driver got installed but upon reboot the Ubuntu wouldn't boot and i had to do recovery mode and uninstall it.  Could i burn ubuntu 10.04 CD and choose repair ubuntu and will that wipe the drivers and configs? I just want the driver to work either one will do. thank for the reply.

You should still be able to get into recovery mode from the grub boot screen. Which method did you use to install the ATI driver? If you install the one from the AMD website, the general idea is:

1. uninstall fglrx. Very important.

```
sudo apt-get remove fglrx
```

If that doesn't work then run the ATI uninstall script as per ATI's instructions.

2. Run the downloaded ATI hotfix installer using the --buildpkg Ubuntu/lucid parameter as per the ATI instructions. This should create a number of deb packages. 

3. Install the deb packages via ```
sudo dpkg -i *.deb
``` 
(make sure there are no other deb files other than the ati ones in the folder you created them in.

4 [COLOR="Red"]sudo aticonfig --initial -f[/COLOR]

5. Reboot.

The card you have should work fine with current versions of fglrx. If you get totally stuck, then wait till Maverick Meercat (Ubuntu 10.10) comes out in a couple of days and install that. The fglrx in the Maverick repos is Cat 10.10 which you can't get directly off AMD yet. Just install it via the hardware menu.

---

### Post by I8NY on 2010-10-09
thank you so much for your help, it finally worked after i have failed 4 times before.  So i remove fglrx command (when i tried before i just removed it in the hardware drivers menu) and got a error ```
Errors were encountered while processing:
 fglrx
E: Sub-process /usr/bin/dpkg returned an error code (1)
```it has something to do with the ubuntu ati driver not uninstalling and it keeps coming every time i try to uninstall it.  So installed the ati hot fix driver and there were no deb files, i just ran the main .run file in the terminal. (doesn't work when clicked)  Then i did your comman[COLOR=Black]d "[/COLOR][COLOR=Black]sudo aticonfig --initial -f"  I have tried it before but i think that was after i rebooted and didn't have "-f" at the end.  So it works after opening amdcccle and configuring the displays.  It also fixed my other problem of lagging games with the desktop effects turned on.:)   Thanks so much, you saved me from a reinstall and maybe i should make a back up of my PC while it is still working.
[/COLOR]

---

