---
title: "Need help setting up Ubuntu!! made some mistakes"
date: 2011-07-20
forum: New to Ubuntu
---

### Post by SuchetBargoti on 2011-07-20
Just got a new computer and decided to partition a bit of it to Ubuntu (along with Windows 7). Its a 64 bit, Dell xps 17. 

I installed Ubuntu from the CD, but when that was complete, unity didnt open up, the desktop was in classic mode. It mentioned that your hardware cannot support unity which is off as this is a very new computer (Nvidia Gforce GT 555M). So I thought this might be a driver problem.

Then I started typing these commands as they were recommended to some guy in some other forum who had a similar problem:
```
cp /etc/X11/xorg.conf /home/you
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
sudo /etc/init.d/gdm restart

```

Then the computer went to a terminal type screen (black) (as you can tell I am a complete noob)
I restarted the system by pressing ctrl + alt + delete. Now it always goes back to this screen which says things like:
```

speed-dispatched disabled; edit /etc/default/speech-dispatcher
* Stopping System V initialisation compatibility     [OK]
* Starting System V runlevel compatibility           [OK]
* Stopping automatic crash report generation         [fail]
* ...
...
..
..
* Starting restore sound card(s') mixer state(s)     [fail]

```

There is a whole list of these which I havent put up as I am having to manually type this up on my other computer (so sorry for any typing errors up there). 

I can access the terminal from here by pressing Ctrl + Alt + F1, But I dont know where to go from there.

Please need help quickly, thanks in advance

---

### Post by thefasterblueone on 2011-07-20
Try typing :

```
Ctrl + Alt + F7
```

---

### Post by Bodsda on 2011-07-20
> **SuchetBargoti said:**
> Just got a new computer and decided to partition a bit of it to Ubuntu (along with Windows 7). Its a 64 bit, Dell xps 17. 
 
I installed Ubuntu from the CD, but when that was complete, unity didnt open up, the desktop was in classic mode. It mentioned that your hardware cannot support unity which is off as this is a very new computer (Nvidia Gforce GT 555M). So I thought this might be a driver problem.
 
Then I started typing these commands as they were recommended to some guy in some other forum who had a similar problem:
```
cp /etc/X11/xorg.conf /home/you
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
sudo /etc/init.d/gdm restart

```
 
Then the computer went to a terminal type screen (black) (as you can tell I am a complete noob)
I restarted the system by pressing ctrl + alt + delete. Now it always goes back to this screen which says things like:
```

speed-dispatched disabled; edit /etc/default/speech-dispatcher
* Stopping System V initialisation compatibility     [OK]
* Starting System V runlevel compatibility           [OK]
* Stopping automatic crash report generation         [fail]
* ...
...
..
..
* Starting restore sound card(s') mixer state(s)     [fail]

```
 
There is a whole list of these which I havent put up as I am having to manually type this up on my other computer (so sorry for any typing errors up there). 
 
I can access the terminal from here by pressing Ctrl + Alt + F1, But I dont know where to go from there.
 
Please need help quickly, thanks in advance
 
If I remember correctly, nvidia-xconfig auto creates an xorg.conf file. If this is the case, getting back to the stage when you actually had a graphical desktop should be fairly simple. So, as you say, hit CTRL+ALT+F1 and then type the following command which will rename your xorg.conf file effectively removing the misconfiguration caused by nvidia-xconfig
 
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.broken

```
 
Then try running
```

sudo /etc/init.d/gdm restart

```
 
Or CTRL+ALT+F7
Or restart, and let us know whether you got back to a desktop environment.
 
HTH,
Bodsda

---

### Post by SuchetBargoti on 2011-07-20
Omg Bodsda, I love you!

Need to ask you some generic questions:
I just learnt that the screen you go into by pressing Ctrl+Alt+F1 is referred to as the 'Console'
What is the screen called that I was seeing before, with the "Ok"s and "Fail"s ?

Also back to my original problem:
The desktop is currently loading a classic form, I want it equipped with unity (I hope I am saying it right but Unity is the more appealing desktop with the applications tabs along the left of the screen?).

When I go into 

1. System-> Administration -> NVIDIA X Server Settings
A pop-up box comes up saying "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server. 
I dont know how to do the above or if I am meant to do it.

2. System -> Administration -> Additional Drivers 
The window opens with one option selected:
'NVIDIA accelerated graphics driver (version current) [Recommended]' 
and its status is: This driver is activated but not currently in use

Could you direct me towards the set up of unity

---

### Post by Bodsda on 2011-07-20
> **SuchetBargoti said:**
> Omg Bodsda, I love you!
 
Need to ask you some generic questions:
I just learnt that the screen you go into by pressing Ctrl+Alt+F1 is referred to as the 'Console'
What is the screen called that I was seeing before, with the "Ok"s and "Fail"s ?
 
Also back to my original problem:
The desktop is currently loading a classic form, I want it equipped with unity (I hope I am saying it right but Unity is the more appealing desktop with the applications tabs along the left of the screen?).
 
When I go into 
 
1. System-> Administration -> NVIDIA X Server Settings
A pop-up box comes up saying "You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server. 
I dont know how to do the above or if I am meant to do it.
 
2. System -> Administration -> Additional Drivers 
The window opens with one option selected:
'NVIDIA accelerated graphics driver (version current) [Recommended]' 
and its status is: This driver is activated but not currently in use
 
Could you direct me towards the set up of unity
 
Ok, the reason unity is not loading is probably because you are not using nvidia drivers. This may be due to missing kernel modules for nvidia, for which we need to reinstall the headers.
 
Open a terminal from the Applications menu and run the following command.
```

uname -a

```
Note the kernel number, something like 2.6.38-8
 
Then run the following commands, replacing the numbers with those you saw from the uname command
 
```

sudo apt-get install --reinstall linux-headers-2.6.38-8-generic-pae
sudo apt-get install --reinstall linux-image-2.6.38-8-generic-pae

```
 
After running this, reboot the machine. When it loads back up, load the hardware drivers section again and check the status of the nvidia driver. Hopefully it will no longer say "This driver is activated but not currently in use"
 
If this is the case, then we are on the right track. Now you should be able to rerun your nvidia-xconfig command, log out, log in and hopefully unity should be working.
 
> 
Need to ask you some generic questions:
I just learnt that the screen you go into by pressing Ctrl+Alt+F1 is referred to as the 'Console'
What is the screen called that I was seeing before, with the "Ok"s and "Fail"s ?

 
It is also a console. But it has different output because it is a seperate virtual console. It's not really something you need to worry about, just know that you can drop to any other tty by using ctrl+alt+F# - some will be running other things and be unusable, but some will be free.
 
HTH,
Bodsda

---

### Post by SuchetBargoti on 2011-07-20
> **Bodsda said:**
> Ok, the reason unity is not loading is probably because you are not using nvidia drivers. This may be due to missing kernel modules for nvidia, for which we need to reinstall the headers.
 
Open a terminal from the Applications menu and run the following command.
```

uname -a

```
Note the kernel number, something like 2.6.38-8
 
Then run the following commands, replacing the numbers with those you saw from the uname command
 
```

sudo apt-get install --reinstall linux-headers-2.6.38-8-generic-pae
sudo apt-get install --reinstall linux-image-2.6.38-8-generic-pae

