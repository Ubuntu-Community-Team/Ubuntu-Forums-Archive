---
title: "Must reinstall wireless driver after reboot"
date: 2008-05-06
forum: Networking &amp; Wireless
---

### Post by it_broke_again on 2008-05-06
Hi, everyone!

I'm having an odd issue with my wireless driver. After I start my computer, 99% of the time, I must reinstall my wireless driver in order to get it to work. I was wondering if anyone else had this problem and if there is a fix for it. Here is some more information: (the terminal output is for the relevant hardware/drivers only-- if more information is needed, please just let me know)

Ubuntu 8.04 x64
Toshiba Satellite A215-S4817

lspci
```

14:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

```

ndiswrapper -l
```

net5211 : driver installed
	device (168C:001C) present (alternate driver: ath_pci)

```
*Note: I had a previous problem with the driver not being x64, but now I am using the x64 driver listed above and the wireless card will work, I just need to keep reinstalling the driver.

If anyone has any suggestions, they would be much appreciated. Please let me know if you need more information.

Thanks!

~ Lisa

---

### Post by Aearenda on 2008-05-07
When using NDISwrapper, you have to add 'ndiswrapper' to the end of /etc/modules to make it load every boot - and you should run ```
sudo ndiswrapper -m
``` as well, so that it adds the appropriate aliases in /etc/modprobe.d.

---

### Post by it_broke_again on 2008-05-10
Thanks for your suggestion. I tried "sudo ndiswrapper -m" and it gave me lines and lines of this:

```
module configuration already contains alias directive

```

I also tried adding "ndiswrapper" to /etc/modules, but it still didn't work on startup. 

What happens is that it will detect a signal, try to connect to the internet but it will never work-- I have to reinstall the driver for it to connect to the wireless signal. Is there anything else I could try?

Thanks,
~Lisa

---

### Post by lswest on 2008-05-10
i assume you're running on 8.04?
idea #1: make a script like this: right-click anywhere, desktop will probably be your first choice, choose "new file" and "empty document" then enter this into the file: ```
#!/bin/bash
sudo modprobe -r ath_pci
sudo modprobe -r ndiswrapper
sudo modprobe ndiswrapper
``` when saving, make sure that it ends in ".sh" and make it executable (by going to properties and under "permissions" check the "allow executing as a binary file" option.  Then run it to see if it gets your wireless working.  If it does do this:```
sudo cp /path/to/script /etc/init.d/wireless.sh #you can call it anything, i called it wireless.sh for simplicity's sake
sudo chmod 755 /etc/init.d/wireless.sh
sudo update-rc.d wireless.sh defaults #this will make it run at boot
```  Hope it helps (don't have an atheros card, so i can't test it)

idea #2: otherwise you can set a script to install the drivers, such as ```
#!/bin/bash
sudo ndiswrapper -i /path/to/driver/
sudo modprobe ndiswrapper
``` and save it in a script, then make it run at boot like i listed above.

idea #3: Also, check to see if you blacklisted the ath_pci driver by doing ```
sudo gedit /etc/modprobe.d/blacklist
``` and seeing if there is a line that read "blacklist ath_pci" if it doesn't exist, add it.

good luck,
Lswest

**Note** the ideas are numbered according to when i thought of them, not in what order you should try them.

---

### Post by Aearenda on 2008-05-10
It seems to me that if the blacklist entry is right, the rest of lswest's steps are unnecessary. However, I have seen a problem with some wireless cards such that they only start up on the second attempt - so 
```
ifdown wlan0
ifup wlan0
```
added to /etc/rc.local will make it work.

---

### Post by lswest on 2008-05-10
> **Aearenda said:**
> It seems to me that if the blacklist entry is right, the rest of lswest's steps are unnecessary. However, I have seen a problem with some wireless cards such that they only start up on the second attempt - so 
```
ifdown wlan0
ifup wlan0
```
added to /etc/rc.local will make it work.

um, the "other steps" are all seperate ideas, wait, i'll number them.  Sorry for any confusion.

*edit* numbered and noted.

Also, i think the issue is with conflicting drivers (the ath_pci and the ndiswrapper drivers), not so much a startup error.

---

### Post by Aearenda on 2008-05-10
Sorry lswest, I did understand that, it's MY language that's wrong! I should have said 'suggestions' or 'ideas'. 

You may well be right about the driver conflict.

---

### Post by it_broke_again on 2008-05-20
Lswest, I did try creating the two scripts that you had suggested and they were a big help. Though I didn't get a chance to formally set them up, they helped me to avoid reinstalling the driver after every startup-- which is tiresome. 

Though I was interested in trying out all the suggestions that you and Aearenda made, I cannot because I am no longer near a wireless network (back from college). I thank you both for your help and I will keep this thread bookmarked to give any further comments or thank yous when I return to college (and the wireless network there).

:)

---

### Post by lswest on 2008-05-22
I hope it works for you, and any feedback would be greatly appreciated.

---

