---
title: "Broadcom 4312 driver installation stalled on HP Mini 2133."
date: 2018-10-10
forum: Networking &amp; Wireless
---

### Post by egarcia1970 on 2018-10-10
Hello to all.

I installed Lubuntu 16.04 on an old HP Mini 2133 and can't get the proprietary Broadcom 4312 wireless driver to install. The update utility recognizes the driver and allows me to select it for installation and apply the changes but the process stalls at approximately 20%:

[ATTACH=CONFIG]281294[/ATTACH][ATTACH=CONFIG]281295[/ATTACH]


My wired internet connections works fine so that's not an issue.

¿Is there another way to install the driver without using this application? ¿Maybe using apt-get from the terminal?

Thanks in advance.
Ernesto.

---

### Post by wildmanne39 on 2018-10-10
I do not believe that is the correct driver or I should say not the best one, please do:
```

sudo apt update
sudo apt dist-upgrade
sudo apt install firmware-b43-installer
```
Reboot

If it does not work then click on the wireless script in my signature and post the results here.

---

### Post by egarcia1970 on 2018-10-11
Hi there.

Thanks for your response.

The system updated successfully but the device is still not working.

Results of script run attached.

Regards,
Ernesto.

[ATTACH]281318[/ATTACH]

---

### Post by wildmanne39 on 2018-10-11
I see two networks in the connections available section with the same name but no networks show up in network manager config, please go to your network icon and remove all networks then reboot your computer and let network manger find your network then enter your password, if it does not connect please run and post a new script file so we can see if any changes took place.

Thanks

---

### Post by egarcia1970 on 2018-10-12
Hi there.

That did the trick.

Thank you very much for your support.

Regards,
Ernesto.

---

### Post by wildmanne39 on 2018-10-12
Your welcome! please use threads tools at the top of the page to mark the thread solved.

Enjoy!

---