```
 
After running this, reboot the machine. When it loads back up, load the hardware drivers section again and check the status of the nvidia driver. Hopefully it will no longer say "This driver is activated but not currently in use"
 


My kernel number was 2.6.38-10. Did the above step successfully, restarted comp, went to Additional Drivers, and it still says 'This driver is activated but not currently in use'.
Any ideas on where to go from here?

---

### Post by Bodsda on 2011-07-20
> **SuchetBargoti said:**
> My kernel number was 2.6.38-10. Did the above step successfully, restarted comp, went to Additional Drivers, and it still says 'This driver is activated but not currently in use'.
Any ideas on where to go from here?
 
Can you run the following command, it should load a graphical window with loads of settings and options, just ignore them. Let me know if it pops any dialog boxes up with info related to the driver or kernel module
```

sudo nvidia-settings

```
 
Also, could you pastebin the output of
```

dpkg -l | grep -i nvidia

```
 
and
```

cat /var/log/Xorg.0.log | grep -i nvidia

```
 
Cheers,
Bodsda

---

### Post by SuchetBargoti on 2011-07-20
> **Bodsda said:**
> Can you run the following command, it should load a graphical window with loads of settings and options, just ignore them. Let me know if it pops any dialog boxes up with info related to the driver or kernel module
```

sudo nvidia-settings

```
Loaded the NVIDIA X Server Settings, not that many setting options (only 5 check boxes). But anyways, yes there is a popup, 
"You do not appear to be using the NVIDIA X Driver, Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart X-server"

> **Bodsda said:**
> 
Also, could you pastebin the output of
```

dpkg -l | grep -i nvidia

```


```

ii  nvidia-common                         0.2.30                                     Find obsolete NVIDIA drivers
ii  nvidia-current                        270.41.06-0ubuntu1                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                       270.29-0ubuntu1                            Tool of configuring the NVIDIA graphics driver

```

> **Bodsda said:**
> 
and
```

cat /var/log/Xorg.0.log | grep -i nvidia

```Cheers,
Bodsda

```

[    12.426] (II) Module glx: vendor="NVIDIA Corporation"
[    12.426] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    12.510] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

---

### Post by Bodsda on 2011-07-20
> **SuchetBargoti said:**
> Loaded the NVIDIA X Server Settings, not that many setting options (only 5 check boxes). But anyways, yes there is a popup, 
"You do not appear to be using the NVIDIA X Driver, Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart X-server"
 
 
 
```

ii  nvidia-common                         0.2.30                                     Find obsolete NVIDIA drivers
ii  nvidia-current                        270.41.06-0ubuntu1                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                       270.29-0ubuntu1                            Tool of configuring the NVIDIA graphics driver

```
 
Ok cool, lets try the xconfig again. Hopefully, this time it will work. Please run 
```

sudo nvidia-xconfig

```
 
Restart gdm as before
```

sudo /etc/init.d/gdm restart

```
 
Log in (hopefully) and load the settings again.
```

sudo nvidia-settings

```
 
Do you still get the message about the driver not being used?
 
Cheers,
Bodsda

---

### Post by SuchetBargoti on 2011-07-20
I posted the output from 
```

cat /var/log/Xorg.0.log | grep -i nvidia

```
up there too.

Anyways I repeated those steps again and instead of restarting the desktop, it took me back to that weird console with the [OK]'s and [Fail]'s.
Then I restarted using Ctrl+Alt+Del
came back to this console, typed in Ctrl+Alt+F1
typed in the initial commands you gave me to fix this problem, and now I am back on the desktop just like before with the additional drivers saying "installed but not currently in use"

---

### Post by Bodsda on 2011-07-20
> **SuchetBargoti said:**
> I posted the output from 
```

cat /var/log/Xorg.0.log | grep -i nvidia

```
up there too.
 
Anyways I repeated those steps again and instead of restarting the desktop, it took me back to that weird console with the [OK]'s and [Fail]'s.
Then I restarted using Ctrl+Alt+Del
came back to this console, typed in Ctrl+Alt+F1
typed in the initial commands you gave me to fix this problem, and now I am back on the desktop just like before with the additional drivers saying "installed but not currently in use"
 
Ok, can you paste the contents of the /etc/X11/xorg.broken file
```

gksudo gedit /etc/X11/xorg.broken

```
 
Then we can see which driver it is trying to use.
 
Cheers,
Bodsda

---

### Post by SuchetBargoti on 2011-07-20
> **Bodsda said:**
> Ok, can you paste the contents of the /etc/X11/xorg.broken file
```

gksudo gedit /etc/X11/xorg.broken

```Then we can see which driver it is trying to use.
 
Cheers,
Bodsda

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by Bodsda on 2011-07-20
> **SuchetBargoti said:**
> ```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT 2011
 
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection
 
Section "Files"
EndSection
 
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
 
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection
 
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection
 
Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection
 
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
 
Ok, can you change the Driver info in the "Device" section from "nvidia" to "nv" Then run the following command
```

sudo cp /etc/X11/xorg.broken /etc/X11/xorg.conf

```
 
Then run
```

sudo /etc/init.d/gdm restart

```
 
And see if that works
 
Cheers,
Bodsda

---

### Post by SuchetBargoti on 2011-07-20
Same result as before unfortunately, repeated the whole process again, and then looked at the new broken file in gedit just to check i did change it to 'nv' and turns out that I did that part correctly 

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

As i mentioned right at the start that I am on a 64 bit system. The Ubuntu i have installed is the 32 bit version (after browsing online about information, it seemed that the 32 bit version can run normally on a 64 bit machine). I am pretty sure this is not the problem, but just stating it out. 
Thanks for you ongoing time and efforts, really appreciate it!

---

### Post by Bodsda on 2011-07-20
> **SuchetBargoti said:**
> Same result as before unfortunately, repeated the whole process again, and then looked at the new broken file in gedit just to check i did change it to 'nv' and turns out that I did that part correctly 
 
```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT 2011
 
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection
 
Section "Files"
EndSection
 
Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection
 
Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection
 
Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection
 
Section "Device"
    Identifier     "Device0"
    Driver         "nv"
    VendorName     "NVIDIA Corporation"
EndSection
 
Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```
 
As i mentioned right at the start that I am on a 64 bit system. The Ubuntu i have installed is the 32 bit version (after browsing online about information, it seemed that the 32 bit version can run normally on a 64 bit machine). I am pretty sure this is not the problem, but just stating it out. 
Thanks for you ongoing time and efforts, really appreciate it!
 
I dont think its architecture related, but thanks for restating. From some other info i've been reading, we may need to blacklist some of the other nvidia modules. So lets try that.
 
Run
```

gksudo gedit /etc/default/linux-restricted-modules-common

```
Look for a line that looks like           DISABLED_MODULES=" "
Change this to look like            DISABLED_MODULES="nv nvidia_new"
Then save the file.
 
Then run this again
```

sudo cp /etc/X11/xorg.broken /etc/X11/xorg.conf

```
 
Have another look at the xorg.conf file
```

gksudo gedit /etc/X11/xorg.conf

```
Ensure that the driver is now "nvidia", not "nv" - If this is the case, go ahead and restart gdm again
```

sudo /etc/init.d/gdm restart

```
 
Let me know how you get on this time,
Bodsda

---

### Post by SuchetBargoti on 2011-07-20
> **Bodsda said:**
> 
Run
```

gksudo gedit /etc/default/linux-restricted-modules-common

