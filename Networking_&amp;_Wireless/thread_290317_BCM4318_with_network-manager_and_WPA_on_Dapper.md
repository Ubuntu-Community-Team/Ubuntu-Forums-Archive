---
title: "BCM4318 with network-manager and WPA on Dapper"
date: 2006-11-01
forum: Networking &amp; Wireless
---

### Post by finite9 on 2006-11-01
This guide is very quick to implement and is an elegant solution as upgrades should not break this (assuming that the new upstart still calls /etc/network/ scripts) and there is minimal scripting involved.  Some things to bear in mind: I have not tested with an Edgy upgrade and it only works at 11Mbit at the moment, but this should improve as the driver in the kernel is improved upon.

This method uses the opn source BCM43xx driver, not ndiswrapper, and is the preferred method for free software enthusiasts.  Almost all other guides on the forums concentrate on ndiswrapper as it is perceived as more stable and/or less buggy, but I have not had any instability issues with this driver, and as long as you do not need to copy large files over a LAN regularly, the 11Mbit limit should not be an issue for people with lone laptops connecting to a broadband service at <8Mbit.

In the past, there have been problems getting the open source driver to work with WPA and network-manager, but development continues at a very nice pace, and I believe that most 'issues' will disappear with Edgy Eft and Feisty Fawn releases, as many issues have already been solved between 2.6.15-23 and 2.6.15-27.

This was tested on an Acer Aspire 5021WLMi and an Acer Aspire 3023 by another Ubuntu user.
[B]
Drawbacks:

11Mbit only *at the moment*
Laptop suspend not functioning with network-manager in 6.06, but OK in 7.04
Automatic switching from wired->wireless not working for Acer users (workaround exists) in 6.06[/B]

[B]Pre-requisites:

clean install of Ubuntu 6.06.1 or 7.04 i386 or amd64.
A working wired ethernet connection.
Broadcom AirForce54g 4318 (rev 02) adapter.
[There is no reason why this should not work with rev 01 or 4306 adapters]
The universe repository must be enabled.[/B]

Open a Terminal and paste in the following commands&#8230;

*[COLOR="Red"]UPDATE 2006-11-03[/COLOR]: A few days ago cafuego released a newer version of bcm43xx-firmware that shows up in update-manager.  When trying to install this update, it fails as the size is incorrect.  I do not know if this is an issue with new installs and I will email the maintainer asking for clarification.*

*[COLOR="Red"]UPDATE 2006-11-23[/COLOR]: I mailed Cafuego and he has fixed the problem with the DEB file in his repository!*

```
echo 'deb http://ubuntu.cafuego.net dapper-cafuego bcm43xx' | sudo tee -a /etc/apt/sources.list
wget http://ubuntu.cafuego.net/969F3F57.gpg -O- | sudo apt-key add -
sudo apt-get update
sudo apt-get install bcm43xx-fwcutter bcm43xx-firmware
echo 'blacklist ndiswrapper' | sudo tee -a /etc/modprobe.d/blacklist
echo 'ENABLED=0' | sudo tee -a /etc/default/wpasupplicant
sudo mv /etc/network/interfaces /etc/network/interfaces~
echo 'auto lo' | sudo tee -a /etc/network/interfaces
echo 'iface lo inet loopback' | sudo tee -a /etc/network/interfaces
```
 

## ******************** ONLY FOR ACER USERS *******************************
## *** Other laptops may also require SW to 'turn on' wireless ************

NOTE.  If running 7.04 then you need to get Acer_acpi-0.4 instead, as 0.3 will not compile on kernel 2.6.18 and above by default.

#install acer_acpi to turn on wireless adapter through software
#this is the only package that will be manually installed
#as it will be compiled, it works on 32-bit and 64-bit systems whereas acerhk #only works on 32-bit systems AFAIK
#when upgrading kernel, make sure to re-compile and re-install acer_acpi in the new kernel, after having installed the linux-headers-`uname -r` package for the new kernel.

```
wget http://www.archernar.co.uk/acer_acpi/acer_acpi-0.3.tar.gz
tar -xvf acer_acpi-0.3.tar.gz
cd acer_acpi-0.3
sudo apt-get install build-essential linux-kernel-headers linux-headers-$arch linux-headers-`uname -r`
make
sudo make install
echo 'acer_acpi' | sudo tee -a /etc/modules
echo 'pre-up /etc/network/StartAcerWireless' | sudo tee -a /etc/network/interfaces
sudo touch /etc/network/StartAcerWireless
echo 'chmod 777 /proc/acpi/acer/wireless' | sudo tee -a /etc/network/StartAcerWireless
echo 'echo "enabled: 1" > /proc/acpi/acer/wireless' | sudo tee -a /etc/network/StartAcerWireless
echo 'iwconfig eth1 ap any' | sudo tee -a /etc/network/StartAcerWireless
sudo chmod 754 /etc/network/StartAcerWireless
```

## ************************************************************************

From the Gnome menu bar, go to System|Preferences|Sessions|Startup Programs, click the Add button and write in the following and click OK:

```
nm-applet &#8211;sm-disable
```


reboot PC


When rebooted, left-click on nm-applet and choose to "connect to other wireless network" even if your AP is visible (this only applies the first time you connect as nm-applet will not prompt for a password if using WPA.  Once the password is stored on the keyring you can simply click on the WLAN that appears in the list).  Write in the SSID, choose WEP or WPA and enter the password.  Upon connecting nm-applet will ask for a master password for the wallet.  Choose something simple.

DONE!



**A note about switching between wireless and wired:**

On Acer laptops at least, when you plug in the wired ethernet, network-manager automatically switches over, but after unplugging, it will not re-conect to the wireless lan.  I do not know if this is a nm-applet issue/bcm43xx issue or acer_acpi issue but the code below can be pasted into a terminal to get it all working again.  Note that before running the code below, you need to right-click network-manager, disable wireless, run the script, then re-enable wireless in nm-applet, and if that fails to reconnect (very unusual) then left-click the nm-applet icon and select your AP from the list to re-connect:

```
sudo modprobe -r acer_acpi
sudo modprobe -r bcm43xx
sudo modprobe bcm43xx
sudo modprobe acer_acpi
sudo chmod 777 /proc/acpi/acer/wireless
sudo echo "enabled: 1" > /proc/acpi/acer/wireless
```

---

### Post by smarted on 2007-02-15
Awesome job! We got the bcm 4318 working on my laptop. No more carrying external wireless card ever again!
Thanks a lot!:popcorn: :popcorn: :popcorn:

---

### Post by bomanizer on 2007-02-26
This is odd... i followed this through and ended up with a freeze during GDM login. I can type my login & password, but during the login (loading nautilus, etc.. I guess???) GDM freezes. I remember seeing posts about beryl & nm-applet conflicts but I've been unsuccessful in finding them. Also, the card and wireless are both unreachable at my desktop... will resume with the tinkering.. :)

Any hints?

Thanks!

---

### Post by vangelm on 2007-09-28
Hello, I am using Ubuntu 7.10, but I tried it in also in 7.04 and I still have same problem:
When I type:

sudo echo "enabled: 1" > /proc/acpi/acer/wireless 

reply from terminal is:

echo: write error: Invalid argument

What do I do? Please help me! :(

---

### Post by johnnycordeiro on 2007-09-30
hi use "1" instead of "enabled: 1" The program seems to only use a 1 or 0
hope this helps

---

