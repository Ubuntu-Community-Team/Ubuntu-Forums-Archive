---
title: "Mute and Lock Screen with one command"
date: 2009-12-26
forum: New to Ubuntu
---

### Post by abhiroopb on 2009-12-26
I usually press CTRL+ALT+L to lock the screen. However, I would like to know if I could set it up so that when I lock the screen my speakers also get muted. I sometimes forget to mute the speakers when I lock my screen and step away from my computer and if someone calls me on skype the ringtone is really loud and disturbs others.

---

### Post by Vermind on 2009-12-26
For this, you need to create a script with the two commands in it.
```
gnome-screensaver-command -l
``` locks the screen.
I am not sure about the mute command. If you have not changed the karmic default pulseaudio install, you can get a list of sound sinks with
```
list-sink-inputs
``` and mute them with ```
set-sink-input-mute
```. I am more familiar with alsa though. For alsa, the mute command is ```
amixer set Master mute
```.

To create the script, you can for example ```
gedit mute-and-lock.sh

``` and then insert this text into the file:
```
#!/bin/bash
# for pulse:
set-sink-input-mute xx 1 # xx is what you get from list-sink-inputs. Should be master or something. Not sure about this
# Lock the screen:
gnome-screensaver-command -l
```

Then save and quit gedit. After this, right-click the file you created and choose properties, and on the permissions tab "allow executing as program". Now you can try the script, by double clicking on it and choosing run or run in terminal. If it locks and mutes, congrats!

Next we make a shortcut for it. In the System menu, Preferences, there is Keyboard Shortcuts. Click the Add button there. The name can be for example "mute and lock" and the command should be the file you created; you can drag it to the command text box or write ```
/home/youruser/mute-and-lock.sh
``` into it. Press ok, and find the new command in the shortcut list. It will be in the last Custom Shortcuts category. Click the right side to assign a key combo for it. Then press whatever combo you want to assign, for example ctrl-alt-L.

---

### Post by abhiroopb on 2009-12-26
Thanks your solution was PERFECT!

Incidentally, in Karmic (with default sound settings) the command to mute is:
```

amixer set Master mute
```

So, my script was:
```

#!/bin/bash
amixer set Master mute
gnome-screensaver-command -l

```

Thanks again!

---

### Post by CaptainMark on 2009-12-26
what about when you unlock, this wont unmute will it. i guess thats not so bad,

---

### Post by abhiroopb on 2009-12-26
The problem with unmuting is that when you unlock you unlock with ANY button. Therefore, it is hard to bind a particular key to unmute.

---

### Post by Vermind on 2009-12-26
For automatic unmute, have the script changed to this:

```
#!/bin/bash
amixer set Master mute
gnome-screensaver-command -l
haslock=;
while true; do
    sleep 2;
    locked=$( gnome-screensaver-command -q | grep " active" );
    if [ -n "$haslock" ]; then
        # lock has happened before. Check unlock and break if unlocked
        if [ -z "$locked" ]; then break; fi
    fi
    if [ -n "$locked" ]; then
        haslock="true";
    fi
done
# we only exit the loop after an unlock, so
# now unmute:
amixer set Master unmute
```


Run this in the console first to see if it works for you. I just tested it on this machine, looks good.
Cheers,

---

### Post by abhiroopb on 2009-12-26
That's really cool! Thanks a lot.

---

### Post by Vermind on 2009-12-26
Hi,
nobody likes sharp edges, so I thought up a smooth fade of volume into the mute and lock script. It now remembers your pre-lock volume and fades it down to zero prior to muting. When unlocking, it fades the volume up again. I also made it modular and less platform-dependent by providing some settings for choosing the sound card and channel.

```
#!/bin/bash
########################################
# Settings                             #
########################################

card=0;           # Sound card. 0 == default, first card.
channel="Master"; # Which volume to control. Examples: Master, PCM, Headphone
step=3;           # Fade step: The volume increment/decrement amount
interval=0.2      # Seconds between increments/decrements when fading

########################################
# Functions                            #
########################################

# fades volume up or down
function fade {
    # get current volume
    vol=$( ${m} sget ${channel} | awk '$0 ~ "%" { print $3 }' )
    if [ "$1" == "down" ]; then
        # fade down:
        while [ ${vol} -gt 0 ]; do
            sleep ${interval}
            ${m} set ${channel} ${step}-
            let vol-=${step}
        done
        ${m} set ${channel} mute
   else
       # first unmute, then fade up
        ${m} set ${channel} unmute
         while [ ${orig} -gt ${vol} ]; do
            sleep ${interval}
            let vol+=${step}
            if [ ${vol} -gt ${orig} ]; then vol=${orig}; fi
            ${m} set ${channel} ${step}+
        done
        ${m} set ${channel} ${orig}
   fi
}

# Returns when the screen has been locked and unlocked
function unlockcheck {
    haslock=
    while true; do
        sleep 2
        locked=$( gnome-screensaver-command -q | grep " active" )
        if [ -n "${haslock}" ]; then
            # lock has happened before. Check unlock and break if unlocked
            if [ -z "${locked}" ]; then break; fi
        fi
        if [ -n "${locked}" ]; then
            haslock="true"
        fi
    done
}

########################################
# Startup                              #
########################################

# short mixer command with card
m="amixer -c ${card}";
# record original volume value
orig=$( ${m} sget ${channel} | awk '$0 ~ "%" { print $3 }' )

########################################
# Procedure                            #
########################################

gnome-screensaver-command -l # lock screen
fade down # fade volume down and mute
unlockcheck # wait for unlock
fade up # fade volume up and unmute
# That's it!

```

Ok, I better do some work...

---

### Post by abhiroopb on 2009-12-26
since we're tweaking like mad...

The initial mute and lock is fine. However, when it comes out of the lock screen it takes a second for it to unmute. Can it unmute either at the same time as it unlocks or even before it unlocks. Presumably when you are there to unlock it you want it to mute. The one second wait makes everything feel slow.

Thanks again!

---

### Post by abhiroopb on 2009-12-27
> **Vermind said:**
> Hi,
nobody likes sharp edges, so I thought up a smooth fade of volume into the mute and lock script. It now remembers your pre-lock volume and fades it down to zero prior to muting. When unlocking, it fades the volume up again. I also made it modular and less platform-dependent by providing some settings for choosing the sound card and channel.

