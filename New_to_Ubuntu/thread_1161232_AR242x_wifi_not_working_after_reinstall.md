---
title: "AR242x wifi not working after reinstall"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by ____ on 2009-05-16
In my first install i had to install a backport to get the wifi working but i accidentally deleted my partition and had to reinstall. Now i can't get it to work again.

Atheros AR242x wlan

---

### Post by LesterPalooza on 2009-05-16
I'm assuming you reinstalled Ubuntu and tried to install your atheros wifi but was unsuccesful. Which guide are you using?

---

### Post by anewguy on 2009-05-16
Don't know if it applies to 9.04, but you may want to check this post:

[http://ubuntuforums.org/showthread.php?t=967654]("http://ubuntuforums.org/showthread.php?t=967654")


Dave :)

---

### Post by LesterPalooza on 2009-05-16
In Ubuntu it really does try to detect your Atheros chip. In Ubuntu 7.10 the wireless on my laptop was detected as the AR5006EG and I use ndiswrapper and the net5416.inf driver. On Ubuntu 8.04 my wireless was detected as the AR242x and I was able to download ndisgtk (in the repos) and use the net5211.net driver, (the ndisgtk is just a graphical interface for ndiswrapper, very easy and very nice!). This time (Ubuntu 8.10) it wasn’t detected as the AR5006EG, it was however detected as the AR242x BUT I couldn’t use ndisgtk as before. I’m thinking it’s because they updated the network manager in 8.10. Either way here is how I got it working.

Remember TAB is your friend in the terminal!

To check what you wireless is detected as just run the following in the Terminal:

lspci | grep Wireless

These steps are done using Ethernet, if it is unavailable, just go to any computer with Internet and download the mad wifi snapshot shown in these steps. Just follow the step from there once you have gotten the file.

1) First disable Ubuntu’s Atheros HAL driver if loaded:

Click ‘System’ –> ‘Administration’–> ‘Hardware drivers’ then deactivate support for the Atheros 802.11 wireless driver

I rebooted just to make sure there was no chance it was running.

Everything else is done in the Terminal :)

2) Get the Ubuntu built essentials package, this will allow the program to compile:

sudo apt-get install build-essential

**if this is a new install of 8.10 you MUST do “sudo apt-get update” (without quotes) to update your repositories

3) Download the madwifi snapshot:

wget [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6-current.tar.gz)

4) Untar (unzip) the newly downloaded file:

tar xvf madwifi-hal-0.10.5.6-current.tar.gz

5) Go into the newly created directory:

cd madwifi-hal-0.10.5.6-r3879-20081204

6) Then compile the package:

make

7) The install the package:

sudo make install

8) Then load the newly created module:

sudo modprobe ath_pci

if yours is like mine you may not get a wifi light, in that case you won’t know if the card is on, just try pushing the button to toggle it (on the Acer 4720Z it’s a picture of a satillite)

9)  If your wireless is working after this when you reboot the computer it won’t to fix it, you must add it to the kernel boot modules list:

In the terminal type “sudo gedit /etc/modules”(without quotes) and add “ath_pci”(again without quotes) to the bottom of the list if you don’t have anything in the list just add it to the bottom. Click ‘Save’ and that’s it. ::PER Joe Purdy “DO A REBOOT”::

FYI: If there is ONLY one reason you want to update to Ubuntu 8.10, it’s for the boot-up time. It’s supa-speedy.

---

### Post by ugm6hr on 2009-05-16
Try 9.04, it has the ath5k driver out of the box.

---

### Post by binbash on 2009-05-16
In jaunty it works out of the box.On intrepid follow one of this : [http://www.ubuntu-inside.me/search/label/ar242x](http://www.ubuntu-inside.me/search/label/ar242x)

---

### Post by ____ on 2009-05-17
In Hardware Drivers the wifi driver is called Alternate Atheros "madwifi" driver but still doesn't work I think I installed it using the command ```
sudo apt-get install linux-backports-modules-jaunty
``` Is there any way I can remove it and try the default driver?

---

### Post by nothingspecial on 2009-05-17
Wireless worked in Jaunty for me since day one ........... until yesterday.

After much messing about with config files and such, a relatively simple fix worked.

That`s usually the way - not always.

All I did was add ath5k to /etc/modules

To do this type ```
sudo nano /etc/modules
```

Press the down arrow till you get to the bottom - there might be lines with fuse and lp in them - don`t touch.

Then type ```
ath5k
```

Press Ctrl O (capital o not zero) then Enter. (That saves it)

Then Ctrl X (That closes nano)

Reboot.

---

### Post by ____ on 2009-05-17
> **nothingspecial said:**
> Wireless worked in Jaunty for me since day one ........... until yesterday.

After much messing about with config files and such, a relatively simple fix worked.

That`s usually the way - not always.

All I did was add ath5k to /etc/modules

To do this type ```
sudo nano /etc/modules
```

Press the down arrow till you get to the bottom - there might be lines with fuse and lp in them - don`t touch.

Then type ```
ath5k
```

Press Ctrl O (capital o not zero) then Enter. (That saves it)

Then Ctrl X (That closes nano)

Reboot.

Just tried that, did not work. I think I just need to uninstall the alternate driver and retry the default ath5k driver that comes with 9.04 but I don't know how.

---

