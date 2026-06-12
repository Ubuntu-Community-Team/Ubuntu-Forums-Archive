---
title: "DPMS (Power Mgmt Sys) is Not Working"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by dwhitney67 on 2010-02-22
I have a 6-year old laptop with an ATI Radeon video chip-set, which I believe is the X1100 (maybe X1300).  The only information I have about it is the following:
```

ATI Technologies Inc Radeon RV250 [Mobility FireGL 9000] (rev 01)

```
A few weeks ago, the DPMS (or something related) stopped working, possibly due to an **Ubuntu 9.10** update.  The external monitor I use is no longer placed in it's "sleep" mode after a certain period of inactivity.

Can someone please point me in a direction where I can sort this issue out?  I want to stop wasting power, and hence money, when the monitor (and my system) are not in use.

This is my xorg.conf file, which IMO is not very helpful:
```

Section "Monitor"
        Identifier      "Configured Monitor"
        Option          "DPMS" "true"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        SubSection "Display"
                Virtual 2560 800
        EndSubSection
EndSection

Section "Device"
        Identifier      "Configured Video Device"
EndSection

```

The current "xset -q" results are:
```

Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000000
  auto repeat delay:  660    repeat rate:  25
  auto repeating keys:  00ffffffdffffbbf
                        fadfffefffedffff
                        9fffffffffffffff
                        fff7ffffffffffff
  bell percent:  0    bell pitch:  400    bell duration:  100
Pointer Control:
  acceleration:  2/1    threshold:  4
Screen Saver:
  prefer blanking:  yes    allow exposures:  yes
  timeout:  0    cycle:  0
Colors:
  default colormap:  0x20    BlackPixel:  0    WhitePixel:  16777215
Font Path:
  /usr/share/fonts/X11/misc,/usr/share/fonts/X11/100dpi/:unscaled,/usr/share/fonts/X11/75dpi/:unscaled,/usr/share/fonts/X11/Type1,/usr/share/fonts/X11/100dpi,/usr/share/fonts/X11/75dpi,/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,built-ins
DPMS (Energy Star):
  Standby: 0    Suspend: 0    Off: 0
  DPMS is Enabled
  Monitor is On

```

I have edited the screensaver and power management options via the Gnome utility to be enabled 5 minutes after no user activity is detected.  The screensaver works, however the monitor remains on.  These settings do not seem to be listed in the "xset -q" results above; can anyone explain this?

P.S.  The monitor is an Acer LCD X203H which supports DPMS.

---

### Post by dwhitney67 on 2010-03-05
<bump>

Does anyone have any ideas/suggestions to resolve, or even investigate this issue I reported a week ago?

My external monitor is placed into standby-mode when I log out of my account, but it will not enter this mode when I am logged in.

Is it possible that my personal power-management configuration is different from the system's?  Where are these config settings stored??

---

### Post by Redache on 2010-03-05
You might get a better response in the general support forums as this is above the level of normal support needed in Absolute Beginners.

---

### Post by dwhitney67 on 2010-03-08
I finally came up with the correct Google search words, and found a link that offered sane advice on how to enable the DPMS.  Basically, it boils down to the following:
```

xset +dpms            # enable DPMS
xset dpms 0 0 300     # 5 minute timeout

```
I ran both of these commands as root and it worked like a charm; thus I decided to place them in a script (within /usr/local/bin), so that it can be called via /etc/rc.local each time the system is rebooted.

---

### Post by Schuby007 on 2010-11-10
> **dwhitney67 said:**
> I finally came up with the correct Google search words, and found a link that offered sane advice on how to enable the DPMS.  Basically, it boils down to the following:
```

xset +dpms            # enable DPMS
xset dpms 0 0 300     # 5 minute timeout

```I ran both of these commands as root and it worked like a charm; thus I decided to place them in a script (within /usr/local/bin), so that it can be called via /etc/rc.local each time the system is rebooted.

Hi,

I'm having the same problem you were having. I've gone ahead and ran

```
xset dpms 0 0 1800    # I wanted a 30 minute delay before screen powers off
```as root. How do I set the computer up so that the setting is maintained after reboot? I'm a total linux n00b so I don't know how to make a script.

Also, why doesn't Ubuntu just do what I asked it to do in System->Preferences->Power Management??

---

### Post by dwhitney67 on 2010-11-10
Since I last posted on this thread, I have found that part of the solution that I wrote about did not work as I would have hoped.