```
#!/bin/bash
########################################
# Settings                             #
########################################

card=0;           # Sound card. 0 == default, first card.
channel="Master"; # Which volume to control. Examples: Master, PCM, Headphone
step=3;           # Fade step: The volume increment/decrement amount
interval=0.2      # Seconds between increments/decrements when fading

########################################
# Functions                            #
########################################

# fades volume up or down
function fade {
    # get current volume
    vol=$( ${m} sget ${channel} | awk '$0 ~ "%" { print $3 }' )
    if [ "$1" == "down" ]; then
        # fade down:
        while [ ${vol} -gt 0 ]; do
            sleep ${interval}
            ${m} set ${channel} ${step}-
            let vol-=${step}
        done
        ${m} set ${channel} mute
   else
       # first unmute, then fade up
        ${m} set ${channel} unmute
         while [ ${orig} -gt ${vol} ]; do
            sleep ${interval}
            let vol+=${step}
            if [ ${vol} -gt ${orig} ]; then vol=${orig}; fi
            ${m} set ${channel} ${step}+
        done
        ${m} set ${channel} ${orig}
   fi
}

# Returns when the screen has been locked and unlocked
function unlockcheck {
    haslock=
    while true; do
        sleep 2
        locked=$( gnome-screensaver-command -q | grep " active" )
        if [ -n "${haslock}" ]; then
            # lock has happened before. Check unlock and break if unlocked
            if [ -z "${locked}" ]; then break; fi
        fi
        if [ -n "${locked}" ]; then
            haslock="true"
        fi
    done
}

########################################
# Startup                              #
########################################

# short mixer command with card
m="amixer -c ${card}";
# record original volume value
orig=$( ${m} sget ${channel} | awk '$0 ~ "%" { print $3 }' )

########################################
# Procedure                            #
########################################

gnome-screensaver-command -l # lock screen
fade down # fade volume down and mute
unlockcheck # wait for unlock
fade up # fade volume up and unmute
# That's it!

```

Ok, I better do some work...

Running this new script in the terminal gives me the following:

```

./mute-and-lock.sh: line 21: [: too many arguments
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 24 [80%] [-10.50dB] [off]
  Front Right: Playback 24 [80%] [-10.50dB] [off]
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 24 [80%] [-10.50dB] [on]
  Front Right: Playback 24 [80%] [-10.50dB] [on]
./mute-and-lock.sh: line 30: [: too many arguments
amixer: Invalid command!

```

Seems to be a problem somewhere!

Also (and I think this may be related to the error) after it unlocks the volume unmutes after about 1-2 seconds.

The old script gives the following output:
```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 24 [80%] [-10.50dB] [off]
  Front Right: Playback 24 [80%] [-10.50dB] [off]
Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 24 [80%] [-10.50dB] [on]
  Front Right: Playback 24 [80%] [-10.50dB] [on]

```

But, even using this script there is a 1-2 second delay after unlock for the volume to unmute.

---

### Post by Vermind on 2009-12-27
Hello
here is a version that unmutes faster, at the cost of more CPU when locked. Introduced lockdelay, the delay between checks for unlocking. Smaller values unmute faster after unlock. The CPU cost for 0.5 secs between checks is modest, but for very small values of lockdelay may become considerable.

Someone said that line 21 was buggy; I tested this version in console and normally, and it should work. If you get bugs, make sure you copy the code verbatim and your editor does not introduce extra line breaks.

```
#!/bin/bash
########################################
# Settings                             #
########################################

card=0;           # Sound card. 0 == default, first card.
channel="Master"; # Which volume to control. Examples: Master, PCM, Headphone
step=3;           # Fade step: The volume increment/decrement amount
interval=0.2      # Seconds between increments/decrements when fading
lockdelay=0.5     # How long wait between unlock checks. Smaller values unmute faster
# but use more CPU used when locked.

########################################
# Functions                            #
########################################

# fades volume up or down
function fade {
    # get current volume
    vol=$( ${m} sget ${channel} | awk '$0 ~ "%" { print $3 }' )
    if [ "$1" == "down" ]; then
        # fade down:
        while [ ${vol} -gt 0 ]; do
            sleep ${interval}
            ${m} set ${channel} ${step}- >/dev/null
            let vol-=${step}
        done
        ${m} set ${channel} mute >/dev/null
   else
       # first unmute, then fade up
        ${m} set ${channel} unmute >/dev/null
         while [ ${orig} -gt ${vol} ]; do
            sleep ${interval}
            let vol+=${step}
            if [ ${vol} -gt ${orig} ]; then vol=${orig}; fi
            ${m} set ${channel} ${step}+ >/dev/null
        done
        ${m} set ${channel} ${orig} >/dev/null
   fi
}

# Returns when the screen has been locked and unlocked
function unlockcheck {
    haslock=
    while true; do
        sleep ${lockdelay}
        locked=$( gnome-screensaver-command -q | grep " active" )
        if [ -n "${haslock}" ]; then
            # lock has happened before. Check unlock and break if unlocked
            if [ -z "${locked}" ]; then break; fi
        fi
        if [ -n "${locked}" ]; then
            haslock="true"
        fi
    done
}

########################################
# Startup                              #
########################################

# short mixer command with card
m="amixer -c ${card}";
# record original volume value
orig=$( ${m} sget ${channel} | awk '$0 ~ "%" { print $3 }' )

########################################
# Procedure                            #
########################################

gnome-screensaver-command -l # lock screen
fade down # fade volume down and mute
unlockcheck # wait for unlock
fade up # fade volume up and unmute
# That's it!

```

---

### Post by abhiroopb on 2009-12-27
Thanks for the update. I didn't realise it would cost CPU cycles. I usually keep the computer locked at night but with high CPU cost the noise would become a problem.

---

### Post by abhiroopb on 2009-12-27
I am still getting errors while running it:

```

./mute-and-lock.sh: line 23: [: too many arguments
./mute-and-lock.sh: line 32: [: too many arguments
amixer: Invalid command!

```

---

