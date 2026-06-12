---
title: "How Do I Run This Script (Mouse Switcher)"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by giddyup306 on 2010-10-30
My Asus g73's touch pad is wayyyy too sensitive, and messes up my typing all the time.  I found a some code to disable the pad when a USB mouse.  How do I run this script?  I thought that I could just hit the execute button or run it in a terminal...

```
#!/bin/bash
#
# Toggle touchpad on and off
#
# Author: Heath Thompson
# Email:  Heath.Thompson@gmail.com
#
# For startup wait for desktop to load first.
while true
do
    if ps -A | grep gnome-panel > /dev/null; 
    then
        echo 'X loaded'
        break; 
    else
        echo 'X not loaded, waiting...'
        sleep 5
    fi
done
#
# Check to see if appletouch is running
# if lsmod | grep appletouch > /dev/null; 
# then
#     echo " * Appletouch enabled"; 
# else
#     echo " * Appletouch either not working or not installed"
#     killall mouseSwitcher
# fi

while true
do
    # 'xinput list' will list all input devices x detects
    # I could reference my usb mouse by ID but I'm afraid that if I plug
    # another device in before my mouse, it might not have the same ID each
    # time.  So using the device name makes it relatively fail-safe.
    if xinput list 'Microsoft Microsoft? 2.4GHz Transceiver v5.0';
    then
        # Found my usb wireless mouse
        # Disable everything on the Touchpad and turn it off
        synclient TouchpadOff=1 MaxTapTime=0 ClickFinger1=0 ClickFinger2=0 ClickFinger3=0; 
        # Ends all syndaemon capturing which may have been used to monitor the touchpad/keyboard activity
        killall syndaemon
    else
        # My usb wireless mouse isn't present we need the touchpad
        # Reenable Touchpad and configure pad-clicks
        # RTCornerButton is the Right Top Corner on the touchpad
        #     The value 3 maps it as the right click button
        # RBCornerButton is the Right Bottom Corner on the touchpad
        #    The value 2 maps it as the middle click button
        synclient TouchpadOff=0 MaxTapTime=150 ClickFinger1=1 ClickFinger2=2 ClickFinger3=3 RTCornerButton=3 RBCornerButton=2;
        # Forces break of touchpad functions while typing if the touchpad is enabled.
        # Adds a 3 second interval following keyboard use which helps to prevent the
        # mouse from jumping while typing & resting hands on restpad or the touchpad
        syndaemon -i 3 -d;
    fi
    
    # wait 2 seconds and poll the mouse state again
    sleep 2
done

sleep 15
```Or do I need to add this to the fstab?

Thanks in advance. :guitar:

---

### Post by TeoBigusGeekus on 2010-10-30
Save it as, say, script.sh.
Make it executable
```
chmod +x script.sh
```
Then add it to your startup applications Administration>System(or Preferences)>Startup Applications
Add a new application and give
```
sh /path/to/your/script/script.sh
```
as its command.

---

### Post by giddyup306 on 2010-10-30
Thanks for the reply.  I'm getting the same error I got when I tried running it the other ways I mentioned. 

```
giddyup306@giddyup306-laptop:~$ chmod +x mouseSwitcher.sh
giddyup306@giddyup306-laptop:~$ sh /home/giddyup306/mouseSwitcher.sh
X loaded
unable to find device Microsoft Microsoft? 2.4GHz Transceiver v5.0
unable to find device Microsoft Microsoft? 2.4GHz Transceiver v5.0
unable to find device Microsoft Microsoft? 2.4GHz Transceiver v5.0
unable to find device Microsoft Microsoft? 2.4GHz Transceiver v5.0
unable to find device Microsoft Microsoft? 2.4GHz Transceiver v5.0
unable to find device Microsoft Microsoft? 2.4GHz Transceiver v5.0

```

---

### Post by giddyup306 on 2010-10-31
[http://ubuntuforums.org/showthread.php?t=1004591](http://ubuntuforums.org/showthread.php?t=1004591)

Here's the original thread.  If someone could help me out I'd appreciate it.

For now I'm trying this.  

```
synclient TouchpadOff=1

synclient TouchpadOff=0
```

---

### Post by giddyup306 on 2010-11-03
Anyone???

---

### Post by migs73 on 2010-11-03
This is what to do, it is in the comment tags in the script.

```
    # 'xinput list' will list all input devices x detects
    # I could reference my usb mouse by ID but I'm afraid that if I plug
    # another device in before my mouse, it might not have the same ID each
    # time.  So using the device name makes it relatively fail-safe.
 if xinput list 'Microsoft Microsoft? 2.4GHz Transceiver v5.0';


```


put
 ```
xinput list
``` 

into a terminal to determine the mouse hardware name. Then replace the text inside the apostrophes (currently the Microsoft Microsoft stuff) with the name of your hardware as provided by xinput list.

Hopefully that will be your only problem. :)

---

### Post by giddyup306 on 2010-11-03
> **migs73 said:**
> This is what to do, it is in the comment tags in the script.

```
    # 'xinput list' will list all input devices x detects
    # I could reference my usb mouse by ID but I'm afraid that if I plug
    # another device in before my mouse, it might not have the same ID each
    # time.  So using the device name makes it relatively fail-safe.
 if xinput list 'Microsoft Microsoft? 2.4GHz Transceiver v5.0';


```
put
 ```
xinput list
```into a terminal to determine the mouse hardware name. Then replace the text inside the apostrophes (currently the Microsoft Microsoft stuff) with the name of your hardware as provided by xinput list.

Hopefully that will be your only problem. :)

THANK YOU!  Now it works!!!  Unfortunately, this isn't my only problem.  I'm having problems installing my external wireless software.  I bought this 500 mw unit from ebay... came from Hong Kong...  The directions are extremely poor, and for some reason it wanted me to install Back Track Linux.  The disc they gave me was bad.  I have another CD which has NO instructions.  It's some software for it that I'd like to install, but the readme confuses me right from the very first step.

I don't really feel like chasing that down right now...

---

### Post by migs73 on 2010-11-03
Glad to have been of help :)

I would have thought the writer of the code would have tried to make it more obvious that, that line of code would need modified and how to do it. But then some people do tend to think every one has similar expertise to themselves. Not that I could have written that script!! I am still a noob, but with a good background (industrial) in fault finding via code.
Hope you get your wireless issues sorted out, if it came with a Linux OS I would think you should be able to get it going. (with some tweaking probably!!)

Mike

---

