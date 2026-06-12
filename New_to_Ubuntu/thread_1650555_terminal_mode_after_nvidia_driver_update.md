---
title: "terminal mode after nvidia driver update"
date: 2010-12-21
forum: New to Ubuntu
---

### Post by uveryames on 2010-12-21
i just installed ubuntu 10.10 .386.  a pop up came up and said to install an nvidia driver for my card. so i installed and rebooted.  

now ubuntu starts in the terminal.  i log in and try to 'startx' with an error of 'no devices'

how do i configure ubuntu to run gdm at startup again :(  

ty in advance!

---

### Post by alzie on 2010-12-21
Did you install Nvidia from the repositories or from the Nvidia site?

If from the Nvidia site, do you recall where you left the file (ie desktop)?

---

### Post by uveryames on 2010-12-21
on the top dock bar next to the wifi symbol..there was a 'driver update' icon that popped up next to it.  it had the option to 'activate'. i activated the nvidia driver and it started downloading/installing.  then it said it was complete.  so then i rebooted and im stuck in the terminal blegh :(  

so im not sure where the download came from...but i did not physically go to the nvidia site and download a driver.  hopefully that answers the question.  

ty!

---

### Post by uveryames on 2010-12-21
ive tried:

sudo service gdm stop, start
sudo /etc/init.d/gdm restart
sudo dpkg -reconfigure xserver-xorg
sudo dpkg -reconfigure -phigh xserver-xorg

all fail. im still stuck in terminal.  

i also tried removing 'quiet splash' in the grub menu and replacing it with nomodeset then ctrl x to restart.  that failed as well.  

im lost.  i ran lspci | grep vga:  

00:02:0 VGA compatible controller: intel corp mobile 4 series chipset integrated graphics controller rev 07

01:00:0 VGA compatible controller: nvidia corp G96 [geforce GT 130M] (rev a1)

thanks for any more help

---

### Post by alzie on 2010-12-21
Are you wired or wireless to the internet?  The following code is to install nvidia drivers from the repositories but if you cannot connect to the internet then they can't download to install. Enter your password when prompted to do so. 

```
sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

sudo apt-get update && sudo apt-get install nvidia-current nvidia-current-modaliases nvidia-settings

restart
```




source: [http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html](http://www.webupd8.org/2010/06/how-to-install-nvidia-25635-display.html)

---

### Post by daneforce on 2010-12-21
Do you happen to have a laptop with switchable graphics? If so, try disabling the switchable option in BIOS, then get rid of the Nvidia driver.

---

### Post by uveryames on 2010-12-22
> **daneforce said:**
> Do you happen to have a laptop with switchable graphics? If so, try disabling the switchable option in BIOS, then get rid of the Nvidia driver.

this solved the problem.  i have a laptop with "hybrid graphics mode" which saves power and puts the video card at a sleep state when enabled.  i disabled this in BIOS, and set the display driver to nvidia.  solved.  

thank you all very much.

---