I did finally find a good solution, but I forgot to come back to this thread.

Here's what I did...

**Step 1**:  Create a shell-script called */usr/local/bin/enable_dpms*.
```

sudo vi /usr/local/bin/enable_dpms

```
The script contains the following:
```

#!/bin/bash

sleep 20        # arbitrary delay to allow Gnome (ie Power Mgr) to fully start up.

if [ "$DISPLAY" != "" ]
then
        timeout=`xset -q | grep Off | awk '{print $6}'`

        while [ $timeout -eq 0 ]
        do
                xset -display $DISPLAY +dpms            # enable DPMS
                xset -display $DISPLAY dpms 0 0 300     # turn off display after 5 minutes of idling

                if [ $? -eq 0 ]
                then
                        break
                else
                        sleep 10
                fi
        done
fi

```
After the file has been saved, exit the editor, and then set the appropriate permissions:
```

sudo chmod 755 /usr/local/bin/enable_dpms

```

**Step 2**:  Enable a start up program under Gnome.  Here's how...
```

a) Choose **System->Preferences->Startup Applications**

b) Select **Add**

c) Complete the fields in the dialog box; for the Name, enter Enable DPMS; for the command, enter /usr/local/bin/enable_dpms.  Insert a comment if you wish.

```

**Step 3**:  Logout of Gnome.

**Step 4**:  Log back in.

Voilà!


P.S.  The script probably could be written better.  I was not seeking a Pulitzer, thus the mere fact that it works is good enough for me.

---

### Post by Mark124 on 2010-12-26
thanks for putting that script together.  However I believe you left out a timeout variable set in while which will create an infinite loop.  Here's my corrected version, pardon the style change.

#!/bin/bash

sleep 20        # arbitrary delay to allow Gnome (ie Power Mgr) to fully start up.

if [ "$DISPLAY" = "" ]; then exit 1
fi

timeout=`xset -q | grep Off | awk '{print $6}'`

while [ $timeout -eq 0 ]; do

   xset -display $DISPLAY +dpms            # enable DPMS
   xset -display $DISPLAY dpms 0 0 300     # turn off display after 5 minutes of idling

   if [ $? -eq 0 ]; then break
   else sleep 10
   fi
   
   timeout=`xset -q | grep Off | awk '{print $6}'`
done

i tried it on this laptop Dell Inspiron B130 running ubuntu 10.10 and it works.  I wonder what the real problem is since I don't see this issue on my newer Asus laptop.

---

### Post by troitino on 2011-03-19
> **Mark124 said:**
> thanks for putting that script together.  However I believe you left out a timeout variable set in while which will create an infinite loop.  Here's my corrected version, pardon the style change.

#!/bin/bash

sleep 20        # arbitrary delay to allow Gnome (ie Power Mgr) to fully start up.

if [ "$DISPLAY" = "" ]; then exit 1
fi

timeout=`xset -q | grep Off | awk '{print $6}'`

while [ $timeout -eq 0 ]; do

   xset -display $DISPLAY +dpms            # enable DPMS
   xset -display $DISPLAY dpms 0 0 300     # turn off display after 5 minutes of idling

   if [ $? -eq 0 ]; then break
   else sleep 10
   fi
   
   timeout=`xset -q | grep Off | awk '{print $6}'`
done

i tried it on this laptop Dell Inspiron B130 running ubuntu 10.10 and it works.  I wonder what the real problem is since I don't see this issue on my newer Asus laptop.

This worked excellent for me. THanks!!

---

### Post by dwhitney67 on 2011-03-19
> **Mark124 said:**
> thanks for putting that script together.  However I believe you left out a timeout variable set in while which will create an infinite loop.
The intent was to have an repeating loop, with a 10-second period of sleep between iterations.  The loop would have exited when the xset -display command was successful.  Reseting the timeout variable, as you have done, was not necessary.

P.S.  Something like this would have been better:
```

...

if [ $timeout -eq 0 ]
then
        while [ true ]
        do
                ...
        done
fi

```

---

### Post by dalban on 2012-03-04
[Post deleted. My solution was ineffective.]

---

### Post by dalban on 2012-03-05
Switching to xfce4-power-manager is the easiest way to solve it. Here is how to make that happen:  [http://askubuntu.com/a/110006/44640](http://askubuntu.com/a/110006/44640)

Based on this bug report: [https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/447728](https://bugs.launchpad.net/ubuntu/+source/gnome-power-manager/+bug/447728)

---

