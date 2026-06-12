---
title: "Lost wireless driver on restart"
date: 2011-02-02
forum: New to Ubuntu
---

### Post by Nahjil567 on 2011-02-02
Ok I have a broadcom bcm4318 chipset wireless card. I have gotten it online, but everytime I reboot I have to 
```
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.0.o
sudo b43-fwcutter --unsupported -w lib/firmware broadcom-wl-4.150.10.5/wl_apsta_mimp.o
sudo modprobe -r b43 ssb
sudo modprobe b43
```to get reconnected to the router and the internet, now I am unsure if the first two steps are necessary, though it works. What can I do to make the changes permanent and not have to worry about doing this everytime I restart.

---

### Post by Nahjil567 on 2011-02-02
I am running Ubuntu 10.04 which I forgot to mention. Sorry.

---

### Post by TeoBigusGeekus on 2011-02-02
_Solution No1:_
Create a script in gedit or geany
```
#!/bin/bash
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.0.o
sudo b43-fwcutter --unsupported -w lib/firmware broadcom-wl-4.150.10.5/wl_apsta_mimp.o
sudo modprobe -r b43 ssb
sudo modprobe b43
```
save it, let's say as wireless, move it to your /etc/init.d directory
```
sudo mv wireless /etc/init.d
```
and make it executable
```
sudo chmod +x /etc/init.d/wireless
```
Finally, run
```
sudo update-rc.d wireless defaults
```
and your script should run upon every boot up.

_Solution No2:_
My recent adventure with a broadcom wireless chipset made me believe that the most stable and less error prone solution is [ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper").

---

### Post by Nahjil567 on 2011-02-02
I have tried using ndiswrapper a few times and have not been able to get it to work with my machine, whether or not it is user error or what I do not know. Thank you for the work around, but I wonder if there is another way, as I have had it working before on a previous installation of the same Ubuntu build, but I have not been able to figure it out this time around.

---

