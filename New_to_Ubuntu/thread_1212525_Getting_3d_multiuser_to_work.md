---
title: "Getting 3d multiuser to work"
date: 2009-07-13
forum: New to Ubuntu
---

### Post by likeitfast on 2009-07-13
I wanted to try converting these instructions to ubunutu and see if they end up working.
[ 2 user multiseat with 3d working for debian]("http://www.automation.dn.ua/linux/3d-multiseat_en.html")
I am rather new to ubuntu but know very little about debian. Expecialy the small differences from ubuntu in terms of the xorg and gdm struture.
This is my attempt at converting the instructions to work on my computer.

cpu: AMD Atholon 64 Processor 3200+;Socket AM2
1024 Mb of ram
Videoadapter1 8400GS
Videoadapter2 7300LE

likeitfast@likeitfast-desktop:~$ lspci | grep VGA
04:00.0 VGA compatible controller: nVidia Corporation G72 [GeForce 7300 LE] (rev a1)
05:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)

My interpretation for my setup in xorg.conf
```
Section "ServerLayout"
    Identifier     "Seat0"
    Screen         "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "ServerLayout"
    Identifier     "Seat1"
    Screen         "Screen1" 0 0
    InputDevice    "Keyboard1" "CoreKeyboard"
    InputDevice    "Mouse1" "CorePointer"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
EndSection

Section "ServerFlags"

EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mouse1"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "Device" "/dev/input/event3"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Mouse1"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/input/mouse2"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard1"
    Driver         "kbd"
    Option         "Device" "/dev/input/event5"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HP MX90"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Unknown"
    ModelName      "HP MX90"
    HorizSync       30.0 - 95.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 LE"
    BusID          "PCI:4:0:0"
    Screen         0
EndSection
Section "Device"
    Identifier     "Device1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8400 LE"
    BusID          "PCI:5:0:0"
    Screen         1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Device1"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```
In the following instructions changed:
"/usr/share/gdm" to -> /etc/gdm/
defaults.conf* -> gdm.conf*



what I used in gdm.conf.multiseat
```
[servers]
# These are the standard servers.  You can add as many you want here and they
# will always be started.  Each line must start with a unique number and that
# will be the display number of that server.  Usually just the 0 server is
# used.
0=Standard0
1=Standard1

[server-Standard0]
name=Standard server #0
command=/usr/bin/X -sharevts -isolateDevice PCI:4:0:0 -layout seat1 :0
flexible=false

[server-Standard1]
name=Standard server #1
command=/usr/bin/X -sharevts -isolateDevice PCI:5:0:0 -layout seat0 :1
flexible=false

```

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          fake Xorg initialization
# Should-Start:      console-screen acpid
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: fake Xorg preinit script for multiseat system
# Description:       Debian preinit script for the multiseat system
### END INIT INFO
#
# Author:       Andrey Zhornyak 
#
set -e

PATH=/sbin:/bin:/usr/sbin:/usr/bin
GDM_SCRIPT=/etc/init.d/gdm                       
MULTISEAT_FILE=/usr/share/gdm/defaults.conf.multiseat #changed to /etc/gdm/gdm.conf.multiseat
ORIG_FILE=/usr/share/gdm/defaults.conf.orig #changed to /etc/gdm/gdm.conf.orig
SYMLINK_FILE=/usr/share/gdm/defaults.conf #changed to /etc/gdm/gdm.conf

test -x $GDM_SCRIPT || exit 0

case "$1" in
   start)
          rm -f $SYMLINK_FILE
          ln -s $ORIG_FILE $SYMLINK_FILE
          echo "Starting temporary single X server"
        /usr/bin/X -dpi 96 -audit 0 & #changed to X -dpi 96 -audit 0 &
        sleep 5
        /usr/bin/killall Xorg #changed to kill all Xorg
        rm -f $SYMLINK_FILE
        ln -s $MULTISEAT_FILE $SYMLINK_FILE
        exec /etc/init.d/gdm start
  ;;
  stop)
        exec /etc/init.d/gdm stop
  ;;
  reload)
  ;;
  restart|force-reload)
        $0 stop
        $0 start
  ;;
  *)
        echo "Usage: /etc/init.d/gdm-multiseat {start|stop|restart|reload|force-reload}"        exit 1
  ;;
esac

exit 0

```

now that I am writting it up I see a few things that look like naming errors in my code.

Thank you very much inhead of time.

Edit:
I got this setup working ish. but every time I hit return my screen shifts over.

Edit:
I just messed it up because I thought purging 'userful' was a good idea. I don't know what it did but after that it stoped working

---

### Post by likeitfast on 2009-08-18
i just wanted to update this. I managed to get it to work fine. just didn't get around to setting up sound and my mouse scroll doesn't work. but that does not matter much. I am also thinking of upgrading my system so it can handle games with 4 people.

---

### Post by likeitfast on 2009-08-18
also is there a way to get a groovix.com set up. that would be nice.

Edit: I am mistaken. The most recent version of 3D SLIM I can find is for Ubuntu 7.*

---

