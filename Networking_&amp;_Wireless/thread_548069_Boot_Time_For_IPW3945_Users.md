---
title: "Boot Time For IPW3945 Users"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by Matthew Wiebelhaus on 2007-09-10
[CENTER][SIZE=5][COLOR=Red][SIZE=7]This guide is for users of the ipw3945 card  that have a boot that hangs[/SIZE]
[COLOR=Black][SIZE=2]

If your boot time hangs at [_________|_______________] on the status bar then you may have problems with ipw3945, if it goes through normal then you probably do not have any problems with ipw3945.

There are two simple ways to fix this problem I am not held responsible for any damage this is how i fixed it and may others have fixed it.

[SIZE=6]Option 1 Editing [/SIZE][/SIZE][/COLOR][/COLOR][/SIZE][FONT=Tahoma][SIZE=6][COLOR=Black]S40networking
[SIZE=2]
This will probably fix your problem the first time if not there is always option 2.

First we edit the networking file:
[/SIZE][/COLOR][/SIZE][/FONT][CENTER]sudo gedit /etc/rcS.d/S40networking[/CENTER]

  [COLOR=Black]now, put "##" in your code as follow:
(or simply overwrite your code with those lines respectively)
[COLOR=Red]**BOLD AND RED MARKS WHERE YOU NEEDED TO PUT ## BEFORE THE CODE**[/COLOR]

 [/COLOR]
```
 case "$1" in
start)
    log_action_begin_msg "Configuring network interfaces"
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 120" || true
[COLOR=Red] ##[/COLOR]    if [ "$VERBOSE" != no ]; then
[COLOR=Red] ##[/COLOR]        if ifup -a; then
[COLOR=Red] ## [/COLOR]       log_action_end_msg $?
[COLOR=Red] ## [/COLOR]       else
[COLOR=Red] ##[/COLOR]        log_action_end_msg $?
[COLOR=Red] ##[/COLOR]        fi
[COLOR=Red] ##[/COLOR]    else
[COLOR=Red] ##[/COLOR]        if ifup -a >/dev/null 2>&1; then
        log_action_end_msg $?
[COLOR=Red] ##[/COLOR]        else
[COLOR=Red] ##[/COLOR]        log_action_end_msg $?
[COLOR=Red] ##[/COLOR]        fi
[COLOR=Red] ## [/COLOR]   fi
        type usplash_write >/dev/null 2>/dev/null && usplash_write "TIMEOUT 15" || true
    ;;

stop)
```[SIZE=5][COLOR=Red][COLOR=Black][SIZE=2]Note This Is not the whole file if you are overwriting find in your file:[/SIZE][/COLOR][/COLOR][/SIZE] [COLOR=Black]**case "$1" in **and over write that all the way up to**stop)**[/COLOR][SIZE=5][COLOR=Red][COLOR=Black][SIZE=2][B] 

Restart your computer after saving and your boot time should be normal 

[SIZE=5]MAKE SURE TO MAKE A BACKUP!!

[SIZE=6]OPTION 2
[SIZE=2]

This is slightly simpler but may not work for all

[/SIZE][/SIZE][/SIZE][/B][SIZE=5][SIZE=6][SIZE=2]First make sure that eth1 is ipw3945 ([/SIZE][/SIZE][/SIZE][/SIZE][/COLOR][/COLOR][/SIZE]Verify via [B]lshw -C network)
[/B][COLOR=Black]Second after verifing: **remove the stanza (all lines) regarding eth1 from /etc/network/interfaces**; this will (a) tell it not to try to configure the interface automatically at boot and (b) will tell NetworkManager to treat the device in "roaming mode". Typically the wireless interface on a portable is configured later by NetworkManager or the like.[/COLOR]
[B]
[COLOR=Red][SIZE=7]AGAIN, MAKE A BACK UP!!!!!!

[/SIZE][/COLOR][/B][SIZE=2][COLOR=Red]DISCLAIMER- I am not responsible for any damage done to your computer if you made a backup and it ****ed up then you can replace your file. If you do not listen and it ****s up done whine you didn't follow directions![/COLOR][/SIZE][/CENTER]

Credits: Matthew Wiebelhaus, noob12

---

### Post by noob12 on 2007-09-10
Yikes.  I don't remember recommending that!?

That's a pretty broad hammer!   This will disable boot-time startup of all interfaces in your **/etc/network/interfaces** file.  

The recommended way would just be to remove the lines for the interface associated with your ipw3945 card from your /etc/network/interfaces file or at least comment out the **auto** line for that interface.  Then **ifup -a** should ignore that interface at boot.

The approach here will prevent all interfaces from being configured by **ifup** at boot.

---

### Post by Matthew Wiebelhaus on 2007-09-11
Yes you recommended second one.

---

### Post by Matthew Wiebelhaus on 2007-09-11
Also if you want me ot remove you from credits I can it only disables eth1 from starting on boot network manager can then later configure it easily and timelessly.

---