```Look for a line that looks like           DISABLED_MODULES=" "
Change this to look like            DISABLED_MODULES="nv nvidia_new"
Then save the file.
 
Apparently my computer doesn't have that file, When i run that line, it opens a blank document on gedit. Also I went into the /etc/default/ directory and its not there

---

### Post by Bodsda on 2011-07-20
> **SuchetBargoti said:**
> Apparently my computer doesn't have that file, When i run that line, it opens a blank document on gedit. Also I went into the /etc/default/ directory and its not there
 
Ok, do you have this file
/etc/modprobe.d/nvidia-graphics-drivers.conf
 
If you do, can you paste its contents
 
and the contents of this file
/etc/modprobe.d/blacklist.conf
 
Cheers,
Bodsda

---

### Post by SuchetBargoti on 2011-07-20
> **Bodsda said:**
> Ok, do you have this file
/etc/modprobe.d/nvidia-graphics-drivers.conf


If you do, can you paste its contents

```

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96

```
 
> **Bodsda said:**
> 
and the contents of this file
/etc/modprobe.d/blacklist.conf
 
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

---

### Post by Bodsda on 2011-07-20
> **SuchetBargoti said:**
> ```

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96

```
 
 
```

# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.
 
# evbug is a debug tool that should be loaded explicitly
blacklist evbug
 
# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd
 
# replaced by e100
blacklist eepro100
 
# replaced by tulip
blacklist de4x5
 
# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394
 
# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m
 
# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2
 
# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
 
# replaced by p54pci
blacklist prism54
 
# replaced by b43 and ssb.
blacklist bcm43xx
 
# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps
 
# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi
 
# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp
 
# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr
 
# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```
 
Ok, run
```

gksudo gedit /etc/modprobe.d/nvidia-graphics-drivers.conf

```

And add this line to the bottom of the file
```

alias nvidia nvidia-current

```
 
We also need to set the xorg file again
```

sudo cp /etc/X11/xorg.broken /etc/X11/xorg.conf

```
 
Then reboot. 
 
I am not gonna have access to the internet for the rest of the night unfortunately, so if this doesnt work, i'll continue this with you tomorrow.
 
Thanks for sticking with it.
Bodsda

---

### Post by SuchetBargoti on 2011-07-20
Added that line, copied xorg.broken onto xorg.conf, then restarted computer
Now i just get a blank screen after the ubuntu loading page. 
Terminal command (Ctrl+Alt+F1) doesnt display anything, but was able to restart the computer using ctrl+alt+del.
Am able to boot ubuntu in safe mode. Please advice when you get the time.

---

### Post by thefasterblueone on 2011-07-20
I've been following this thread and have looked up some additional info on this matter. 
Bodsda has been giving you some great help and I didn't want to interfere, but while he is away here is a link that you could use.

[http://askubuntu.com/questions/37084/nvidia-driver-activated-but-currently-not-in-use]("http://askubuntu.com/questions/37084/nvidia-driver-activated-but-currently-not-in-use")

There is alot of info, follow all links if necessary.

---

### Post by oldos2er on 2011-07-20
The "drivers are activated but not in use" is a known bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/777493](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/777493)

Have you tried booting into recovery mode, renaming the xorg.conf file and running ```
sudo apt-get update && sudo apt-get install nvidia-current
```

---

### Post by SuchetBargoti on 2011-07-20
> **oldos2er said:**
> The "drivers are activated but not in use" is a known bug: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/777493](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-173/+bug/777493)

Have you tried booting into recovery mode, renaming the xorg.conf file and running ```
sudo apt-get update && sudo apt-get install nvidia-current
```

I ran that statement in recovery more, it did a bunch of stuff and the last couple of lines said
```

nvidia-current is already the newest version
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

```
Then I tried to restart anyways and run in normal mode, same problem, blank screen

> **thefasterblueone said:**
> I've been following this thread and have looked up some additional info on this matter. 
Bodsda has been giving you some great help and I didn't want to interfere, but while he is away here is a link that you could use.

