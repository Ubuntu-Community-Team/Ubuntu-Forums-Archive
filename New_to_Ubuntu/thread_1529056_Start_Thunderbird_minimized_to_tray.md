---
title: "Start Thunderbird minimized to tray"
date: 2010-07-11
forum: New to Ubuntu
---

### Post by Kajirou on 2010-07-11
How can I make Thunderbird start minimized to tray? And get it done on system startup? "ksystraycmd thunderbird %u" added to autorun in system settings doesn't work... Thanks for help!:)

---

### Post by wilee-nilee on 2010-07-11
I use alltray just install it then in system-prefrences-startup applications hit add name it and put in the command alltray thunderbird
[ATTACH]163116[/ATTACH]

---

### Post by Kajirou on 2010-07-11
It works! Thank you!:D

---

### Post by ububot on 2011-05-02
This is a bit of a hack, but it works great with the messaging menu. Much better than FireTray or any of those things, which don't really work in 11.04 anyhow.

1. Install wmctrl
2. Make a script called start_thunderbird_hidden.sh in ~/bin/ (you can of course change the name of the script and where you put it)
3. $ chmod +x ~/bin/start_thunderbird_hidden.sh
4. Make the contents of the script as follows:

#!/bin/bash

thunderbird &
while [[ $(wmctrl -l | grep Thunderbird) == "" ]]; do sleep 0.1; done
wmctrl -r Thunderbird -b add,skip_taskbar
wmctrl -k on

5. Go to Startup Applications -> add -> Command: ~/bin/start_thunderbird_hidden.sh

---

### Post by Pavluha88 on 2011-06-26
Looks like does not work on 11.04. Thunderbird does not appear at the tray.

Best solution I found is following:

1. Install "Fire tray" add-on in Thunderbird.

2. Create following script and put it in Startup:

```
 
#!/bin/bash
sleep 7
thunderbird &
while [ true ]
do
   sleep 5
   status=`wmctrl -l | grep Thunderbird`
   if [ "$status" != "" ] ; then
      break
   fi
done
wmctrl -c "Mozilla Thunderbird"

```Reference: [http://ubuntuforums.org/showthread.php?t=1603810](http://ubuntuforums.org/showthread.php?t=1603810)

---

### Post by silenzioKLZE on 2011-12-28
For futher reference, and for people like me who don't find fire tray easily.

The above script is correct @ububot, but it does not answer the original poster question.

Just comment/erase [B]

wmctrl -r Thunderbird -b add,skip_taskbar[/B]

 and add this: 

**wmctrl -r Thunderbird -b add,hidden**



Even so, thunderbard will pop up for 0.2 seconds, but will hide.

Enjoy.

---

### Post by Pavluha88 on 2011-12-28
> **silenzioKLZE said:**
> For futher reference, and for people like me who don't find fire tray easily.

The above script is correct @ububot, but it does not answer the original poster question.

Just comment/erase [B]

wmctrl -r Thunderbird -b add,skip_taskbar[/B]

 and add this: 

**wmctrl -r Thunderbird -b add,hidden**



Even so, thunderbard will pop up for 0.2 seconds, but will hide.

Enjoy.

Could you please post full code of the script with your adds? Somewhy it stopped to work when I installed Ubuntu 11.10. Thanks.

---

### Post by wolf_rt on 2012-01-18
Got this to work for me in 11.10

1. Install wmctrl
2. Make a script called start_thunderbird_hidden.sh in ~/bin/ (you can of course change the name of the script and where you put it)
3. $ chmod +x ~/bin/start_thunderbird_hidden.sh
4. Make the contents of the script as follows:

ububot's script, with silenzioKLZE's modification:
```
#!/bin/bash

thunderbird &
while [[ $(wmctrl -l | grep Thunderbird) == "" ]]; do sleep 0.1; done
wmctrl -r Thunderbird -b add,hidden
wmctrl -k on

```**Had to include the full path rather than using ~/ to get it to work**
5. Go to Startup Applications -> add -> Command: /home/<user>/bin/start_thunderbird_hidden.sh

So all good... 
**Is there a way to get rid of TB from the 'Icons on the left of the screen'** while it is running (all the time) (whatever that is called (only new to linux))
The 'minimize to tray' add-on, doesn't appear to do anything?
nor does the 'minimize on start and close' add-on for that matter.

---

### Post by jm1garcia on 2012-02-23
Got rid of the Icon on the left of the screen with the 'minimize to tray' on 11.10

1. Install wmctrl
2. Open Thunderbird and go to Add-ons Manager and search the Add-on "MinimizeToTray revived (MinTrayR) 1.0" then Add to Thunderbird.
3. Restart Thunderbird
4. Go to Add-ons Manager > Extentions > MinimizeToTray revived > Preferences
5. Uncheck everything then check "Instead of closing".
6. Create a new script or reuse "start_thunderbird_hidden.sh" with this script:

#!/bin/bash
sleep 15
thunderbird &
sleep 3
wmctrl -c "Mozilla Thunderbird"

7. Open "Startup Applications" click Add, then on the command Browse for the script.
8. Reboot and test if it works

Note: To close Thunderbird Ctrl+Q, Alt+F4 Minimizes it to Tray.

Hope this helps.

---

### Post by ShaneOSDN on 2012-04-29
Works on Ubuntu 12.04 flawlessly thank you.

---

### Post by Selo on 2012-12-11
If you use firetoTray and this [Minimize On Start and Close]("https://addons.mozilla.org/en-US/thunderbird/addon/minimize-on-start-and-close/") together Thunderbird will start on system tray automatically. Make sure *Minimizing window hides to tray* is **checked** under the FireTray add-on and *Minimize on close* is **UNCHECKED** under the Minimize On Start and Close add-on.

---

### Post by pqwoerituytrueiwoq on 2012-12-11
i am using [Minimize On Start and Close]("https://addons.mozilla.org/en-US/thunderbird/addon/minimize-on-start-and-close/") and [MinimizeToTray revived](https://addons.mozilla.org/en-us/thunderbird/addon/minimizetotray-revived/)

---

