---
title: "Having issues due to my special hardware."
date: 2011-02-20
forum: New to Ubuntu
---

### Post by DDRaptor on 2011-02-20
Good Day All first post, starting a possible long term stay with ubuntu cause my 32SSD died I switched back to a 8GB and ubuntu is the only thing small enough to work well.

Hardware overview
MSI U115
8GB SSD + 160GBHDD
Atom 1.6Ghz + GMA 500 Poublso US15W Working.
N-Wi-fi and Bluetooth both working
Sound working flawlessly

had to install only the GMA 500 Drivers ubuntu is great out of the box. 

I have a few issues with hardware the first one absouluty annoying.

I have no right click whatsoever, I have tried using imwheel, and the mouse properties but nothing works it's as if the os is not recieveing the signal. I have everything else left click and vertical and horizontal scrolling. The context button works from the keyboard. Maybe theres an application to map a mouse button to a key?

I have no brightness function keys - not too important Fn+F4(down) Fn+F5
I can't turn on my Webcam through the function key Fn+F6
I can't use my hybrid feature Unique to this netbook Fn+F10
the hard drive gets turned off and runs only the SSD gives me around 15-20hrs of use with the 9-cell battery.

any help would be so appreciated It would be nice to right click again. 

Thanks.

---

### Post by DDRaptor on 2011-02-21
Have had some success the webcam was working the whole time just needed to apps to verify. Used video for linux control panel, and camorama video app and webcam is A OK.

I ran the update and got Compiz Setting manager and set the brightness control but I have not restarted yet. 

I might of figured out the problem with my right click I believe the button it not working itself I change the left/right handed option and my left button showed the standard right click but the right still did not select. 

So I am about to open up the netbook and make sure that the touchpad wires are connected correctly, I took the system completely apart trying to figure out what was wrong with my SSD.

---

### Post by DDRaptor on 2011-02-21
Got the right-mouse click, the small ribbon cable to the touchpad was not completely connected. Got that fixed.

Restarted and the brightness hot-keys are still not working.

During the large 280MB update process I got a lot of repeat packages and libraries now, How do I remove the old ones safely??

Thanks.

Followed a walk through for poulsbo drivers had all the up to date drivers but my code is kinda long.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX="acpi_osi=Linux acpi_backlight=vendor acpi_skip_timer nomodeset video=uvesafb:mode_option=1024x600-24,mtrr=3,scroll=ywrap pci=nocrs mem=1920mb"

I followed the following guide [http://ubuntuforums.org/showthread.php?t=1229345&highlight=Brightness+control]("http://ubuntuforums.org/showthread.php?t=1229345&highlight=Brightness+control")

NO luck with brightness control.

---

### Post by DDRaptor on 2011-02-22
Any Ideas??? bump.

---

### Post by Ben Page on 2011-02-22
> **DDRaptor said:**
> 

During the large 280MB update process I got a lot of repeat packages and libraries now, How do I remove the old ones safely??



Install Ubuntu Tweak, you can clean all packages safely from there.

---

### Post by DDRaptor on 2011-02-22
I got it Thanks got all that cleaned up.

---

### Post by DDRaptor on 2011-02-26
I have been pretty successful with the Ubuntu so far I have gotten to play 3D games and Music creation software that would croak the netbook on windows. But I still have no brightness control. If I could fix that then I could work on disabling the hard drive. 

Any other ideas? I have read alot of threads on the GMA 500

---