### Post by Vermind on 2009-12-27
please do this:
```
amixer > amixer-controls.txt
```
and post the resulting file. I will check if your amixer has different controls and you need to change some variables.

---

### Post by abhiroopb on 2009-12-27
Thanks for the help

output:
```

Simple mixer control 'Master',0
  Capabilities: pvolume pswitch pswitch-joined
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 25 [83%] [-9.00dB] [on]
  Front Right: Playback 25 [83%] [-9.00dB] [on]
Simple mixer control 'PCM',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 255
  Mono:
  Front Left: Playback 254 [100%] [0.20dB] [on]
  Front Right: Playback 254 [100%] [0.20dB] [on]
Simple mixer control 'Mic',0
  Capabilities: pvolume pswitch
  Playback channels: Front Left - Front Right
  Limits: Playback 0 - 30
  Mono:
  Front Left: Playback 0 [0%] [-34.50dB] [off]
  Front Right: Playback 0 [0%] [-34.50dB] [off]
Simple mixer control 'Mic Boost',0
  Capabilities: volume
  Playback channels: Front Left - Front Right
  Capture channels: Front Left - Front Right
  Limits: 0 - 3
  Front Left: 0 [0%]
  Front Right: 0 [0%]
Simple mixer control 'IEC958',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [off]
Simple mixer control 'IEC958 Default PCM',0
  Capabilities: pswitch pswitch-joined
  Playback channels: Mono
  Mono: Playback [on]
Simple mixer control 'Capture',0
  Capabilities: cvolume cswitch
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 14
  Front Left: Capture 0 [0%] [0.00dB] [on]
  Front Right: Capture 0 [0%] [0.00dB] [on]
Simple mixer control 'Digital',0
  Capabilities: cvolume
  Capture channels: Front Left - Front Right
  Limits: Capture 0 - 120
  Front Left: Capture 60 [50%] [0.00dB]
  Front Right: Capture 60 [50%] [0.00dB]

```

---

### Post by Vermind on 2009-12-27
Hello, Fixed the script for people with stereo sound cards. It now detects the volume properly.

```
#!/bin/bash
########################################
# Settings                             #
########################################

card=0;           # Sound card. 0 == default, first card.
channel="Master"; # Which volume to control. Examples: Master, PCM, Headphone
step=3;           # Fade step: The volume increment/decrement amount
interval=0.2      # Seconds between increments/decrements when fading
lockdelay=0.5     # How long wait between unlock checks. Smaller values unmute faster
# but use more CPU used when locked.

########################################
# Functions                            #
########################################

# get current volume
function getvol {
    vol=$( ${m} sget ${channel} | awk '
$0 ~ "%" { 
    if ($4 ~ "%") {
        print $3;
    } else if ($5 ~ "%") { 
    print $4;
    exit 0;
    }
}' )
}

# fades volume up or down
function fade {
    # get current volume
    getvol
    if [ "$1" == "down" ]; then
        # fade down:
        while [ ${vol} -gt 0 ]; do
            sleep ${interval}
            ${m} set ${channel} ${step}- >/dev/null
            let vol-=${step}
        done
        ${m} set ${channel} mute >/dev/null
   else
       # first unmute, then fade up
        ${m} set ${channel} unmute >/dev/null
         while [ ${orig} -gt ${vol} ]; do
            sleep ${interval}
            let vol+=${step}
            if [ ${vol} -gt ${orig} ]; then vol=${orig}; fi
            ${m} set ${channel} ${step}+ >/dev/null
        done
        ${m} set ${channel} ${orig} >/dev/null
   fi
}

# Returns when the screen has been locked and unlocked
function unlockcheck {
    haslock=
    while true; do
        sleep ${lockdelay}
        locked=$( gnome-screensaver-command -q | grep " active" )
        if [ -n "${haslock}" ]; then
            # lock has happened before. Check unlock and break if unlocked
            if [ -z "${locked}" ]; then break; fi
        fi
        if [ -n "${locked}" ]; then
            haslock="true"
        fi
    done
}

########################################
# Startup                              #
########################################

# short mixer command with card
m="amixer -c ${card}"
# record original volume value
getvol
orig=$vol

########################################
# Procedure                            #
########################################

gnome-screensaver-command -l # lock screen
fade down # fade volume down and mute
unlockcheck # wait for unlock
fade up # fade volume up and unmute
# That's it!
```

---

### Post by abhiroopb on 2009-12-27
Works perfectly...no errors!

---

### Post by abhiroopb on 2009-12-30
I was wondering if there was a way to turn of my monitor when the screen is locked?

The thread [here]("http://brainstorm.ubuntu.com/idea/10585/") seems to suggest a way, but where should I put it in the script?

Thanks

---

### Post by Vermind on 2009-12-30
Hello,
here is a new version that turns off the screen.
The screen is turned off after muting sound, so that it happens around the time that the gnome-screensaver has smoothly turned down the brightness. Also, during the lock period, accidental keystrokes or mouse moves will not leave your screen on until relock, but rather DPMS is used to turn off the screen with 10 seconds of inactivity. The script also restores your pre-lock dpms settings after it is done. Tweak the settings to your liking. 

Just in case something goes wrong, say xset 0 0 0 in a terminal to put dpms on infinite again. The first number is standby, then suspend, then off.