[http://askubuntu.com/questions/37084/nvidia-driver-activated-but-currently-not-in-use]("http://askubuntu.com/questions/37084/nvidia-driver-activated-but-currently-not-in-use")

There is alot of info, follow all links if necessary.

Thanks but I am currently one step behind, not being able to load any sort of desktop and stuck to deal with things in recovery mode

---

### Post by SuchetBargoti on 2011-07-20
I also trying this in safe mode with no success upon restart:
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by SuchetBargoti on 2011-07-20
I was able to start ubuntu in recovery mode and then select the option:
"Run in failsafe graphic mode"

There I selected a few other options such as reset graphics etc. 

Then I restarted the comp and booted in normal mode.

And YAY I can see the desktop

Now back to my original aim, seeing things in classic mode right now, want to enable unity! Any ideas guys?

---

### Post by wildmanne39 on 2011-07-20
Hi, run this in terminal so we can see what driver your are currently using.
```
lsmod
```
What it says about not currently in use is just a bug and you do not need to worry about that.

After you install your driver in additional drivers restart then at the login screen click on your user name and go to the bottom of the screen and choose ubuntu that is the one that is unity and see if it loads.

You may have to go into synaptic and remove some nvidia drivers if there are  two installed. It will only show one in additional drivers so you do need to look in synaptic.

---

### Post by Bodsda on 2011-07-21
> **wildmanne39 said:**
> Hi, run this in terminal so we can see what driver your are currently using.
```
lsmod
```
What it says about not currently in use is just a bug and you do not need to worry about that.
 
After you install your driver in additional drivers restart then at the login screen click on your user name and go to the bottom of the screen and choose ubuntu that is the one that is unity and see if it loads.
 
You may have to go into synaptic and remove some nvidia drivers if there are two installed. It will only show one in additional drivers so you do need to look in synaptic.
 
If thats the case, then the issue is that the nvidia drivers are failing to load (see the outputs from the xorg log on page 1 i think). 
 
My next suggestion would be to remove all nvidia drivers, and then reinstall those in the 'Additional drivers' section. 
 
Pasting the output of lsmod is also a good shout, hopefully we can get to the bottom of this issue today.
 
Bodsda
 
EDIT: Well, form the looks of [this]("http://ubuntuforums.org/showthread.php?t=1809012") post, you no longer have Ubuntu installed...

---

### Post by SuchetBargoti on 2011-07-21
Bodsda, Yes i panicked and attempted to reinstall ubuntu. not a smart decision. Anyways after a long day, I am back to square 1. where I am unable to activate unity, Additional drivers say that NVIDIA driver is activated but not currently in use. Would love if you could continue your assistance if you have time. 

Ultimately I am trying to work on the Xbox Kinect controller (if you know things about that then I will consider myself in heaven!!). I just trying to install the drivers for that and try run a live video stream and comes up with an error
"OpenGL GLX entension not supported by display"
I am hoping this again is a graphics problem so fixing the above problem might fix this too

---

### Post by Bodsda on 2011-07-21
> **SuchetBargoti said:**
> Bodsda, Yes i panicked and attempted to reinstall ubuntu. not a smart decision. Anyways after a long day, I am back to square 1. where I am unable to activate unity, Additional drivers say that NVIDIA driver is activated but not currently in use. Would love if you could continue your assistance if you have time. 
 
Ultimately I am trying to work on the Xbox Kinect controller (if you know things about that then I will consider myself in heaven!!). I just trying to install the drivers for that and try run a live video stream and comes up with an error
"OpenGL GLX entension not supported by display"
I am hoping this again is a graphics problem so fixing the above problem might fix this too
 
Fixing the nvidia drivers will probably resolve the OpenGL error you are getting. 
 
But back to the original issue, as this is now a clean install, please provide output of the following commands
 
```

lsmod

```
 
```

dmesg

```
 
```

lspci

```
 
```

dpkg -l | grep -i nvidia

```
 
```

cat /var/log/Xorg.0.log | grep -i nvidia

```
 
```

cat /etc/modprobe.d/nvidia-graphics-drivers.conf

```
 
```

cat /etc/modprobe.d/blacklist.conf

```
 
Also, please run these commands again
> 
```

uname -a

```
Note the kernel number, something like 2.6.38-8

Then run the following commands, replacing the numbers with those you saw from the uname command
```

sudo apt-get install --reinstall linux-headers-2.6.38-8-generic-pae
sudo apt-get install --reinstall linux-image-2.6.38-8-generic-pae

```

 
Also, please then uninstall the drivers, reinstall them and then run
```

sudo nvidia-xconfig

```
 
Let us all know how you get on,
Cheers,
Bodsda

---

### Post by SuchetBargoti on 2011-07-21
1. "lsmod"
```

Module                  Size  Used by
aesni_intel            17758  1 
cryptd                 19801  1 aesni_intel
aes_i586               16956  1 aesni_intel
aes_generic            38023  2 aesni_intel,aes_i586
binfmt_misc            13213  1 
rfcomm                 38125  8 
sco                    17827  2 
bnep                   17785  2 
l2cap                  48656  16 rfcomm,bnep
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_realtek   255882  1 
snd_hda_intel          24140  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
arc4                   12473  2 
nvidia               9766978  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
joydev                 17322  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
iwlagn                284778  0 
i915                  450969  2 
iwlcore               148965  1 iwlagn
soundcore              12600  1 snd
btusb                  18160  2 
mac80211              257001  2 iwlagn,iwlcore
drm_kms_helper         40745  1 i915
drm                   184133  3 i915,drm_kms_helper
bluetooth              65493  9 rfcomm,sco,bnep,l2cap,btusb
cfg80211              156212  3 iwlagn,iwlcore,mac80211
psmouse                59039  0 
dell_wmi               12601  0 
sparse_keymap          13666  1 dell_wmi
i2c_algo_bit           13184  1 i915
video                  18951  1 i915
uvcvideo               66851  0 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
videodev               75143  1 uvcvideo
serio_raw              12990  0 
dell_laptop            13515  0 
dcdbas                 14054  1 dell_laptop
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usbhid                 41704  0 
hid                    77084  1 usbhid
ahci                   21591  2 
libahci                25548  1 ahci
r8169                  46630  0 
xhci_hcd               72190  0 

```

2. "dmesg"
creates an extremely long script, what would be the best way to put that information up here?

3. "lspci"
```

00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation 2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.5 PCI bridge: Intel Corporation 6 Series Chipset Family PCI Express Root Port 6 (rev b5)
00:1d.0 USB Controller: Intel Corporation 6 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation HM67 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series Chipset Family 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series Chipset Family SMBus Controller (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation Device 0dcd (rev a1)
03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6230 (rev 34)
04:00.0 USB Controller: NEC Corporation uPD720200 USB 3.0 Host Controller (rev 04)
0a:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)

```

4. dpkg -l | grep -i nvidia
```


ii  nvidia-common                         0.2.30                                     Find obsolete NVIDIA drivers
ii  nvidia-current                        270.41.06-0ubuntu1                         NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                       270.29-0ubuntu1                            Tool of configuring the NVIDIA graphics driver

```

5. cat /var/log/Xorg.0.log | grep -i nvidia
```

[    14.820] (II) Module glx: vendor="NVIDIA Corporation"
[    14.820] (II) NVIDIA GLX Module  270.41.06  Mon Apr 18 15:11:28 PDT 2011
[    15.127] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

```

6. cat /etc/modprobe.d/nvidia-graphics-drivers.conf
```

blacklist nouveau
blacklist lbm-nouveau
blacklist nvidia-173
blacklist nvidia-96

```

7. cat /etc/modprobe.d/blacklist.conf
```


# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac

```

Give me a sec and I will run the rest of the things

---

### Post by SuchetBargoti on 2011-07-21
Reinstalled the linux headers and image for my kernel number

went to additional drivers, uninstalled then re installed the driver. then restarted the computer

Once back up ran sudo nvidia-xconfig
```



Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.

Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

```

the new X configuration file is:
```


# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 270.41.06  (buildmeister@swio-display-x86-rhel47-07.nvidia.com)  Mon Apr 18 15:15:12 PDT 2011

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       28.0 - 33.0
    VertRefresh     43.0 - 72.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

---

### Post by candtalan on 2011-07-21
I have just discovered Unity 2D. I think it is in the repository for Ubuntu 11.04 and possibly also for 10.10.
I am a bit surprised at how close it is to (full fat) Unity.
Might be worth a try.

---

### Post by zero2xiii on 2011-07-21
Hay sorry I'm budding in here...

un-install ALL Nvidia drivers and (download and) install the 270.41.06 dirvers if this isn't what you are using. I had the EXACT problem you are having, it still says my drivers are activated, but not in-use, but ALL 3D acceleration works.. Including unity and 3D intensive games inside wine..

---

### Post by SuchetBargoti on 2011-07-21
> **zero2xiii said:**
> Hay sorry I'm budding in here...

un-install ALL Nvidia drivers and (download and) install the 270.41.06 dirvers if this isn't what you are using. I had the EXACT problem you are having, it still says my drivers are activated, but not in-use, but ALL 3D acceleration works.. Including unity and 3D intensive games inside wine..

When you say uninstall and install drivers, I just open up the 'Additional Drivers' window which only displays one driver:
'NVIDIA accelerated graphics driver (version current) [Recommended]'

So I don't really know how to uninstall/install except that driver from this window

---

### Post by SuchetBargoti on 2011-07-21
> **candtalan said:**
> I have just discovered Unity 2D. I think it is in the repository for Ubuntu 11.04 and possibly also for 10.10.
I am a bit surprised at how close it is to (full fat) Unity.
Might be worth a try.

I will probably resort to that if this doesn't. But it seems like I really need to solve this graphics card problem as I hope to be interfacing with the Kinect camera, which gave me an OpenGL error.

---

### Post by SuchetBargoti on 2011-07-21
Hey Bodsda/others following this thread.

Past midnight here in Sydney so am heading off to bed. Please leave any recommendations and I have a look at them tomorrow

---

### Post by Bodsda on 2011-07-21
Ok, looking at those logs and outputs, it shows that the nvidia module got loaded, but never got used. What would be useful, is another copy of lsmod after we try to use the nvidia driver, dmesg and the xorg log.
 
So, please rerun
```

sudo nvidia-xconfig

```
 
Restart gdm with
```

sudo /etc/init.d/gdm restart

```
 
When this throws the black screen at you, drop to tty1 (ctrl+alt+F1)
Then run the following
 
```

sudo lsmod > /lsmod.log

```
```

sudo dmesg > /dmesg.log

```
```

sudo cat /var/log/Xorg.0.log | grep -i nvidia > /xorg.log

```
 
After you have run these commands, you can get your gui back
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.broken

```
```

sudo /etc/init.d/gdm restart

```
 
Please then paste these logs back here - (all logs are in the root of the filesystem '/')
/lsmod.log
/dmesg.log
/xorg.log
 
For pasting dmesg, please use [http://paste.ubuntu.com](http://paste.ubuntu.com)
 
From these logs, we will be able to see if the nvidia driver ever gets used (from lsmod output), we will see whether dmesg holds any errors regarding it, and also see if X.org threw any errors. Hopefully this will narrow things down for us.
 
Additionally, do you have more than one output port? (vga, hdmi, dvi etc.)
 
Cheers,
Bodsda

---

### Post by wildmanne39 on 2011-07-21
Hi, the problem I see is you have two graphic cards one built in intel card one nvidia you will have to disable your intel card to get the nvidia card to work properly.

---

### Post by SuchetBargoti on 2011-07-21
Hi Bodsda, 
The last thing I did last night was 
```

nvidia-xconfig

```
which did nothing while the computer was on. 

When I restarted the computer this morning, It was back to that black screen, but I saw your post (other comp). 
So i entered 
```

sudo lsmod > /lsmod.log

```
and it told me:
```

bash: /lsmod.log: Permission denied

```

Then i replaced a previous xorg file
```

sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

```
and restarted the server
```

sudo /etc/init.d/gdm restart

```

Now back on the desktop, I try run through your steps 
```

nvidia-xconfig

```
it said:
```

Using X configuration file: "/etc/X11/xorg.conf".

VALIDATION ERROR: Data incomplete in file /etc/X11/xorg.conf.
                  Device section "Default Device" must have a Driver line.


ERROR: Unable to write to directory '/etc/X11'.

```

The current xorg.conf file is (a short one):
```

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

```

So unfortunately I cant follow the rest of your steps as I am stuck at the first one. Please advice when you see this message.

Ports: I have a HDMI and a mini display port. After I get all this working I am hoping to extend the display to an external monitor via HDMI. I'll need your help on that too, I have that setup running on my old computer but now if the start the computer without the monitor connected (DVI) it doesn't display things properly. So to change to single monitor view, I have to have the external monitor connected and then change the settings to single monitor and then restart. I was hoping to have some sort of command to switch between single and dual monitors. I tried to follow these steps:
[http://www.dotkam.com/2007/06/02/switch_between_dual-single_monitor_on_ubuntu_linux/](http://www.dotkam.com/2007/06/02/switch_between_dual-single_monitor_on_ubuntu_linux/)
but didnt have much luck. Well that's down the track, gotta fix these drivers first.

P.s. I did a couple of other things to get the above to work, e.g. re download the linux headers , images + maybe some other random thing as I dont know why the xorg.conf is so small. I decided I will stop touching things until I get your guidance (unlike yesterday where I ended up reinstalling the whole operating system!)

---

### Post by SuchetBargoti on 2011-07-21
Also I went to the NVIDIA website and downloaded this driver:
[http://www.nvidia.com/object/linux-display-ia32-275.21-driver.html](http://www.nvidia.com/object/linux-display-ia32-275.21-driver.html)

Its the 32 bit version as I am running the 32 bit Ubuntu (or should I download 64 bit because of my computer specs?)

Anyways, Now I have a NVIDIA-Linux-x86-275.run file sitting in my downloads and not really sure if its need or what to do with it.

---

### Post by Bodsda on 2011-07-22
Whoops, my bad, forgot the sudo in front of nvidia-xconfig.
 
I have ammended my previous post, please run through again.

---

### Post by Bodsda on 2011-07-22
> **wildmanne39 said:**
> Hi, the problem I see is you have two graphic cards one built in intel card one nvidia you will have to disable your intel card to get the nvidia card to work properly.
 
I have built in graphics, and an nvidia graphics card and am succesfully running with the drivers without needing to disable the on-board one. Any reason to think that he may need to disable the intel graphics?
 
Cheers,
Bodsda

---

### Post by SuchetBargoti on 2011-07-22
> **Bodsda said:**
> Whoops, my bad, forgot the sudo in front of nvidia-xconfig.
 
I have ammended my previous post, please run through again.

woops, I feel stupider than usual :(

ok:
1. ```
sudo nvidia-xconfig
```
reconfigured xorg.conf file
2. ```
sudo /etc/init.d/gdm restart
```
Took me to the black screen
3. ```
sudo lsmod > /lsmod.log
```
returns:
```
 -bash: /lsmod.log: Permission denied 
```

currently leaving it in the console (not resetting any xorg files or restarting) till I get your response.

---

### Post by Bodsda on 2011-07-22
> **SuchetBargoti said:**
> woops, I feel stupider than usual :(
 
ok:
1. ```
sudo nvidia-xconfig
```
reconfigured xorg.conf file
2. ```
sudo /etc/init.d/gdm restart
```
Took me to the black screen
3. ```
sudo lsmod > /lsmod.log
```
returns:
```
 -bash: /lsmod.log: Permission denied 
```
 
currently leaving it in the console (not resetting any xorg files or restarting) till I get your response.
 
Hmm, thats strange. Try this
 
```

sudo lsmod >> ~/lsmod.mylog

```
 
Bodsda

---

### Post by SuchetBargoti on 2011-07-22
Ok this is what I did:
1. ```
sudo lsmod >> ~/lsmod.mylog
```
2. ```
sudo dmesg >> ~/dmesg.mylog
```
3. I accidently typed in the following, it didn't give an error
```
 sudo cat /var/log/Xorg.0.log | grep -i nvidia >xorg.log
```
Then I retyped the correct thing:
```
 sudo cat /var/log/Xorg.0.log | grep -i nvidia >> ~/xorg.mylog
```
4. ```
 mv /etc/X11/xorg.conf /etc/X11/xorg.broken
```
5. The following brought be back to my desktop ```
sudo /etc/init.d/gdm restart
```
6. ```
gksudo gedit lsmod.mylog
```
view lsmod log [here]("http://paste.ubuntu.com/649884/")
7. ```
gksudo gedit dmesg.mylog
```
view dmesg log [here]("http://paste.ubuntu.com/649886/")
8. ```
gksudo gedit xorg.mylog
```
view xorg log [here]("http://paste.ubuntu.com/649887/")


Where to from here?

---

### Post by Bodsda on 2011-07-22
> **SuchetBargoti said:**
>  
Where to from here?
 
Ok, can you now run
```

gksudo nvidia-settings

```
 
Do you get any popup messages?
 
Cheers,
Bodsda

---

### Post by SuchetBargoti on 2011-07-22
> **Bodsda said:**
> Ok, can you now run
```

gksudo nvidia-settings

```
 
Do you get any popup messages?
 
Cheers,
Bodsda

Unfortunately yes, same as before:

You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.

---

### Post by Bodsda on 2011-07-22
> **SuchetBargoti said:**
> Unfortunately yes, same as before:
 
You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.
 
Ok, can you please run
```

sudo apt-get install --reinstall nvidia-glx-new

```
 
Then, rerun the 
```

sudo nvidia-xsettings

```
 
Cheers,
Bodsda

---

### Post by SuchetBargoti on 2011-07-22
Sorry was away getting pizza
> **Bodsda said:**
> Ok, can you please run
```

sudo apt-get install --reinstall nvidia-glx-new

```

Cheers,
Bodsda

This is the return from the above command:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-glx-new

```

---

### Post by Bodsda on 2011-07-22
> **SuchetBargoti said:**
> Sorry was away getting pizza
 
 
This is the return from the above command:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package nvidia-glx-new

```
 
Ok, wasnt expecting that... Can you try this please
```

apt-cache search *nvidia*

```
 
Cheers,
Bodsda

---

### Post by SuchetBargoti on 2011-07-22
Input:
```

apt-cache search *nvidia*

```

Return:
```

E: Regex compilation error

```


Also not sure if this is relevant, but I started another thread earlier when I encountered a problem installing Ubuntu.

> **SuchetBargoti said:**
> Hi guys, Installing Ubuntu 11.04 right now, and get a popup saying:

Do you want to resume partitioning?
The attempt to mount a file system with type swap in SCSI2 (0,0,0), partition #6 (sdb) at none failed. 
You may resume partitioning from the partitioning menu.

The options are: [Go Back], [Continue]

I try pressing either of them and nothing happens. 

Down below on the installation status it says
"Creating ext file system for / in partition #5 of SCSI2 (0,0,0)(sdb)..."

Please help urgently as the installation is current in progress on my other computer. Thanks in advance

I ended up having to force shutdown, and just went through the installation process again and it worked well (giving me the Ubuntu I have now).

---

### Post by Bodsda on 2011-07-22
> **SuchetBargoti said:**
> Input:
```

apt-cache search *nvidia*

```
 
Return:
```

E: Regex compilation error

```
 
ok, try without the asterix's
```

apt-cache search nvidia

```
 
Sorry for the mass of mistakes so far. Im doing this all from memory, I have no access to my ubuntu machine at the moment
 
Bodsda

---

### Post by SuchetBargoti on 2011-07-22
> **Bodsda said:**
> ok, try without the asterix's
```

apt-cache search nvidia

```
 
Sorry for the mass of mistakes so far. Im doing this all from memory, I have no access to my ubuntu machine at the moment
 
Bodsda

```


dmraid - Device-Mapper Software RAID support tool
jockey-common - user interface and desktop integration for driver management
jockey-gtk - GNOME user interface and desktop integration for driver management
jockey-kde - KDE user interface and desktop integration for driver management
libvdpau-dev - Video Decode and Presentation API for Unix (development files)
libvdpau-doc - Video Decode and Presentation API for Unix (documentation)
libvdpau1 - Video Decode and Presentation API for Unix (libraries)
nvidia-common - Find obsolete NVIDIA drivers
nvidia-settings - Tool of configuring the NVIDIA graphics driver
xserver-xorg-video-nouveau - X.Org X server -- Nouveau display driver (experimental)
xserver-xorg-video-nouveau-dbg - X.Org X server -- Nouveau display driver (debug symbols)
nvidia-173 - NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-173-dev - NVIDIA binary Xorg driver development files
nvidia-173-kernel-source - Transitional package for nvidia-glx-173-kernel-source
nvidia-180-kernel-source - Transitional package for nvidia-glx-185-kernel-source
nvidia-180-libvdpau - Transitional package for nvidia-185-libvdpau
nvidia-180-libvdpau-dev - Transitional package for nvidia-185-libvdpau-dev
nvidia-185-kernel-source - Transitional package for nvidia-glx-185-kernel-source
nvidia-185-libvdpau - Transitional package for nvidia-185-libvdpau
nvidia-185-libvdpau-dev - Transitional package for nvidia-185-libvdpau-dev
nvidia-96 - NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-96-dev - NVIDIA binary Xorg driver development files
nvidia-96-kernel-source - Transitional package for nvidia-glx-96-kernel-source
nvidia-current - NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-current-dev - NVIDIA binary Xorg driver development files
nvidia-glx-173 - Transitional package for nvidia-glx-173
nvidia-glx-173-dev - Transitional package for nvidia-glx-173-dev
nvidia-glx-180 - Transitional package for nvidia-glx-185
nvidia-glx-180-dev - Transitional package for nvidia-glx-185-dev
nvidia-glx-185 - Transitional package for nvidia-glx-185
nvidia-glx-185-dev - Transitional package for nvidia-glx-185-dev
nvidia-glx-96 - Transitional package for nvidia-glx-96
nvidia-glx-96-dev - Transitional package for nvidia-glx-96-dev
conky-all - highly configurable system monitor (all features enabled)
cpufreqd - fully configurable daemon for dynamic frequency and voltage scaling
gimp-normalmap - Normal map plugin for GIMP
nvclock - Allows you to overclock your nVidia card under GNU/Linux
nvclock-gtk - Allows you to overclock your nVidia card under GNU/Linux
nvclock-qt - Allows you to overclock your nVidia card under GNU/Linux
nvidia-180-modaliases - Transitional package for nvidia-185-modaliases
nvtv - tool to control TV chips on NVidia cards under Linux
pyrit - A GPGPU-driven WPA/WPA2-PSK key cracker
sensors-applet - Display readings from hardware sensors in your Gnome panel
smartdimmer - Change LCD brightness on Geforce cards
sysinfo - display computer and system information
trigger-rally-data - free 3D rally racing car game - data files
vdpau-va-driver - VDPAU-based backend for VA API
xserver-xorg-video-nv - X.Org X server -- NV display driver
nouveau-firmware - Firmware for nVidia graphics cards
nvidia-cg-toolkit - Cg Toolkit - GPU Shader Authoring Language

```

I can't thank you enough for all your time and efforts

---

### Post by Bodsda on 2011-07-22
> **SuchetBargoti said:**
> ```

 
dmraid - Device-Mapper Software RAID support tool
jockey-common - user interface and desktop integration for driver management
jockey-gtk - GNOME user interface and desktop integration for driver management
jockey-kde - KDE user interface and desktop integration for driver management
libvdpau-dev - Video Decode and Presentation API for Unix (development files)
libvdpau-doc - Video Decode and Presentation API for Unix (documentation)
libvdpau1 - Video Decode and Presentation API for Unix (libraries)
nvidia-common - Find obsolete NVIDIA drivers
nvidia-settings - Tool of configuring the NVIDIA graphics driver
xserver-xorg-video-nouveau - X.Org X server -- Nouveau display driver (experimental)
xserver-xorg-video-nouveau-dbg - X.Org X server -- Nouveau display driver (debug symbols)
nvidia-173 - NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-173-dev - NVIDIA binary Xorg driver development files
nvidia-173-kernel-source - Transitional package for nvidia-glx-173-kernel-source
nvidia-180-kernel-source - Transitional package for nvidia-glx-185-kernel-source
nvidia-180-libvdpau - Transitional package for nvidia-185-libvdpau
nvidia-180-libvdpau-dev - Transitional package for nvidia-185-libvdpau-dev
nvidia-185-kernel-source - Transitional package for nvidia-glx-185-kernel-source
nvidia-185-libvdpau - Transitional package for nvidia-185-libvdpau
nvidia-185-libvdpau-dev - Transitional package for nvidia-185-libvdpau-dev
nvidia-96 - NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-96-dev - NVIDIA binary Xorg driver development files
nvidia-96-kernel-source - Transitional package for nvidia-glx-96-kernel-source
nvidia-current - NVIDIA binary Xorg driver, kernel module and VDPAU library
nvidia-current-dev - NVIDIA binary Xorg driver development files
nvidia-glx-173 - Transitional package for nvidia-glx-173
nvidia-glx-173-dev - Transitional package for nvidia-glx-173-dev
nvidia-glx-180 - Transitional package for nvidia-glx-185
nvidia-glx-180-dev - Transitional package for nvidia-glx-185-dev
nvidia-glx-185 - Transitional package for nvidia-glx-185
nvidia-glx-185-dev - Transitional package for nvidia-glx-185-dev
nvidia-glx-96 - Transitional package for nvidia-glx-96
nvidia-glx-96-dev - Transitional package for nvidia-glx-96-dev
conky-all - highly configurable system monitor (all features enabled)
cpufreqd - fully configurable daemon for dynamic frequency and voltage scaling
gimp-normalmap - Normal map plugin for GIMP
nvclock - Allows you to overclock your nVidia card under GNU/Linux
nvclock-gtk - Allows you to overclock your nVidia card under GNU/Linux
nvclock-qt - Allows you to overclock your nVidia card under GNU/Linux
nvidia-180-modaliases - Transitional package for nvidia-185-modaliases
nvtv - tool to control TV chips on NVidia cards under Linux
pyrit - A GPGPU-driven WPA/WPA2-PSK key cracker
sensors-applet - Display readings from hardware sensors in your Gnome panel
smartdimmer - Change LCD brightness on Geforce cards
sysinfo - display computer and system information
trigger-rally-data - free 3D rally racing car game - data files
vdpau-va-driver - VDPAU-based backend for VA API
xserver-xorg-video-nv - X.Org X server -- NV display driver
nouveau-firmware - Firmware for nVidia graphics cards
nvidia-cg-toolkit - Cg Toolkit - GPU Shader Authoring Language

```
 
I can't thank you enough for all your time and efforts
 
When you look in the 'additional drivers' sections, does it say what driver number or version you where trying to install?
 
Cheers,
Bodsda

---

### Post by pqwoerituytrueiwoq on 2011-07-22
i think you need nomodeset in your kernel's boot line to keep the default driver from taking over
for legacy grub there is this line in /boot/grub/menu.lst
# defoptions=quiet splash
once you add nomodeset to that line like this 
# defoptions=quiet splash nomodeset
sudo update-grub
i don't remember for grub 2

---

### Post by SuchetBargoti on 2011-07-22
> **Bodsda said:**
> When you look in the 'additional drivers' sections, does it say what driver number or version you where trying to install?
 
Cheers,
Bodsda

The highlighted (and the only) driver is labeled:

NVIDIA accelerated graphics driver (version current) [Recommended]

Also bodsda, what are your views to pqwoerituytrueiwoq's comment?

---

### Post by Bodsda on 2011-07-22
> **SuchetBargoti said:**
> The highlighted (and the only) driver is labeled:
 
NVIDIA accelerated graphics driver (version current) [Recommended]
 
Also bodsda, what are your views to pqwoerituytrueiwoq's comment?
 
Theres no number like 170 or 185?
 
Erm, the kernel boot param, its worth a shot, but you need to be careful about changing these parameters because you could render your system unbootable. And it will beslightly confusing to explain how to undo these options from within the grub bootloader.
 
I would recommend creating a new grub entry with this line, not editing the current one. Do you know if you are using grub2 (v1.99)? If not, what version of Ubuntu are you running?
 
Cheers,
Bodsda

---

### Post by SuchetBargoti on 2011-07-22
> **Bodsda said:**
> Theres no number like 170 or 185?
 
No there is no number.
> **Bodsda said:**
> 
Erm, the kernel boot param, its worth a shot, but you need to be careful about changing these parameters because you could render your system unbootable. And it will beslightly confusing to explain how to undo these options from within the grub bootloader.
 
I would recommend creating a new grub entry with this line, not editing the current one. Do you know if you are using grub2 (v1.99)? If not, what version of Ubuntu are you running?

I installed Ubuntu 11.04. Dont know much about grub or what version it is.

I have also got the same ubuntu on my older computer <-- thats probably highly irrelevant here :).

---

### Post by Bodsda on 2011-07-22
> **SuchetBargoti said:**
> No there is no number.
 
I installed Ubuntu 11.04. Dont know much about grub or what version it is.
 
I have also got the same ubuntu on my older computer <-- thats probably highly irrelevant here :).
 
Ok, your probably using grub2, but I don't think it matters with this approach. Please follow [this]("https://help.ubuntu.com/community/BootOptions#Change Boot Options Temporarily For An Existing Installation") link to test the boot parameter change. Let me know if you have any problems following that section
  
Bodsda

---

### Post by SuchetBargoti on 2011-07-22
I have GeForce 9500M GS on the old comp (Asus M51Sn)

Half way through that link, under:
"Change Boot Options Temporarily For An Existing Installation"
It says 
"For Ubuntu 9.10 (Karmic Koala) or later, please see Grub2"

which links to [here]("http://help.ubuntu.com/community/Grub2").

There is too much information on that page and I am too scared to try anything as I am unsure of what exactly I a trying to do, don't really understand what it means to 'test the boot parameter change'.

---

### Post by Bodsda on 2011-07-22
> **SuchetBargoti said:**
> I have GeForce 9500M GS on the old comp (Asus M51Sn)
 
Reading through that link, well be in touch if I get stuck
 
Any problems with the drivers on that machine?
 
Bodsda

---

### Post by SuchetBargoti on 2011-07-22
nope, unity running fine, got dual monitors and desktop cube happening there too

I edited that previous comment incase you missed it.

---

### Post by Bodsda on 2011-07-22
> **SuchetBargoti said:**
> nope, unity running fine, got dual monitors and desktop cube happening there too
 
I edited that previous comment incase you missed it.
 
hmm, ok. I don't know enough about grub2 to give proper instructions. I will have to wait until I'm home to do some testing unfortunately.
 
If anyone is watching this thread and can provide info on one time boot param changes in grub2, please post.
 
Cheers,
Bodsda

---

### Post by SuchetBargoti on 2011-07-22
> **Bodsda said:**
> hmm, ok. I don't know enough about grub2 to give proper instructions. I will have to wait until I'm home to do some testing unfortunately.
 
If anyone is watching this thread and can provide info on one time boot param changes in grub2, please post.
 
Cheers,
Bodsda

When do you get back home? (just so I know when to expect your contact).

Also do you prefer to communicate through here later or would some type on instant messaging be better? I guess this sort of communication allows you to present code nicely and keeps good track of the progress for everyone to see (there... I think I have answered myself).

Note to all others: I am open to any suggestions on this topic!

---

### Post by fi2 on 2011-07-22
AFAIK Dell XPS 17 has a hybrid Nvidia Optimus graphics. I spent ages struggling with the proprietary Nvidia drivers on a similar machine, but Unity never started.

Then, after I messed my Ubuntu 11.04 completely I decided to reinstall it, but this time I did not allow to install proprietary drivers. Unity started, and I have used it (and compiz) ever since.

I found a very nice explanation [COLOR="Blue"]_[here]("http://ubuntuforums.org/showthread.php?t=1657660&highlight=nvidia+optimus")_[/COLOR]. It was some time ago, but it still looks that Nvidia does not support optimus in linux. So I still have the intel driver in my xorg.conf. 

I installed bumblebee, but power usage went astronomical, so I gave in. I am not an expert of graphics cards, and I couldn't afford the time to experiment, but It seems others used it ok.
I use the machine for work, so no idea about how 3D games would run, but it is perfect for some CAD apps.

---

### Post by SuchetBargoti on 2011-07-22
> **fi2 said:**
> AFAIK Dell XPS 17 has a hybrid Nvidia Optimus graphics. I spent ages struggling with the proprietary Nvidia drivers on a similar machine, but Unity never started.

Then, after I messed my Ubuntu 11.04 completely I decided to reinstall it, but this time I did not allow to install proprietary drivers. Unity started, and I have used it (and compiz) ever since.

I found a very nice explanation [COLOR="Blue"]_[here]("http://ubuntuforums.org/showthread.php?t=1657660&highlight=nvidia+optimus")_[/COLOR]. It was some time ago, but it still looks that Nvidia does not support optimus in linux. So I still have the intel driver in my xorg.conf. 

I like that explanation! So if I already have the restricted drivers downloaded, do I just go into 'Additional Drivers' and select remove, and just run with that?
Currently I just want to use the machine to connect the Kinect camera, no gaming or anything (I have dual boot Windows 7 for that). Previously when I tried it, it gave me some OpenGl error. 

> **fi2 said:**
> 
I installed bumblebee, but power usage went astronomical, so I gave in. I am not an expert of graphics cards, and I couldn't afford the time to experiment, but It seems others used it ok.
I use the machine for work, so no idea about how 3D games would run, but it is perfect for some CAD apps.
I am not an expert on any computing so if I was to follow the steps to install bumblebee, would it be easy enough to remove it if I don't like? With reference to the power requirements, considering my computer is less than a week old, I think it should be able to handle it.



Also Bodsda, what do you think? Is this a lost case considering what is mentioned in that linked post about problems with Nvidia Optimus?

---

### Post by Bodsda on 2011-07-22
> **SuchetBargoti said:**
> I like that explanation! So if I already have the restricted drivers downloaded, do I just go into 'Additional Drivers' and select remove, and just run with that?
Currently I just want to use the machine to connect the Kinect camera, no gaming or anything (I have dual boot Windows 7 for that). Previously when I tried it, it gave me some OpenGl error. 
 
 
I am not an expert on any computing so if I was to follow the steps to install bumblebee, would it be easy enough to remove it if I don't like? With reference to the power requirements, considering my computer is less than a week old, I think it should be able to handle it.
 
 
 
Also Bodsda, what do you think? Is this a lost case considering what is mentioned in that linked post about problems with Nvidia Optimus?
 
Anything is worth a go. Do the uninstall as you said, and see what happens :)

---

### Post by SuchetBargoti on 2011-07-22
> **Bodsda said:**
> Anything is worth a go. Do the uninstall as you said, and see what happens :)

:)

Ok first trying out the bumblebee setup:
```

sudo apt-add-repository ppa:mj-casalogic/bumblebee
sudo apt-get update
sudo apt-get install bumblebee

```

---

### Post by fi2 on 2011-07-22
SB You can remove bumblebee without problem if you don't like it. The reason I decided to quit was, that the fan boosted up, and turned my laptop to a hair-drier.

It seems the open nvidia project nouveau also [COLOR="Blue"]_[has a solution]("http://linux-hybrid-graphics.blogspot.com/2011/04/linux-nouveau-intelnvidia-working-with.html")_[/COLOR], but so far I haven't seen too much feedback, so I think I'd rather wait.

Do you have the intel driver installed? Also, beware, bumblebee is not used by Ubuntu, you have to use bumblebee commands to start the 3D application.

---

### Post by SuchetBargoti on 2011-07-22
yay unity works!!

thanks a lot fi2, and many thanks to bodsda for your time and efforts.

As for bumblebee, I have got desktop cube working :D
Some glitches here and there, i.e. on restart, system hangs at the purple screen after the grub menu, some 3D rendering apps lag heaps or hang and gotta restart them. But better than no solution!!

Haha, that link you just sent me about Nouveau:
"If you have a Linux hybrid graphics laptop and a _bit of time for testing_"
Yeh, I think i'll pass that, maybe in a few months they come up with something concrete

next thing (maybe I should make a new thread for this)
_Need to get dual monitors with an HDMI port._
It was easy on my old comp by going into NVIDIA X Server Settings
But now when i go onto this, i get the error: 
"You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server."

Update:
Post [here]("https://github.com/MrMEEE/bumblebee/issues/75") talking about a similar thing, see post from rockorequin. Gotta go buy a minidisplay port to hdmi connector!

---

### Post by fi2 on 2011-07-22
Well, it seems there is still something to do on your system. 

Just to make it sure: bumblebee is not required for compiz, you can use desktop effects without it. Also, my machine with the intel driver does single and dual monitor on HDMI as well as Win7 does. You shouldn't have trouble with that at all.

How does your /etc/X11/xorg.conf look?

---

### Post by wildmanne39 on 2011-07-22
Hi Bodsda, yes the reason I thought that it was a problem with both cards installed is because of the issues with Optimus,I have the same instructions for bumblebee that I was going to give, but I have been distracted my wife was in the hospital and I left out the part about the Optimus issue.

I am sorry about that, you are doing a great job and I am going to back out know that you are aware of the issue.

---

### Post by fi2 on 2011-07-22
Hi all. Sorry for having burst into the thread this blunt, but with the limited time I have, that was all I could afford. But then, I really appreciate the huge work people like 3602 or Bodsda (list goes) do. Optimus seems to cause a lot of headache to people with new models, but it is getting better, so I trust it will be cracked finally.

---

### Post by SuchetBargoti on 2011-07-22
> **fi2 said:**
> Well, it seems there is still something to do on your system. 

Just to make it sure: bumblebee is not required for compiz, you can use desktop effects without it. Also, my machine with the intel driver does single and dual monitor on HDMI as well as Win7 does. You shouldn't have trouble with that at all.

How does your /etc/X11/xorg.conf look?

Sorry I am a bit new to all this. How would you define the problem I was having? Previously when I didn't have unity, was it just using the integrated intel card? And now with bumblebee it can use the nvidia card (but now it just uses the nvidia card as opposed to switching between them in a smart way like in windows)?

And I though config was one of the features of Unity, If all those "cool" effects compiz provides available without unity, what is the purpose of unity except the taskbar on the left hand side?

w.r.t. dual monitors, do you mean if I was to stay at my previous settings (without bumblebee, using the integrated graphics card) I can just plug in my HDMI cable and view the output. 

The one thing I was missing previously (before bumblebee) was that I was unable to connect my Kinect camera due to some OpenGL issues. Now there arnt any problems with that.

Regarding xorg.conf:
It doesn't seem to exist right now,
When I type in 
```

gksudo gedit /etc/X11/xorg.conf

```
I get an empty document in gedit

Here are the list of files I haev on /etc/X11/
```


app-defaults             X                 xorg.conf.nvidia  Xsession.d
cursors                  xinit             Xreset            Xsession.options
default-display-manager  xkb               Xreset.d          Xwrapper.config
fonts                    xorg.broken       Xresources
rgb.txt                  xorg.conf.backup  Xsession

```

---

### Post by fi2 on 2011-07-27
Hi SuchetBargoti,
As I said, I have never had the time to dig too deep into video adapters (it is on my list, but is is just too long :) ). As the above thread says, nvidia-optimus is actually not a dual video card, in terms of one could select which one to use. The system can see the low power intel (with 3D support itself), and for computation consuming 3D applications it can invoke the peckish nvidia 3D engine. Generating the video output is down to the intel GPU anyway. Bumblebee can activate nvidia for single apps on user demand, but as they say, it cannot do it automatically, and they look for developers to finalize it. 

For a while the only way to configure X server used to be editing xorg.conf, however later releases can also auto configure. (I think it came with desktop distributions). If there is an xorg.conf, it will however override autoconfig. Editing it manually gives some nice and tricky features, but I found autoconfig works pretty well, so I haven't met a case to have to do it for a while.

HDMI: I connected it and it just worked fine. The only reason I needed some manual editing was to put the Unity launcher on my external monitor.

Unity (3D) is a compiz plugin, so you are right, that it is not needed to get compiz desktop effects. I know quite a few people, insisting to classic desktop (yet, with compiz). I found however Unity was nice, mainly for three reasons: launcher bar works out better to me than panels, search is at hand and fast, and the single line window headers cover less useful monitor height. I started to play with it a bit skeptically, but then I stayed with it.

I found Ubuntu has always been good in spotting actual problems, and nouveau driver is also said to have cracked the switching matter, so I am looking forward to seeing how it goes with further updates.

---

