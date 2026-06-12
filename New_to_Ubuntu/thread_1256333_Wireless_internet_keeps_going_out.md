---
title: "Wireless internet keeps going out"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by pissedoffdude on 2009-09-02
I have an hp hdx16 laptop that just keeps disconnecting from wireless networks.  All of a sudden, the wireless light turns orange and I must push it in order to reactivate it.  

I don't think it's an o/s issue because it goes out in both windows and linux.  Also, it doesn't seem to matter if the network is secured or unsecured, and it happens on multiple networks

Anyone have any ideas? Thanks

---

### Post by bkratz on 2009-09-02
> **pissedoffdude said:**
> I have an hp hdx16 laptop that just keeps disconnecting from wireless networks.  All of a sudden, the wireless light turns orange and I must push it in order to reactivate it.  

I don't think it's an o/s issue because it goes out in both windows and linux.  Also, it doesn't seem to matter if the network is secured or unsecured, and it happens on multiple networks

Anyone have any ideas? Thanks

could it be overheating after a period of time?

---

### Post by pissedoffdude on 2009-09-02
> **bkratz said:**
> could it be overheating after a period of time?

Maybe, but I don't feel it as too hot.  Sometimes it does go off when it appears cool.  I'm usually just browsing the web when it happens, so I don't think it's been overheating.

---

### Post by pierre2113 on 2010-04-12
I have had the exact same problem as the 1st user who posted this for some time now.  After troubleshooting in many, many different paths, I think I have figured out the cause and possibly the solution.

I am currently running Ubuntu lucid 10.04.  I noticed this error message in my log file
/var/log/messages

Apr  4 10:21:06 hdx16t kernel: [ 4284.364525] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
Apr  4 10:21:06 hdx16t kernel: [ 4284.364528] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.

the hdx16t notebook has extra keys that is part of the mediasmart bar and the touchpad button that enables/disable the touchpad.  All of these keys throw the kernel error, I listed one sample above.  I think once I start using one of these mediasmart bar buttons such as the disasble touchpad button, it triggers the RF_KILL toggle also under the kernel control, which happens to be mapped to the wifi button.

Mar 28 11:06:56 hdx16t kernel: [ 1388.407998] atkbd.c: Unknown key pressed (translated set 2, code 0x94 on isa0060/serio0).
Mar 28 11:06:56 hdx16t kernel: [ 1388.408006] atkbd.c: Use 'setkeycodes e014 <keycode>' to make it known.
Mar 28 11:06:56 hdx16t kernel: [ 1388.408030] iwlagn 0000:02:00.0: RF_KILL bit toggled to disable radio.

I followed the advise of the log file in /var/log/messages, and tried to press all the keys to get scancode,keycodes the kernel was not aware of, I came up with the list below.
I put these command in   /etc/rc.local  to be run everytime the system boots
before I have a chance pressing any of these keys.


#several keys use this 0x94
/usr/bin/setkeycodes e014 148
#rewind
/usr/bin/setkeycodes e025 165
#stop
/usr/bin/setkeycodes e026 166
#pause/play
/usr/bin/setkeycodes e024 164
#fast forward
/usr/bin/setkeycodes e023 163

#increase trebble 0xbe
/usr/bin/setkeycodes e03e 190
#decrease trebble 0xbf
/usr/bin/setkeycodes e03f 191

#increase bass 0xc0
/usr/bin/setkeycodes e040 192
#decrease bass 0xc1
/usr/bin/setkeycodes e041 193
#mediasmart check 0xc2
/usr/bin/setkeycodes e042 194

#disable touchpad 0xd8
/usr/bin/setkeycodes e058 216
#enable touchpad 0xd9
/usr/bin/setkeycodes e059 217


there may be other side effect mapping these keys, but for a couple of  days my wifi is not toggling off by itself anymore.

so far the touchpad has 2 second delay before it starts working after disabling/enabling

in /var/log/messages it shows a minor error, but touchpad works eventually.

Apr 11 23:36:40 hdx16t kernel: [41177.229349] psmouse.c: TouchPad at isa0060/serio1/input0 lost synchronization, throwing 4 bytes away.
Apr 11 23:36:40 hdx16t kernel: [41177.746103] psmouse.c: resync failed, issuing reconnect request

---

### Post by pierre2113 on 2010-04-13
some corrections to my previous post, I had some incorrect scan codes.
also running setkeycodes to increase/decrease bass button had the side effect
of enabling/disabling the touch pad.  running setkeycodes for the touch pad on/off toggle did not return touchpad control until you switch to the console then back to the X screen.

Anyone else having wifi keep going out here's my total config.
in /boot/grub/grub.cfg
I have added   rfkill.default_state=1 
to the line

linux    /boot/vmlinuz-2.6.32-18-generic root=UUID=fb09f422-7fb7-44aa-9796-ea35e702a9c3 ro   crashkernel=384M-2G:64M,2G-:128M rfkill.default_state=1 splash


in /etc/rc.local

#mediasmart check 0xc2
/usr/bin/setkeycodes e042 194

##rewind
/usr/bin/setkeycodes e010 165
##stop
/usr/bin/setkeycodes e024 166
##pause/play
/usr/bin/setkeycodes e022 164
##fast forward
/usr/bin/setkeycodes e019 163

#eject button-no keycode seems to be generated

#mute
/usr/bin/setkeycodes e020 113

#decrease volume
/usr/bin/setkeycodes e02e 114
#increase volume
/usr/bin/setkeycodes e030 115

#increase trebble 0xbe
/usr/bin/setkeycodes e03e 190
#decrease trebble 0xbf
/usr/bin/setkeycodes e03f 191

#all keys seem to generate 0x94
/usr/bin/setkeycodes e014 148


Pressing the Mute button, or increase/decrease volume slide button now do not cause the wifi to start going out by itself anymore, but I haven't really tested if all the remaing (media playback controls) on the mediasmart bar still work.

---

