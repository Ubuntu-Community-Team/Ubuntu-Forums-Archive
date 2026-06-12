---
title: "Bluetooth proximity check"
date: 2007-06-28
forum: Networking &amp; Wireless
---

### Post by benjaminwr on 2007-06-28
Hi, 

I thought you might like this script. It is a bluetooth proximity check. It checks weather your phone is near your computer and if it goes beyond the threshold it locks it. It unlocks it when the phone returns within the threshold. It is based on a script from gentoo wiki.

The only requirements for this script are:

Install sox from repositories if you want to play wav files as messages when your phone is in/out of range
chmod +s hcitool and l2ping so that you can run the script without use of sudo.
Pair your phone previously whith your computer.

You might have to tweake the threshold, since it depends a bit on the signal of your phone.

Here is the script. The only thing I would like to know if someone has any idea, would be the role of STARTX_PID in this script. I don't understand it's role

```
 STARTX_PID=$(pgrep startx)
```

```
#!/bin/bash
#set -o verbose sh -v
# Based on script from Steven on http://gentoo-wiki.com/Talk:TIP_Bluetooth_Proximity_Monitor

# These are the sections you'll need to edit

# You'll need to use the MAC address of your phone here
DEVICE="00:18:AF:44:61:34"

# How often to check the distance between phone and computer in seconds
CHECK_INTERVAL=4

# The RSSI threshold at which a phone is considered far or near
THRESHOLD=-3

# The command to run when your phone gets too far away
FAR_CMD='/usr/bin/gnome-screensaver-command --lock'

# The command to run when your phone is close again
NEAR_CMD='/usr/bin/gnome-screensaver-command --deactivate'

# The command to run, to play a sound message on events
VOX=/usr/bin/play

# The location of audio messages to be played
WAV_LOCK='/opt/proximity/locked.wav'
WAV_UNLOCK='/opt/proximity/unlocked.wav'

HCITOOL="/usr/bin/hcitool"
STARTX_PID=0
DEBUG="/tmp/btproximity.log"

function msg {
    echo "$1" #>> "$DEBUG"
}

function check_connection {
    connected=0;
    found=0
    for s in `$HCITOOL con`; do
        if [[ "$s" == "$DEVICE" ]]; then
            found=1;
        fi
    done
    
    if [[ $found == 1 ]]; then
        connected=1;
    else
       msg 'Attempting connection...'
        if [ -z "`$HCITOOL cc $DEVICE 2>&1`" ]; then
           msg 'Connected.'
            connected=1;
        else
                if [ -z "`l2ping -c 2 $DEVICE 2>&1`" ]; then
                        if [ -z "`$HCITOOL cc $DEVICE 2>&1`" ]; then
                            msg 'Connected.'
                            connected=1;
                        else
                        msg "ERROR: Could not connect to device $DEVICE."
                        connected=0;
                        fi
                fi
        fi
    fi
}

check_connection

while [[ $connected -eq 0 ]]; do
    check_connection
    sleep 3
done

name=`$HCITOOL name $DEVICE`
msg "Monitoring proximity of \"$name\" [$DEVICE]";

state="near"
while /bin/true; do

    check_connection

    if [[ $connected -eq 1 ]]; then
        rssi=$($HCITOOL rssi $DEVICE | sed -e 's/RSSI return value: //g')

        if [[ $rssi -le $THRESHOLD ]]; then
            if [[ "$state" == "near" ]]; then
                msg "*** Device \"$name\" [$DEVICE] has left proximity"
                state="far"
		$VOX $WAV_LOCK > /dev/null 2>&1                
		$FAR_CMD > /dev/null 2>&1
            fi
        else
            if [[ "$state" == "far" && $rssi -ge $[$THRESHOLD+2] ]]; then
                msg "*** Device \"$name\" [$DEVICE] is within proximity"
                state="near"
		$VOX $WAV_UNLOCK > /dev/null 2>&1               
		$NEAR_CMD > /dev/null 2>&1
                STARTX_PID=$(pgrep startx)
            fi
        fi
	msg "state = $state, RSSI = $rssi"
    else
        if [[ "$state" == "near" ]]; then
                msg "*** Device \"$name\" [$DEVICE] has been disconnected"
                state="far"
		$VOX $WAV_LOCK > /dev/null 2>&1
                $FAR_CMD > /dev/null 2>&1
        fi
    fi

    sleep $CHECK_INTERVAL
done
```

---

### Post by chaumurky on 2007-11-05
Great stuff. Just one question - my readings are erratic and i keep getting annoying locks occasionally so how do I modify the code so that:

* hcitool is run twice
* then the status is changed to 'far' if the sum of the two results is less than the doubled threshold.

I kinda know what i want to do but not sure how to go about it - not being a programmer.

---

### Post by christophski on 2007-11-15
i know this is a really old thread but i've only just found it. This sounds like it would be a really neat feature but i have installed it and it just constantly says 
" state = near, RSSI = 0"
No matter how far away I move, it still said it if i turned the bluetooth on my phone off. Anyone know how to fix this, or a better way to do it?

---

### Post by shingalated on 2007-11-18
Mine just says "Attempting Connection..." forever :(  I can see the phone on blueman just fine.

---

### Post by shingalated on 2007-11-18
I'm dumb...I never changed the mac address.

---

### Post by QwertyManiac on 2007-11-22
Get BlueProximity here: [http://blueproximity.sf.net/](http://blueproximity.sf.net/)

---

### Post by christophski on 2007-11-24
Ah Thankyou, this works fantastically!

---