```
#!/bin/bash
########################################
# mute-and-lock.sh                     #
# Mutes sound and locks the screen     #
# using amixer and gnome-screensaver.  #
# Version 1.0                          #
# -Added DPMS screen turnoff           #
#                                      #
# written by Vermind                   #
########################################

########################################
# Settings                             #
########################################

card=0;           # Sound card. 0 == default, first card.
channel="Master"; # Which volume to control. Examples: Master, PCM, Headphone
step=3;           # Fade step: The volume increment/decrement amount
interval=0.2      # Seconds between increments/decrements when fading
lockdelay=0.5     # How long wait between unlock checks. Smaller values unmute faster
# but use more CPU when locked.
# DPMS settings to use when locked, 0==infinity:
standby=0 # how many seconds of inactivity to wait before screen standby
suspend=0 # before screen suspend
off=10 # before turning the screen off


########################################
# Functions                            #
########################################

# get current volume
function getvol {
    vol=$( ${m} sget ${channel} | awk '
$0 ~ "%" { 
    if ($4 ~ "%") {
        print $3;
    } else if ($5 ~ "%") { 
    print $4;
    exit 0;
    }
}' )
}

# fades volume up or down
function fade {
    # get current volume
    getvol
    if [ "$1" == "down" ]; then
        # fade down:
        while [ ${vol} -gt 0 ]; do
            sleep ${interval}
            ${m} set ${channel} ${step}- >/dev/null
            let vol-=${step}
        done
        ${m} set ${channel} mute >/dev/null
   else
       # first unmute, then fade up
        ${m} set ${channel} unmute >/dev/null
         while [ ${orig} -gt ${vol} ]; do
            sleep ${interval}
            let vol+=${step}
            if [ ${vol} -gt ${orig} ]; then vol=${orig}; fi
            ${m} set ${channel} ${step}+ >/dev/null
        done
        ${m} set ${channel} ${orig} >/dev/null
   fi
}

# Returns when the screen has been locked and unlocked
function unlockcheck {
    screenlockacc=0;
    haslock=
    while true; do
        sleep ${lockdelay}
        locked=$( gnome-screensaver-command -q | grep " active" )
        if [ -n "${haslock}" ]; then
            # lock has happened before. Check unlock and break if unlocked
            if [ -z "${locked}" ]; then break; fi
        fi
        if [ -n "${locked}" ]; then
            haslock="true"
        fi
    done
}

########################################
# Startup                              #
########################################

# short mixer command with card
m="amixer -c ${card}"
# record original volume value
getvol
orig=$vol

# record original DPMS settings.
dpms=$( xset dpms q | awk '$0 ~ "Suspend" && $0 ~ "Standby" && $0 ~ "Off" { print $2, $4, $6; }' )

########################################
# Procedure                            #
########################################

# set specified DPMS settings:
xset dpms ${standby} ${suspend} ${off}
gnome-screensaver-command -l # lock screen
fade down # fade volume down and mute
xset dpms force off # turn off the screen (directly after lock results in too quick turnoff)
unlockcheck # wait for unlock
fade up # fade volume up and unmute
xset dpms ${dpms} # restore dpms settings
# That's it!

```

---

### Post by abhiroopb on 2009-12-30
Works great. But, if I move the mouse or keyboard (while in lock mode) the panel shows up where I can put in my password to unlock. Then if I don't put my password in the computer locks again but the screen does not go to sleep.

Does that make sense? Slight hiccup

---

### Post by Vermind on 2009-12-31
You should test if your dpms works in normal mode at all. Perhaps it's disabled or something? Type ```
xset dpms q
``` into a terminal and check what's written after DPMS (Energy Star):
Also, try to enable dpms screen turnoff without my script, using
```
xset dpms 0 0 10
``` Then wait for 10 seconds without typing or moving the mouse. The screen should turn off. If not, maybe dpms is not working for you? The script can be modified to turn off the screen anyway without dpms in that case.

---

### Post by abhiroopb on 2009-12-31
> **Vermind said:**
> You should test if your dpms works in normal mode at all. Perhaps it's disabled or something? Type ```
xset dpms q
``` into a terminal and check what's written after DPMS (Energy Star):
Also, try to enable dpms screen turnoff without my script, using
```
xset dpms 0 0 10
``` Then wait for 10 seconds without typing or moving the mouse. The screen should turn off. If not, maybe dpms is not working for you? The script can be modified to turn off the screen anyway without dpms in that case.

Happy New Year! - It's already Jan 1 2010 5:20 am here!

Anyway back to the matter at hand.

```
xset dpms q
```
I get the following output:
```
$ xset dpms q
Keyboard Control:
  auto repeat:  on    key click percent:  0    LED mask:  00000002
  auto repeat delay:  500    repeat rate:  30
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

So, I guess there is no problem with that

```
xset dpms 0 0 10
```

This seems to turn my monitor off every 10 seconds. So, I will not move my mouse and EVERY 10 seconds my monitor turns off.

I am currently having two problems using the script:

1. The monitor turns off when I lock the screen but after 10 seconds the monitor turns back on.

2. If I move the mouse or hit a key on the keyboard the unlock box shows up and if I don't type anything the monitor still stays on.

Any thoughts?

Thanks

---

### Post by Vermind on 2009-12-31
Change this in the script:
```
# set specified DPMS settings:
xset dpms ${standby} ${suspend} ${off}
```
to 
```
# set specified DPMS settings:
echo "xset dpms ${standby} ${suspend} ${off}"
xset dpms ${standby} ${suspend} ${off}
```
then run it in the console and see what it is setting for dpms.

---

### Post by abhiroopb on 2010-01-01
> **Vermind said:**
> Change this in the script:
```
# set specified DPMS settings:
xset dpms ${standby} ${suspend} ${off}
```
to 
```
# set specified DPMS settings:
echo "xset dpms ${standby} ${suspend} ${off}"
xset dpms ${standby} ${suspend} ${off}
```
then run it in the console and see what it is setting for dpms.

Ran it in the console and here is the output:

```

./mute-and-lock.sh 
xset dpms 0 0 10

```

The screen switches off, but, after about 10s the screen turns back on and stays on.

---

### Post by Vermind on 2010-01-01
Ok, it seems that gnome-screensaver really really wants to show you a pretty blanked screen or some other screensaver. It is turning the screen back on in order to do that. In my opinion, I should really be allowed to choose just locking and not touching the screen after that. Anyway, I was able to hack around it using gnome-screensaver-command -i, which prevents the screensaver from activating. It also blocks, so I have to run it in a separate process. When I run it after locking the screen, the screen will stay locked and dpms will correctly keep the screen turned off like intended, and the 10-second turnoff also functions properly.

