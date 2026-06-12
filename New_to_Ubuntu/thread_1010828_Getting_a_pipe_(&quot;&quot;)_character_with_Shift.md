---
title: "Getting a pipe (&quot;|&quot;) character with Shift-BackSpace key-combo"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by wacky_keyboards on 2008-12-14
Hello,

As my name implies, I like slightly wacky keyboard layouts.  More
specifically, I grew up on the old Sun workstation style of
keyboards, so I prefer my BackSpace key where on most PC keyboards
the BackSlash/Pipe ("\" and "|") key is located.  So I've gotten
into the habit of using xmodmap(1) to swap the two.

However, under Intrepid Ibex (8.10), I am unable to use the key
combination Shift-BackSpace to obtain the Pipe ("|") character.

A search of "Shift-BackSpace" turned up many entries about how
this kills, or used to kill, the X server, so I'm guessing that
Shift-BackSpace is disabled.  But I have no idea (if this is the
case) how to re-enable it.

Can anyone help?

Thanks!

Setting information and experiment data follow:

This is a fresh installation of Ubuntu 8.10.  Keyboard remapping
is one of my top priorities!  I used xmodmap(1) to obtain the
existing mapping, and then swapped the keycodes for the entries
for the two keys, and then invoked xmodmap again:

     % xmodmap -pke > .xmodmaprc
     % vi .xmodmaprc
     % xmodmap .xmodmaprc

At this point, if I hit the BackSpace key, I'll get the BackSlash
character ("\").  But if I hit Shift-BackSpace, I'll still get
the BackSlash character, not the Pipe character.  xev(1) indicates
that a LeftShift+BackSlash event is being seen, but it's being
mapped to the BackSlash character:

KeyPress event, serial 31, synthetic NO, window 0x3400001,
    root 0x25b, subw 0x0, time 1840638, (70,123), root:(1538,174),
    state 0x0, keycode 22 (keysym 0x5c, backslash), same_screen YES,
    XLookupString gives 1 bytes: (5c) "\"
    XmbLookupString gives 1 bytes: (5c) "\"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x25b, subw 0x0, time 1840707, (70,123), root:(1538,174),
    state 0x0, keycode 22 (keysym 0x5c, backslash), same_screen YES,
    XLookupString gives 1 bytes: (5c) "\"
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x25b, subw 0x0, time 1841574, (70,123), root:(1538,174),
    state 0x0, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XmbLookupString gives 0 bytes: 
    XFilterEvent returns: False

KeyPress event, serial 34, synthetic NO, window 0x3400001,
    root 0x25b, subw 0x0, time 1842142, (70,123), root:(1538,174),
    state 0x1, keycode 22 (keysym 0x5c, backslash), same_screen YES,
    XLookupString gives 1 bytes: (5c) "\"
    XmbLookupString gives 1 bytes: (5c) "\"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x25b, subw 0x0, time 1842197, (70,123), root:(1538,174),
    state 0x1, keycode 22 (keysym 0x5c, backslash), same_screen YES,
    XLookupString gives 1 bytes: (5c) "\"
    XFilterEvent returns: False

KeyRelease event, serial 34, synthetic NO, window 0x3400001,
    root 0x25b, subw 0x0, time 1842519, (70,123), root:(1538,174),
    state 0x1, keycode 50 (keysym 0xffe1, Shift_L), same_screen YES,
    XLookupString gives 0 bytes: 
    XFilterEvent returns: False

---

### Post by wacky_keyboards on 2008-12-15
I just discovered that this behavior does not occur in
a kterm(1).  I also discovered that this behavior *does*
occur in the gnome-terminal(1).  My guess is that kterm
is not recognizing some X event that gnome-terminal and
xterm do.

Can anyone point me to a setting or resource that will
disable this event?

Thanks!

---

### Post by wacky_keyboards on 2008-12-15
I found the answer!

     [http://www.manniwood.com/unix_stuff/index.html](http://www.manniwood.com/unix_stuff/index.html)

The key is to edit the file,

     /usr/share/X11/xkb/symbols/pc

and change the following:

    key <BKSP> {
        type="CTRL+ALT",
        symbols[Group1]= [ BackSpace,   Terminate_Server ]
    };

to:

    key <BKSP> {
        type="CTRL+ALT",
        symbols[Group1]= [ BackSpace,   Terminate_Server ]
    };

Very annoying, but at least the problem is solved!

---

### Post by Xnyper on 2009-03-03
I may have found a typo:

> **wacky_keyboards said:**
> 
The key is to edit the file,

     /usr/share/X11/xkb/symbols/pc

and change the following:

    key <BKSP> {
        type="**CTRL+ALT**",
        symbols[Group1]= [ BackSpace,   Terminate_Server ]
    };

to:

    key <BKSP> {
        type="**CTRL+ALT**",
        symbols[Group1]= [ BackSpace,   Terminate_Server ]
    };


Should be:

    key <BKSP> {
        type="**TWO_LEVEL**",
        symbols[Group1]= [ BackSpace,   Terminate_Server ]
    };

Doing this appears to be the best way to swap those two keys, but it does break "CTRL+ALT+BKSP" for restarting X.  A small price to pay for more efficient typing, but if somebody knows how it can be restored...

---

### Post by wacky_keyboards on 2009-03-03
Ah, thanks for fixing my typo!  Yes, you are correct.

As for losing the ability to kill the X-server, I see
that as a bonus, as I have accidentally killed X too
many times ....

---

### Post by beartard on 2009-06-06
> **Xnyper said:**
> 
Doing this appears to be the best way to swap those two keys, but it does break "CTRL+ALT+BKSP" for restarting X.  A small price to pay for more efficient typing, but if somebody knows how it can be restored...

As much as I hear about it, I'm still trying to figure out what anyone's doing to "accidentally" kill the xserver with ctrl+alt+backspace  ;)

At any rate, thanks for those who found the right answer in this thread.  I was searching the forums for ways to do just this (swap backspace with backslash).  I also swapped Esc with `/~.

As for the xserver killing, I re-mapped it in the same "pc" file to ctrl+alt+scroll-lock, using the reverse of the procedure above for backspace.  I didn't test it, but given the above edit, it looks like shift+backspace would kill the xserver now instead of ctrl+alt.  I changed "terminate_server" to "backspace" just in case.  Then I edited the entry for scroll lock to have the type of ctrl+alt and added terminate_server to the symbols list.

---

### Post by bigpook on 2009-06-07
Hey, thats working out great for me. 

A few more changes and I will be able to emulate the HHKB keyboard.

For those that are familiar, the Happy Hacking Keyboard Pro uses a Function key to activate certain keys.

Function + [ = Up Arrow

Function + / = Down Arrow

Function + ; = Left Arrow

Function + ' = Right Arrow

Function + l = Page Up

Function + . = Page Down

Function + k = Home

Function + , = End


Ideally, the function key would be the windows key and on Unbuntu 9.04 the windows key is mapped as Super.

---

### Post by philinux on 2009-06-07
> **beartard said:**
> As much as I hear about it, I'm still trying to figure out what anyone's doing to "accidentally" kill the xserver with ctrl+alt+backspace  ;)

At any rate, thanks for those who found the right answer in this thread.  I was searching the forums for ways to do just this (swap backspace with backslash).  I also swapped Esc with `/~.

As for the xserver killing, I re-mapped it in the same "pc" file to ctrl+alt+scroll-lock, using the reverse of the procedure above for backspace.  I didn't test it, but given the above edit, it looks like shift+backspace would kill the xserver now instead of ctrl+alt.  I changed "terminate_server" to "backspace" just in case.  Then I edited the entry for scroll lock to have the type of ctrl+alt and added terminate_server to the symbols list.


The other default method for killing x is

alt+prtscreensysreq+k

---

