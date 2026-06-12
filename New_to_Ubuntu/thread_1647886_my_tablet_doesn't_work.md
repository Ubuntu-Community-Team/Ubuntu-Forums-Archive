---
title: "my tablet doesn't work"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by TerryDactyl on 2010-12-18
I've just installed Ubuntu 10.10, and my tablet isn't working.

It's a Genius Mousepen tablet,
I looked at the list of compatible tablets (it's not there) does anyone know how to get around this? Really don't feel like buying a new tablet.

---

### Post by Favux on 2010-12-18
Hi TerryDactyl,

Welcome to Ubuntu forums!

Was it working in a previous version of Ubuntu?  What is the the model and model #?

Let's see if the system is seeing it.  Enter in a terminal:
```
xinput --list
```
and post the output.

---

### Post by lmarmisa on 2010-12-18
Maybe these links could help you:

[https://help.ubuntu.com/community/TabletSetup](https://help.ubuntu.com/community/TabletSetup)

[https://help.ubuntu.com/community/TabletSetupWizardpen](https://help.ubuntu.com/community/TabletSetupWizardpen)

---

### Post by TerryDactyl on 2010-12-18
No, I don't think it was, at least it wasn't on the list I saw.

It's the Genius MousePen 8x6, I don't know what its number is.

---

### Post by Favux on 2010-12-18
Could you show me the output of the terminal command (copy & paste)?  Applications > Accesories > Terminal

---

### Post by TerryDactyl on 2010-12-19
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; UC-LOGIC Tablet WP8060U                 	id=8	[slave  pointer  (2)]
&#9116;   &#8627; HID 1241:1177                           	id=9	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Sleep Button                            	id=7	[slave  keyboard (3)]
    &#8627; AT Translated Set 2 keyboard            	id=10	[slave  keyboard (3)]

---

### Post by Favux on 2010-12-19
Hi TerryDactyl,

OK, that's all we need to get things going.  Now check in Synaptic Package Manager that the WizardPen driver is installed.  Search wizardpen.  It should be called something like xserver-xorg-input-wizardpen.  If not install it.  Reboot and see if the tablet works.

If it doesn't replace the 70-wizardpen.conf with:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```
Use:
```
gksudo gedit /usr/share/X11/xorg.conf.d/70-wizardpen.conf
```
to edit it.  Replace the entire contents with the above (make a backup copy) using copy & paste.  Reboot and see if the tablet works.

If it doesn't then change the driver to the one in DoctorMO's PPA, using the Maverick version:  [https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick](https://launchpad.net/~doctormo/+archive/xorg-wizardpen?field.series_filter=maverick)  Instructions on how to use the PPA on the site.  Reboot.  The tablet should work.

---

### Post by TerryDactyl on 2010-12-20
Nope, tablet's still a no-go.

---

### Post by Favux on 2010-12-20
Try MatchProduct instead of MatchVendor:
```
Section "InputClass"
    Identifier "WizardPen class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/event*"
    Driver "wizardpen"
EndSection

Section "InputClass"
    Identifier "WizardPen ignore mouse dev class"
    MatchIsTablet "on"
#    MatchVendor "UC-LOGIC|KYE Systems|Ace Cad"
    MatchProduct "UC-LOGIC"
    MatchDevicePath "/dev/input/mouse*"
    Option "Ignore" "yes"
EndSection
```

---

