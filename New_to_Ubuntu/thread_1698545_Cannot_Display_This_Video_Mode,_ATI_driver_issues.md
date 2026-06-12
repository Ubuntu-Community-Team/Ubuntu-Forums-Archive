---
title: "Cannot Display This Video Mode, ATI driver issues"
date: 2011-03-02
forum: New to Ubuntu
---

### Post by Hoplon on 2011-03-02
To start off I've searched for a solution to this problem for days. I just installed ubuntu 10.10 using Wubi. The install goes great, but then I try to install my ATI radeon 3100 driver. 

After installing the driver which i've tried both this [guide]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI"), and enabling the driver through ubuntu. Both of which I tried on fresh installs, however, when I reboot after install I get to the purple ubuntu screen (The 4 or 5 loading dots look like squares now) and my monitor flickers right before boot, screen goes black and displays "Cannot Display This Video Mode."

Now I can reboot in recovery mode using failsafeX graphics. I've tried many different ways of installing the driver on many fresh installs of ubuntu. 

I'm very new to ubuntu and linux and id like to start learning the computer world outside of microsoft... Please help.

I'm going to continue to work this problem out myself I'll report back if I fix it.

---

### Post by turtle153 on 2011-03-02
If you can get an Ubuntu terminal up (try recovery mode), install the ATI drivers. I don't use them for my graphics but it's worth a try.
```
sudo apt-get install fglrx
``` should do the trick

---

### Post by Hoplon on 2011-03-02
Tried it this is output

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
fglrx is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by Hoplon on 2011-03-02
From what im reading I think my problem has to do with my monitor and xorg.conf file, so I tried 

```
sudo gedit /etc/X11/xorg.conf
```

and the file comes up blank. Any suggestions?

---

### Post by beew on 2011-03-02
First there is no more xorg.conf since 10.04. Secondly I am not sure you can install the ati graphic driver in WUBI (I can be wrong on this, but unlikely). WUBI is NOT a real dual boot, WUBI is a Windows program which you can uninstall with Add/Remove just like other Windows program, Ubuntu exists as a castrated version inside a Windows folder, if you really want to try Ubuntu give it full control by dual booting or install it in an external hard drive.

---

### Post by Hoplon on 2011-03-02
I thought it would have something to do with wubi. As for the xorg.conf file I had the X lower case in 
sudo gedit /etc/X11/xorg.conf once i fixed that it returned

```
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    Option        "UseFastTLS" "1"
    BusID       "PCI:1:5:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

Not sure if that makes a difference. I do want to give ubuntu a full try so i'll dual boot. Thanks for the help you two.

---

### Post by Hoplon on 2011-03-02
ubuntu is running off it's own partition now and i'm still having the same problem. Right before ubuntu goes to purple loading screen I see "unreliable CPU thermal, monitoring disabled" flash by.

---

### Post by Hoplon on 2011-03-04
Fixed I did this:
If you get "RADEONDRIGetVersion failed" in Xorg.0.log  it is because of a race issue. The radeon module is not initialized in  time before X is starting, and X will falsely believe that there is no  KMS support and do its own modesetting... 
To  make sure the radeon modules is initialized before gdm (and X) is  starting, insert "modprobe radeon" into your /etc/init/gdm.conf just  before the gdm-binary is executed: 
    ...
    initctl emit starting-dm DM=gdm

    modprobe radeon
    exec gdm-binary $CONFIG_FILE
end script

Found it [here]("https://wiki.ubuntu.com/X/KernelModeSetting").

Installing a linux game to see if I can play it!

---

