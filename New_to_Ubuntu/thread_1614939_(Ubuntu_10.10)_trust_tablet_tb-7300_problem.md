---
title: "(Ubuntu 10.10) trust tablet tb-7300 problem"
date: 2010-11-06
forum: New to Ubuntu
---

### Post by kurotsuno on 2010-11-06
I'm having a simaler bug reported [https://bugs.launchpad.net/wizardpen/+bug/576610](https://bugs.launchpad.net/wizardpen/+bug/576610) there were the point seems to get stuck. 

I can't make heads or tales of the solution on there and also when looking up wizardpen setup page it lists I need to look at MatchVendor and that page no longer exists. 

How do I know my vendor and how can I get my tablet working properly

My tablet is a Trust TB-7300 wide screen design tablet. I've installed the wizardpen driver it's just this last little bit. 

I would appreciate any help on this as this tablet was a birthday present from my girlfriend :( and it would suck to tell her it doesn't work.

The reason I'm posting it here is because I'm still not comfortable with terminal commands and most of the time people explain things with the assumption you're on their level.

---

### Post by sandyd on 2010-11-06
> **kurotsuno said:**
> I'm having a simaler bug reported [https://bugs.launchpad.net/wizardpen/+bug/576610](https://bugs.launchpad.net/wizardpen/+bug/576610) there were the point seems to get stuck. 

I can't make heads or tales of the solution on there and also when looking up wizardpen setup page it lists I need to look at MatchVendor and that page no longer exists. 

How do I know my vendor and how can I get my tablet working properly

My tablet is a Trust TB-7300 wide screen design tablet. I've installed the wizardpen driver it's just this last little bit. 

I would appreciate any help on this as this tablet was a birthday present from my girlfriend :( and it would suck to tell her it doesn't work.

The reason I'm posting it here is because I'm still not comfortable with terminal commands and most of the time people explain things with the assumption you're on their level.
post output of
```

sudo udevadm monitor --property
cat /proc/bus/input/devices
cat /etc/X11/xorg.conf
cat /usr/lib/X11/xorg.conf.d/70-wizardpen.conf

```

and [https://bugs.launchpad.net/wizardpen/+bug/576610/comments/14](https://bugs.launchpad.net/wizardpen/+bug/576610/comments/14)

---

### Post by kurotsuno on 2010-11-06
tried the commands you listed and it just stays on 
```
monitor will print the received events for:
UDEV - the event which udev sends out after rule processing
KERNEL - the kernel uevent
```

also I've checked xorg.conf and there seems to be nothing listed in there it's being detected but not completely :/

---

### Post by Favux on 2010-11-06
Hi kurotsuno,

Please post the output of this command in a terminal (Applications > Accessories > Terminal):
```
xinput --list
```

---

### Post by kurotsuno on 2010-11-06
```
&#9121; Virtual core pointer                    	id=2	[master pointer  (3)]
&#9116;   &#8627; Virtual core XTEST pointer              	id=4	[slave  pointer  (2)]
&#9116;   &#8627; Logitech USB Optical Mouse              	id=8	[slave  pointer  (2)]
&#9116;   &#8627; WALTOP International Corp. Media Tablet 	id=12	[slave  pointer  (2)]
&#9123; Virtual core keyboard                   	id=3	[master keyboard (2)]
    &#8627; Virtual core XTEST keyboard             	id=5	[slave  keyboard (3)]
    &#8627; Power Button                            	id=6	[slave  keyboard (3)]
    &#8627; Power Button                            	id=7	[slave  keyboard (3)]
    &#8627; zc3xx                                   	id=11	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=9	[slave  keyboard (3)]
    &#8627;   USB Keyboard                          	id=10	[slave  keyboard (3)]

```

---

### Post by Favux on 2010-11-06
OK, what you have is a Waltop tablet rebranded as a Trust:
```
WALTOP International Corp. Media Tablet 	id=12	[slave  pointer  (2)
```
The Waltop can be set up on the WizardPen driver but that is no longer needed in Maverick.  The Waltop tablets are suppose to use the Wacom driver.  See the Waltop HOW TO:  [http://ubuntuforums.org/showthread.php?t=1595648](http://ubuntuforums.org/showthread.php?t=1595648)  Ask if you have any questions.  Post them on the Waltop HOW TO.

---

### Post by kurotsuno on 2010-11-06
that was surprisingly easy thanks :)  worked a treat

any idea how to config the sensitivity

---

### Post by Favux on 2010-11-06
Hi kurotsuno,

Good!  :)

Sure, use the .xsetwacom.sh xsetwacom script attached to the bottom of the post.

Please, please post any further questions on the HOW TO thread.  For some reason no one has and the thread needs a bump.

---

