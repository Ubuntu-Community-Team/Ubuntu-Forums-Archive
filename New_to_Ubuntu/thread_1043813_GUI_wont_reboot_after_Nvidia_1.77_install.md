---
title: "GUI wont reboot after Nvidia 1.77 install"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Gerob on 2009-01-18
Hello Ubuntu people,

I installed Ubuntu 8.10 on my system.  Here is my specs.

[I]Intel(R)Core(TM)2 Quad CPU   Q6600 @2.4ghz
XFX Nforce 680i LT Mobo w/Pheonix AwardBIOS v6.00PG
2GB RAM DDR2 @800mhz
Maxtor 320GB w/Vista Ultimate on the other partition
NVIDIA GeForce 8600 GT 256mb (x2) {I use SLI sometimes and dual monitor when im not gaming}
LG W2052 20.5" @1680x1050 (resolution in Windows)
Broadcom 802.11n Wireless Network Adapter[/I]

I updated everything through the 'Update Manager', restarted, and then went up to 'Device Manager' and activated the Nvidia 1.77 drivers and restarted as I was instructed.  Instead of ending up at the GUI login screen I was dumped to a console with a TTY1 reference.  I tried to 'startx' but got an error message like this.

{{
Fatal Server error:
no screens found
giving up.

xinit: Connection refused (errno 111) unable to connect to x server.
xinit: no such process (errno 3): server error
}}

Could I please get some help getting back into the GUI and also to get my video card up and running again?

Thanks,
Gerob

---

### Post by new4me on 2009-01-18
I had that issue also with a new install. As soon as I took out the video card (bfg 9600) and used the onboard video, the issue went away. I'm still looking for a way around this issue. :(

---

### Post by 67GTA on 2009-01-18
Try booting into recovery mode. Then open a terminal and run ```
sudo nvidia-xconfig
``` and reboot.

---

### Post by Gerob on 2009-01-19
> **67GTA said:**
> Try booting into recovery mode. Then open a terminal and run ```
sudo nvidia-xconfig
``` and reboot.

I get the exact same error and it just overwrites my xorg.conf file with what looks like a generic setup.  Other people must have had this problem before?  Can anyone shed light on what I need to do?

Thanks
Gerob

---

### Post by Gerob on 2009-01-20
bump

---

### Post by Gerob on 2009-01-20
This may help as well.  I did a this code.

```
sudo dpkg-reconfigure -phigh xserver-xorg
sudo nvidia-xconfig
```

Then when I "startx"  I get this along with the error mentioned above.

(EE)Failed to load "type1" (module does not exist, 0)
(EE)No devices detected.

But when I go "lspci" it shows me my video card under

01:00:0 VGA Compatible Controller: nVidia Corporation GeForce 8600 GT (rev a1)

Could it be having trouble locating my video card and if so how do I point it to the video card in my xorg.conf file?

I will not quit till this is solved!! hehe

Thanks 
Gerob

---

### Post by Gerob on 2009-01-20
bump

---

### Post by 67GTA on 2009-01-20
You could boot the live cd, edit /etc/X11/xorg.conf, and change the driver from nvidia to vesa. That should get you booted into a desktop so we can try to find out what is happening.

---

### Post by Gerob on 2009-01-20
I'm quite capable of doing it through the command line with some guidance.  Wouldn't I also be able to just edit the xorg.conf file without the boot cd?

```
sudo nano /etc/X11/xorg.conf
```

right?  I think the issue is because I have 2 cards in my system for SLI it cant figure out which one to use.  What is the line I put in the xorg.conf file to point it to 01:00:0 on my PCI bus?

If it's not that my other thought was it is having trouble with my monitor?  If you really think getting into the desktop will help I can do that.  What is it we would do once in the desktop though?

Thanks
Gerob

---

### Post by Gerob on 2009-01-20
bump

---

### Post by u-foka on 2009-01-20
Hy!

I think you have to add ```
Driver "nv"
``` into the device section to disable the nvidia binary driver, and if you have X xithout acceleration, you can set your nvidia driver properly with nvidia-settings...

---

### Post by bailbath on 2009-01-20
> **Gerob said:**
> Hello Ubuntu people,

I installed Ubuntu 8.10 on my system.  Here is my specs.

[I]Intel(R)Core(TM)2 Quad CPU   Q6600 @2.4ghz
XFX Nforce 680i LT Mobo w/Pheonix AwardBIOS v6.00PG
2GB RAM DDR2 @800mhz
Maxtor 320GB w/Vista Ultimate on the other partition
NVIDIA GeForce 8600 GT 256mb (x2) {I use SLI sometimes and dual monitor when im not gaming}
LG W2052 20.5" @1680x1050 (resolution in Windows)
Broadcom 802.11n Wireless Network Adapter[/I]

I updated everything through the 'Update Manager', restarted, and then went up to 'Device Manager' and activated the Nvidia 1.77 drivers and restarted as I was instructed.  Instead of ending up at the GUI login screen I was dumped to a console with a TTY1 reference.  I tried to 'startx' but got an error message like this.

{{
Fatal Server error:
no screens found
giving up.

xinit: Connection refused (errno 111) unable to connect to x server.
xinit: no such process (errno 3): server error
}}

Could I please get some help getting back into the GUI and also to get my video card up and running again?

Thanks,
Gerob

I have pretty much the same setup as you and had the same problem. I believe it is the Nvidia driver not being compatible with the latest xorg. 
What I did to get a gui back-

```
sudo apt-get remove nvidia*
```
This will uninstall nvidia, when it finishes 

```
sudo init 6
```
This will restart your pc
 
Just copy and paste the above

Then boot into recovery mode and use xfix to get a new configuration.

Then use the resume boot option

You may need to reboot again

```
sudo init 6
```

Then let it boot normally then all should be ok.

I have dual boot of 8.04 and 8.10 Ubuntu on the same pc but I can't get the nvidia drivers to behave on the 8.10. I have full effects on the 8.04 and nvidia driver.

---

### Post by Gerob on 2009-01-20
I fixed it! ahahaha

It was a problem with it not finding my Video card or having direction on which one to use.  So after some research I added this code into the Device line.

```
Busid      "PCI:1:0:0"
```

Saved xorg.conf typed 'startx' and BAM right into the GUI with effects enabled!!  So for anyone trying to setup your video card and you get the same error where it says device not found.  Do 'lspci' find the line that mentions your video card and input the above code substituting the ':1:0:0' with your PCI busid.  Good luck all!!!

---

### Post by u-foka on 2009-01-20
hy!

I'm using the 177 driver happily with my gf 8400m gs and intrepid

so the problem surely not xorg vs nvidia incompatiblity!

---

### Post by bailbath on 2009-01-20
> **Gerob said:**
> I fixed it! ahahaha

It was a problem with it not finding my Video card or having direction on which one to use.  So after some research I added this code into the Device line.

```
Busid      "PCI:1:0:0"
```

Saved xorg.conf typed 'startx' and BAM right into the GUI with effects enabled!!  So for anyone trying to setup your video card and you get the same error where it says device not found.  Do 'lspci' find the line that mentions your video card and input the above code substituting the ':1:0:0' with your PCI busid.  Good luck all!!!

Spot on that solved my problem too!
Thank you

---

### Post by 67GTA on 2009-01-20
.

---

