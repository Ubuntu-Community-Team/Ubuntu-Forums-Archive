---
title: "Wireless Problems"
date: 2007-06-22
forum: Networking &amp; Wireless
---

### Post by vaelz on 2007-06-22
I'm fairly new to linux so you're going to have to hold my hand through most of this, which I apologize for in advance.

I have a Dell Inspirion E1505 Laptop, with the Dell Wireless 1500 WLAN card. I've looked it up on ndiswrapper website, and it does have supported drivers with the program. I believe i have installed ndiswrapper properly, and I also installed ndisgtk to give myself a gui to use.

Previously i tried to follow a documentation on how to install the drivers from terminal with the 1350 Card, and i accidentally installed those drivers, which may be the souce of my problem since they use the same named .inf file. So first i have to ask how to uninstall those drivers. The problem is on the ndisgtk, they dont come up as installed Windows Drivers, nothing does, however when i try to install the 1500 Drivers, an error that says "Driver.inf" is already installed".

But also when i type the command lspci on terminal, my wireless card is listed as 
"0b:00.0 Network controller: Broadcom Corporation Unknown device 4328 (rev 01)"

---

### Post by cyberdork33 on 2007-06-22
Did you read the man page?

```
 man ndiswrapper 
```

Hint:
```
 ndiwrapper -e *your_driver_name*
```

---

### Post by vaelz on 2007-06-24
It appears that the driver is not even installed, but when i prefromed a "ndiswrapper -l" to see the list of installed drivers, the only thing i get is "bcmw5 is an invalid driver" Any ideas whats going on here ?

---

### Post by a1unix529 on 2007-06-24
If you navigate to /etc/ndiswrapper/ you should see folders; these are where ndiswrapper stores its drivers.

In a new terminal window, copy and paste, or type:
```
sudo ndiswrapper -r [COLOR=Red]<case-sensitive name of driver>[/COLOR]
```to get rid of them.

* Replace [COLOR=Red]<case-sensitive name of driver>[/COLOR] with the **case-sensitive name of a folder** in the /etc/ndiswrapper/ directory, so that it looks like: "[COLOR=SeaGreen]sudo ndiswrapper -r wlanuig[/COLOR]" without the quotes.

---

### Post by MeeMaw on 2007-06-24
and this post may help....
[http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx](http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm43xx)

or this one.....
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

I'm sure you'll get it going!

---

### Post by cyberdork33 on 2007-06-25
> **vaelz said:**
> It appears that the driver is not even installed, but when i prefromed a "ndiswrapper -l" to see the list of installed drivers, the only thing i get is "bcmw5 is an invalid driver" Any ideas whats going on here ?

If it is listed, it is "installed" (maybe not working, but installed)

to remove it:
```
ndiswrapper -e bcmwl5
```

---

### Post by kevdog on 2007-06-25
Just cd to the /etc/ndiswrapper directory and perform the following command:
sudo rm -R *

This should remove and and all drivers and sub-directory associated with ndiswrapper driver files.

Make sure the /etc/ndiswrapper directory is empty.
Running ndiswrapper -l should list either nothing or tell you nothing is installed.

---