```
#!/bin/bash
########################################
# mute-and-lock.sh                     #
# Mutes sound and locks the screen     #
# using amixer and gnome-screensaver.  #
# Version 1.01                         #
# -Added DPMS screen turnoff           #
# -Prevent gnome-screensaver from      #
#  turning the screen back on          #
#                                      #
# written by Vermind                   #
########################################

########################################
# Settings                             #
########################################

card=0;           # Sound card. 0 == default, first card.
channel="Master"; # Which volume to control. Examples: Master, PCM, Headphone
step=3;           # Fade step: The volume increment/decrement amount
interval=0.2      # Seconds between increments/decrements when fading
lockdelay=0.5     # How long wait between unlock checks. Smaller values unmute faster
# but use more CPU when locked.
# DPMS settings to use when locked, 0==infinity:
standby=0 # how many seconds of inactivity to wait before screen standby
suspend=0 # before screen suspend
off=10 # before turning the screen off


########################################
# Functions                            #
########################################

# get current volume
function getvol {
    vol=$( ${m} sget ${channel} | awk '
$0 ~ "%" { 
    if ($4 ~ "%") {
        print $3;
    } else if ($5 ~ "%") { 
    print $4;
    exit 0;
    }
}' )
}

# fades volume up or down
function fade {
    # get current volume
    getvol
    if [ "$1" == "down" ]; then
        # fade down:
        while [ ${vol} -gt 0 ]; do
            sleep ${interval}
            ${m} set ${channel} ${step}- >/dev/null
            let vol-=${step}
        done
        ${m} set ${channel} mute >/dev/null
   else
       # first unmute, then fade up
        ${m} set ${channel} unmute >/dev/null
         while [ ${orig} -gt ${vol} ]; do
            sleep ${interval}
            let vol+=${step}
            if [ ${vol} -gt ${orig} ]; then vol=${orig}; fi
            ${m} set ${channel} ${step}+ >/dev/null
        done
        ${m} set ${channel} ${orig} >/dev/null
   fi
}

# Returns when the screen has been locked and unlocked
function unlockcheck {
    screenlockacc=0;
    haslock=
    while true; do
        sleep ${lockdelay}
        locked=$( gnome-screensaver-command -q | grep " active" )
        if [ -n "${haslock}" ]; then
            # lock has happened before. Check unlock and break if unlocked
            if [ -z "${locked}" ]; then break; fi
        fi
        if [ -n "${locked}" ]; then
            haslock="true"
        fi
    done
}

########################################
# Startup                              #
########################################

# short mixer command with card
m="amixer -c ${card}"
# record original volume value
getvol
orig=$vol

# record original DPMS settings.
dpms=$( xset dpms q | awk '$0 ~ "Suspend" && $0 ~ "Standby" && $0 ~ "Off" { print $2, $4, $6; }' )

########################################
# Procedure                            #
########################################

# set specified DPMS settings:
xset dpms ${standby} ${suspend} ${off}
gnome-screensaver-command -l # lock screen
fade down # fade volume down and mute
xset dpms force off # turn off the screen (directly after lock results in too quick turnoff)
gnome-screensaver-command -i -a "mute-and-lock" & # Stop screensaver from waking up the screen
unlockcheck # wait for unlock
# stop inhibiting screensaver
kill $( ps -ef | awk '$0 ~ "gnome-screensaver-command -i" && $NF == "mute-and-lock" { print $2; }' )
fade up # fade volume up and unmute
xset dpms ${dpms} # restore dpms settings
# That's it!

```

Cheers,

---

### Post by abhiroopb on 2010-01-01
Thanks the update fixed the problem.

The only thing is when I move my mouse and the box shows up to unlock BUT I don't unlock and click cancel the monitor does not switch of and the screensaver is shown.

Any thoughts on that?

---

### Post by Vermind on 2010-01-02
For me, the screensaver also shows in that case; also if I press esc on the unlock screen. However, in several seconds, the screen goes off. If it doesn't for you, I can make this script force it off every 10 seconds with the initial command.

---

### Post by Vermind on 2010-01-02
Hi,
Added two things:
[LIST=1]
[*]It is now possible to force the screen off between $off intervals. Uncomment forceoff in Settings to do this.
[*]The script now ensures a smooth dimdown before turning the screen off by giving the lock + volume fade at least 3 seconds of time.
[/LIST]
```
#!/bin/bash
########################################
# mute-and-lock.sh                     #
# Mutes sound and locks the screen     #
# using amixer and gnome-screensaver.  #
# Version 1.02                         #
# -Added DPMS screen turnoff           #
# -Prevent gnome-screensaver from      #
#  turning the screen back on          #
# -Workaround for DPMS timing          #
# -Give screen time to dim down        #
#                                      #
# written by Vermind                   #
########################################

########################################
# Settings                             #
########################################

card=0;           # Sound card. 0 == default, first card.
channel="Master"; # Which volume to control. Examples: Master, PCM, Headphone
step=3;           # Fade step: The volume increment/decrement amount
interval=0.2      # Seconds between increments/decrements when fading
lockdelay=0.5     # How long wait between unlock checks. Smaller values unmute faster
# but use more CPU when locked.
# DPMS settings to use when locked, 0==infinity:
standby=0 # how many seconds of inactivity to wait before screen standby
suspend=0 # before screen suspend
off=10 # before turning the screen off
# Workarounds:
#forceoff=1  # uncomment to have the screen forced off between the dpms off intervals.



########################################
# Functions                            #
########################################

# get current volume
function getvol {
    vol=$( ${m} sget ${channel} | awk '
$0 ~ "%" { 
    if ($4 ~ "%") {
        print $3;
    } else if ($5 ~ "%") { 
    print $4;
    exit 0;
    }
}' )
}

# fades volume up or down
function fade {
    # get current volume
    getvol
    if [ "$1" == "down" ]; then
        # fade down:
        while [ ${vol} -gt 0 ]; do
            sleep ${interval}
            ${m} set ${channel} ${step}- >/dev/null
            let vol-=${step}
        done
        ${m} set ${channel} mute >/dev/null
   else
       # first unmute, then fade up
        ${m} set ${channel} unmute >/dev/null
         while [ ${orig} -gt ${vol} ]; do
            sleep ${interval}
            let vol+=${step}
            if [ ${vol} -gt ${orig} ]; then vol=${orig}; fi
            ${m} set ${channel} ${step}+ >/dev/null
        done
        ${m} set ${channel} ${orig} >/dev/null
   fi
}

function forceoffcheck {
    foacc=$( echo "${lockdelay} +  ${foacc}" | bc ) # lockdelay elapsed
    elapsed=$( echo "${foacc} >= ${off}" | bc ) # off elapsed yet?
    if [ "${elapsed}" == "1" ]; then 
        xset dpms force off;
        foacc=0;
    fi
}

# Returns when the screen has been locked and unlocked
function unlockcheck {
    foacc=0; # forceoff time accumulator
    haslock=
    while true; do
        sleep ${lockdelay}
        locked=$( gnome-screensaver-command -q | grep " active" )
        if [ -n "${haslock}" ]; then
            # lock has happened before. Check unlock and break if unlocked
            if [ -z "${locked}" ]; then break; fi
        fi
        if [ -n "${locked}" ]; then
            haslock="true"
        fi
        if [ "${forceoff}" == "1" ]; then
            echo "forceoffcheck, forceoff=$forceoff"
            forceoffcheck
        fi
    done
}

########################################
# Startup                              #
########################################

# short mixer command with card
m="amixer -c ${card}"
# record original volume value
getvol
orig=$vol

# record original DPMS settings.
dpms=$( xset dpms q | awk '$0 ~ "Suspend" && $0 ~ "Standby" && $0 ~ "Off" { print $2, $4, $6; }' )

########################################
# Procedure                            #
########################################

# set specified DPMS settings:
xset dpms ${standby} ${suspend} ${off}
locktime=$( date +%s )
gnome-screensaver-command -l # lock screen
fade down # fade volume down and mute
let locktime=$( date +%s )-${locktime};
echo "faded down for ${locktime} seconds";
if [ ${locktime} -lt 3 ]; then
    let locktime=3-${locktime}
    echo "giving screen fade ${locktime} seconds more time";
    sleep ${locktime};
fi
xset dpms force off # turn off the screen (directly after lock results in too quick turnoff)
gnome-screensaver-command -i -a "mute-and-lock" & # Stop screensaver from waking up the screen
unlockcheck # wait for unlock
# stop inhibiting screensaver
kill $( ps -ef | awk '$0 ~ "gnome-screensaver-command -i" && $NF == "mute-and-lock" { print $2; }' ) 2>/dev/null
fade up # fade volume up and unmute
xset dpms ${dpms} # restore dpms settings
# That's it!

```

