---
title: "Help with XORG and hardware drivers"
date: 2009-03-19
forum: New to Ubuntu
---

### Post by Pixtu on 2009-03-19
I have installed Intrepid on a Sony VAIO FS315S but am having problems with the nVidia display driver.

I have tried several things but I appear to be going backwards!

Previously I was able to use the standard graphics which still provided a 1280 x 800 display.

Now every time I restart I get a message that the Screen/Graphics/Input method cannot be detected and the system is running in low graphics mode. When I click the OK button I am taken to a dialog box with 3 options: run in low graphics, reconfigure or troubleshoot.

The troubleshoot lets me look at the XORG log and conf files. The log file would appear to suggest that the driver couldn't be found.

If I try and re-configure I get the option to use the previous config or to create a new one. Which ever I choose, if I then click OK it appears to come back to the same place. I can only 'get through' if I click cancel. The system then starts in low graphics.

Once started, I sometimes get a PCI card icon in the top display with a message that says that I am using proprietary drivers that are unsupported. This might happen after I System->Preferences->nVidia X Server settings.

If I click on this icon, or if I choose System->Administration->Hardware Drivers, it suggests that I am not using the nVidia driver but that I need it to obtain best graphics performance.

If I then select one of the displayed drivers (173 or 177)*, and select activate I get a dialog box that suggests that it downloads and installs the driver, and then that I need to restart the system.

When I do this I come back round to the previous low graphics error at start up.

*I have tried using apt-get to obtain the latest drivers and also via the nVidia website. One or other of these routes seems to have added another driver (96) to the list displayed when I select the Hardware Drivers as above.

Any ideas please?

---

### Post by Bachstelze on 2009-03-19
To know exactly what is going on, we need to see your Xorg config file and message log. Please paste the contents of these files:

/etc/X11/xorg.conf
/var/log/Xorg.0.log

---

### Post by Pixtu on 2009-03-19
Sorry, I thought I had attached them.

The attached file was produced through the troubleshooting option when the system booted into low graphics mode.

I have been able to overcome the need to restart in low graphics mode by running xfix from the 'recovery' option in grub.

I now have the 1280 x 800 'standard' resolution but still not able to use the nVidia driver or its extra functionality.

---

