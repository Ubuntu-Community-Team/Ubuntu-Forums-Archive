---
title: "graphic card problem"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by cybuss on 2009-01-27
recently installed a nvidia geforce 7 series graphic card
a lot of things don't work like they did without it
cant change resolution cant change visual effects every time i turn the computer on i have to pick the driver and junk
and it don't change anything computer still running in low graphics

and can i get code for terminal to check my bit version

---

### Post by overdrank on 2009-01-27
> **cybuss said:**
> recently installed a nvidia geforce 7 series graphic card
a lot of things don't work like they did without it
cant change resolution cant change visual effects every time i turn the computer on i have to pick the driver and junk
and it don't change anything computer still running in low graphics

and can i get code for terminal to check my bit version

You can use the command ```
uname -a
```. What graphics card was installed before the nvidia graphics?
Did you remove the drivers before you installed the new card?
I assume you are using intrepid 8.10?
Have you tried the xfix option when booting into recovery mode?

---

### Post by cybuss on 2009-01-27
there was no graphics card before this so no drivers
how do i check if im using intrepid?
i never booted into recovery mode don't even know how to boot in recovery mode

---

### Post by overdrank on 2009-01-27
> **cybuss said:**
> there was no graphics card before this so no drivers
how do i check if im using intrepid?
i never booted into recovery mode don't even know how to boot in recovery mode

Ok, you may use the command ```
lsb_release -a
``` to view the release or under system, about Ubuntu.
You may need to install the drivers for nvidia located under system, administration, Hardware.
Recovery mode is usually the second choice from the grub while booting. Then you will be given four options and one is the xfix that will help with graphics issues.

---

### Post by cybuss on 2009-01-27
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy
thats what it gives me when i type the code in

and i have a driver ubuntu installed for me
[http://ubuntuforums.org/picture.php?albumid=874&pictureid=2963](http://ubuntuforums.org/picture.php?albumid=874&pictureid=2963)

---

### Post by overdrank on 2009-01-27
> **cybuss said:**
> No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 8.04.2
Release:	8.04
Codename:	hardy
thats what it gives me when i type the code in

Ok great, you will need to install nvidia-settings, you may either use synaptic manager or add and remove.
Also you may try the command ```
gksu displayconfig-gtk
``` and adjust the resolution there. If that does not work.

---

### Post by cybuss on 2009-01-27
[http://ubuntuforums.org/picture.php?albumid=874&pictureid=2963]("http://ubuntuforums.org/picture.php?albumid=874&pictureid=2963")

thats my driver its dont work and ubuntu auto installed

---

### Post by cybuss on 2009-01-27
when i typed that code in it told me that one of the graphic cards power cables were not hooked up and i open side and looked and yep there it was
my friend put the card in for me i guess i should do those things my self
i can change resolution etc but i want to change my resolution even more like i can on my other computer that has same monitor size any ideas?

---

### Post by overdrank on 2009-01-27
> **cybuss said:**
> when i typed that code in it told me that one of the graphic cards power cables were not hooked up and i open side and looked and yep there it was
my friend put the card in for me i guess i should do those things my self
i can change resolution etc but i want to change my resolution even more like i can on my other computer that has same monitor size any ideas?

Have you tried to change with the nvidia-settings  ```
gksu nvidia-settings
```

---

### Post by cybuss on 2009-01-27
the code you gave me just attempts to load administration options thing then it disappears without loading

---

### Post by overdrank on 2009-01-27
> **cybuss said:**
> the code you gave me just attempts to load administration options thing then it disappears without loading

Ok have you installed nvidia settings as I suggested earlier post. :)
And just to make sure which command?

---