---

### Post by abhiroopb on 2010-01-02
Thanks for the update.

I checked and realised that you were right after a while the screen does turn off automatically.

Thanks again

EDIT: Annoying little thing (NB: REALLY little thing)....basically when the screen/volume dim-down for a couple of seconds the screensaver shows up. Right now I have set the screensaver to "blank screen", but aesthetically it isn't great. Like I said small thing :P

---

### Post by Vermind on 2010-01-02
Hi, try to adjust the step, interval, and dimtime variables.
If the toning down of your sound is taking longer than the dim,
increase step or decrease interval. Increased step may mean that you hear the grades when the sound is going down, decreased interval just makes more steps happen in the same time. A lower dimtime adds less time to the clock for dimming, in case volume fade is fast. Try 2 or 1 second.
Also, for those who do not wish to turn down the volume, but want to turn off the screen, change the value of mute from 1 to 0 (mute=0). Sorry I forgot about that use case. Also, now you can specify nomute as a parameter to the script, so you can have two shortcuts: one with the command ```
/path/to/mute-and-lock.sh
``` and the other with ```
/path/to/mute-and-lock.sh nomute
```, where the second one does not touch your volume but does turn off and keep off the screen.

```
#!/bin/bash
################################################################################
# mute-and-lock.sh                                                             #
# Mutes sound and locks the screen using amixer and gnome screensaver.         #
# Version 1.03                                                                 #
#                                                                              #
# -Added DPMS screen turnoff                                                   #
# -Prevent gnome-screensaver from turning the screen back on                   #
# -Workaround for DPMS timing                                                  #
# -Give screen time to dim (dimtime)                                           #
# -Allow no muting (nomute parameter and mute setting)                         #
#                                                                              #
# written by Vermind                                                           #
################################################################################

########################################
# Settings                             #
########################################

mute=1            # Mute the sound while locked. 0=do not mute. 
                  # Note: nomute as parameter overrides this setting.
card=0            # Sound card. 0 == default, first card.
channel="Master"  # Which volume to control. Examples: Master, PCM, Headphone
step=3            # Fade step: The volume increment/decrement amount
interval=0.2      # Seconds between increments/decrements when fading
dimtime=3         # whole numbers only. The time given for the initial screen dim.
lockdelay=0.5     # How long wait between unlock checks. Smaller values unmute faster
                  # but use more CPU when locked.
                  # DPMS settings to use when locked, 0==infinity:
standby=0         # how many seconds of inactivity to wait before screen standby
suspend=0         # before screen suspend
off=10            # before turning the screen off
# Workarounds:
#forceoff=1        # uncomment to have the screen forced off between the dpms off intervals.


########################################
# Functions                            #
########################################

# get current volume
function getvol {
    vol=$( ${m} sget ${channel} | awk '
$0 ~ "%" { 
    if ($4 ~ "%") {
        print $3;
    } else if ($5 ~ "%") { 
    print $4;
    exit 0;
    }
}' )
}

# fades volume up or down
function fade {
    # get current volume
    getvol
    if [ "$1" == "down" ]; then
        # fade down:
        while [ ${vol} -gt 0 ]; do
            sleep ${interval}
            ${m} set ${channel} ${step}- >/dev/null
            let vol-=${step}
        done
        ${m} set ${channel} mute >/dev/null
   else
       # first unmute, then fade up
        ${m} set ${channel} unmute >/dev/null
         while [ ${orig} -gt ${vol} ]; do
            sleep ${interval}
            let vol+=${step}
            if [ ${vol} -gt ${orig} ]; then vol=${orig}; fi
            ${m} set ${channel} ${step}+ >/dev/null
        done
        ${m} set ${channel} ${orig} >/dev/null
   fi
}

function forceoffcheck {
    foacc=$( echo "${lockdelay} +  ${foacc}" | bc ) # lockdelay elapsed
    elapsed=$( echo "${foacc} >= ${off}" | bc ) # off elapsed yet?
    if [ "${elapsed}" == "1" ]; then 
        xset dpms force off;
        foacc=0;
    fi
}

# Returns when the screen has been locked and unlocked
function unlockcheck {
    foacc=0; # forceoff time accumulator
    haslock=
    while true; do
        sleep ${lockdelay}
        locked=$( gnome-screensaver-command -q | grep " active" )
        if [ -n "${haslock}" ]; then
            # lock has happened before. Check unlock and break if unlocked
            if [ -z "${locked}" ]; then break; fi
        fi
        if [ -n "${locked}" ]; then
            haslock="true"
        fi
        if [ "${forceoff}" == "1" ]; then
            echo "forceoffcheck, forceoff=$forceoff"
            forceoffcheck
        fi
    done
}

function muteandlock {
    locktime=$( date +%s )
    gnome-screensaver-command -l # lock screen
    if [ "${mute}" == "1" ]; then
        fade down # fade volume down and mute
    fi
    if [ ${dimtime} -gt 0 ]; then
        let locktime=$( date +%s )-${locktime};
        echo "faded down for ${locktime} seconds";
        if [ ${locktime} -lt ${dimtime} ]; then
            let locktime=${dimtime}-${locktime}
            echo "giving screen fade ${locktime} seconds more time";
            sleep ${locktime};
        fi
    fi
    xset dpms force off # turn off the screen (directly after lock results in too quick turnoff)
}

########################################
# Startup                              #
########################################

if [ -n "${1}" -a "${1}" == "nomute" ]; then
    mute=0;
fi

if [ "${mute}" == "1" ]; then
    # short mixer command with card
    m="amixer -c ${card}"
    # record original volume value
    getvol
    orig=$vol
fi

# record original DPMS settings.
dpms=$( xset dpms q | awk '$0 ~ "Suspend" && $0 ~ "Standby" && $0 ~ "Off" { print $2, $4, $6; }' )

########################################
# Procedure                            #
########################################

# set specified DPMS settings:
xset dpms ${standby} ${suspend} ${off}
muteandlock # Initial mute and lock of screen
gnome-screensaver-command -i -a "mute-and-lock" & # Stop screensaver from waking up the screen
unlockcheck # wait for unlock
# stop inhibiting screensaver
kill $( ps -ef | awk '$0 ~ "gnome-screensaver-command -i" && $NF == "mute-and-lock" { print $2; }' ) 2>/dev/null
if [ "${mute}" == "1" ]; then
    fade up # fade volume up and unmute
fi
xset dpms ${dpms} # restore dpms settings
# That's it!

```

---

### Post by abhiroopb on 2010-01-09
Since we like tweaking this so much....

Is it possible to do the following:

1. Volume reduces and mutes
**2. Amarok 1.4 music is paused**
3. Screen is blanked
4. Lock

And coming out of lock amarok should be unpaused after volume is unmuted.

Do you think that could be added in?

---

### Post by raffaele181188 on 2010-01-09
Something like this works for me (KDE on Slackware)
```

qdbus org.kde.amarok /Player Play

```
Replace "Play" with "Stop" :D

But I think this thread has became too exaggerated XD

UPDATE
Thx to Amarok guys I discovered the "Best way" . Simply
```

amarok -t

```
"t" stands for "toggle": if it's playing it will pause and vice-versa ;)

---

### Post by abhiroopb on 2010-01-09
Thanks for the tip.

I changed the bottom of the script:

```


########################################
# Procedure                            #
########################################

# set specified DPMS settings:
xset dpms ${standby} ${suspend} ${off}
muteandlock # Initial mute and lock of screen
gnome-screensaver-command -i -a "mute-and-lock" & # Stop screensaver from waking up the screen
amarok -t
unlockcheck # wait for unlock
# stop inhibiting screensaver
kill $( ps -ef | awk '$0 ~ "gnome-screensaver-command -i" && $NF == "mute-and-lock" { print $2; }' ) 2>/dev/null
if [ "${mute}" == "1" ]; then
    fade up # fade volume up and unmute
    amarok -t
fi
xset dpms ${dpms} # restore dpms settings
# That's it!

```

It now pauses/unpauses amarok

---

### Post by Vermind on 2010-01-09
i knew it was a good idea to make the actual procedure short and understandable at the bottom. This enables adding all kinds of things by users.  To minimize version proliferation, I suggest adding a call to a new script after mute and before unmute. This could be called mute_hooks.sh and have two options: when $1 is mute, it would run stuff when locking and muting. When $1 is unmute, it will run things to do just before unmute and unlock. How does this sound?

---

### Post by abhiroopb on 2010-01-09
I have no idea what any of that meant! I assume it would make things easier, if so go for it!

---

### Post by abhiroopb on 2010-01-19
So, the problem with the "amarok -t" command is that if the music is paused when I lock the screen it "plays" the music and when you unlock the music "pauses" so you never actually hear the music. So, I changed the command to "amarok --pause" and "amarok --play".

So now the procedure list should read:

```

########################################
# Procedure                            #
########################################

# set specified DPMS settings:
xset dpms ${standby} ${suspend} ${off}
muteandlock # Initial mute and lock of screen
gnome-screensaver-command -i -a "mute-and-lock" & # Stop screensaver from waking up the screen
amarok --pause
unlockcheck # wait for unlock
# stop inhibiting screensaver
kill $( ps -ef | awk '$0 ~ "gnome-screensaver-command -i" && $NF == "mute-and-lock" { print $2; }' ) 2>/dev/null
if [ "${mute}" == "1" ]; then
    fade up # fade volume up and unmute
    amarok --play
fi
xset dpms ${dpms} # restore dpms settings
# That's it!

```

---

### Post by abhiroopb on 2010-01-21
Since you seem to know a lot about this sort of thing I had a query...

I have a fan underneath my laptop that is connected to the laptop's USB port. When I put my laptop to sleep the fan remains on. I assume power continues to flow to the USB ports. Is there anyway to have the USB ports disabled when the computer is in SLEEP (NB: NOT when it is in lock).

---

### Post by dli8ilb on 2010-10-20
this is really good, any chance for a GUI?  the option to suspend instead of lock screen would be great too. i could really use something like this, but don't know a thing about scripts and such.

---

### Post by Vermind on 2010-10-21
You just save the bunch of text (previous post from me) as a plain text file called mute-and-lock.sh, right-click it and choose properties, make sure the permissions allow executing it, then point to it from System - Preferences- Keyboard Shortcuts - Add.

Any suggestions what you would like a gui to look like? What would it do?

---

### Post by flyingsolow on 2010-11-02
Vermind, thank you very much. To me, this is fantastic. Unfortunately, with amixer, my range of operational volume is fairly small, so I haven't been able to take great advantage of the fade in volume. Can't find cli volume control support for pulseaudio either.

Made some changes:
- Moved line 61 to 63 and line 69 to 73. Moved "sleep ${interval}" to later as the last 2 steps on the fade didn't seem to have a break between them.

---

### Post by Vermind on 2010-11-03
> **flyingsolow said:**
> Vermind, thank you very much. To me, this is fantastic. Unfortunately, with amixer, my range of operational volume is fairly small, so I haven't been able to take great advantage of the fade in volume. Can't find cli volume control support for pulseaudio either.


pactl set-sink-volume index volume
pacmd to experiment with the commands
However, pactl doesnt seem to follow the obvious syntax, for example pactl 1 100 does not set my volume to full. It seems to take a hex value as input:
pactl set-sink-volume 1 0xffff brings my volume to full.
[Someone made complicated-looking snippets to do this]("http://ubuntuforums.org/showpost.php?p=8198147&postcount=7"). See that for examples and let me know how it goes.

---

### Post by Kyluke on 2010-11-04
Hey I tried out your script as this is a brilliant idea however when I try and run the script i get:
.Mute-lock-Monitoroff.sh: 18: function: not found
.Mute-lock-Monitoroff.sh: 27: sget: not found
.Mute-lock-Monitoroff.sh: 28: Syntax error: "}" unexpected

When running the script inside the terminal.

Also is there a way to make rhythmbox pause when this script is run?

---

### Post by Vermind on 2010-11-04
Sounds like it is not getting run properly, is run with a non-bash shell, or only part of it is in the file. So, here is the whole script as an attachment. This is version 1.03.

To do things with rhythmbox, use the rhythmbox-client command.
For example:
```
rhythmbox-client --no-start --no-present --hide --pause
rhythmbox-client --no-start --no-present --play
```
This says not to start rhythmbox if it is NOT running, not to show a rhythmbox window to you when this command is run if not shown already, hide the rhythmbox window, and pause playback. The second one starts playback again.

---

### Post by Teh_Messiah on 2010-11-16
I cant run this remotely or from a cron job through webmin.
My server is also my media player and we have a teenager who at the moment has to sleep in the loungeroom :( (unavoidable atm)
If i set it as a cron job it only mutes and doesn't lock the screen.
If i run it through an ssh terminal i get errors from the gnome-screensaver-command -l command like
```
ben@CentOS-Server:~$ gnome-screensaver-command -l
** Message: Failed to connect to the D-BUS daemon: /bin/dbus-launch terminated abnormally with the following error: Autolaunch error: X11 initialization failed.
```
I'm running Xubuntu 9.10 64bit.
I dont want to shut the computer down because the server is constantly working 24/7.
I want the screen to lock, sound to mute or to pause/kill any running vlc movies from 1am until 7am from monday to friday.

---

### Post by deathanchor on 2011-04-01
So we have a script that works for muting and locking, but how can I set this up so that if I idle away from my computer that it will mute before the lockscreen comes up? Where is that configuration?

Thanks,
Niko

---

### Post by Vermind on 2011-04-01
Hi,
I don't think that exists. I looked around in google and also in gconf-editor, and couldn't find such a thing.

I myself have disabled the screensaver and use only my script to lock the screen. I use xset dpms 0 0 360 to turn off the screen automatically after 6 minutes of inactivity. At this time, the screen does not lock, but the display is turned off, saving energy. Sound is not affected unless I manually run my script by pressing the shortcut key.

To make mute on lock a reality, we need a script that can detect user activity. Then run the mute-and-lock when user activity has not happened for a time.

---

### Post by Teh_Messiah on 2011-04-18
Ok,
I just did a new install to upgrade from 9.10 to 10.10 to fix a few problems and update.
Now the script doesnt lock the screen, it does mute though.
I found that ```
xflock4
``` now locks the screen but even when I edited my mute-and-lock.sh script to use this instead of ```
xscreensaver-command -l
``` it still doesn't work.
Oh the unmute part of the script doesn't work either(and never has).

---

### Post by arnuschky on 2011-08-01
Hey,

I wrote a similar script that monitors the DBus for changes in the screen lock. This approach has the advantage that it works with the auto-lock of the screensaver as well as the pre-configured shortcuts for screen locking; and we don't need to mess with DPMS etc.

I've combined your muting part with the DBus monitor script. Thanks for the great work!

You can find the script here: [http://projects.nuschkys.net/2011/08/01/mute-sound-on-screen-lock/]("http://projects.nuschkys.net/2011/08/01/mute-sound-on-screen-lock/")

Thanks
Arnuschky

---

### Post by Vermind on 2011-08-01
Hi Arnuschky, thanks for your contribution!
I use DPMS because the gnome screensaver only paints black on the screen. DPMS actually turns the display off, saving energy and the display hardware while it is not being used. If the gnome screensaver turned the display off, yours would be the best solution.

Going the DBUS way seems better though :). Any ideas how to incorporate DPMS support there? Something along the lines of: if a screensaver is running, and it is set to blank screen, also use DPMS to turn the display off.

---

### Post by arnuschky on 2011-08-02
Ah, ok, this I didn't get. Why don't you just configure the power saving settings to kick in at the same time as the screensaver? Or don't you use the screensaver, only the lock command?

Cheers,
Arnuschky

---

### Post by Vermind on 2011-08-02
Hi Arnuschky,
I use the lock command only.
Keeping the DPMS display off time the same as the screen saver activation time should do the trick in most cases.
However, for programs that inhibit the screen saver but do not cause input events (such as a movie player) I am not sure if they also inhibit DPMS display off. Someone want to test this? Do for example xset dpms 0 0 60 and start mplayer or totem, and see if the screen goes off in 60 secs.
Normal behaviour can be achieved with xset dpms 0 0 0 (no shutoff).

---

