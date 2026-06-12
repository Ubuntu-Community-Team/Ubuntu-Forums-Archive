---
title: "gedit word wrap and horizontal ruler"
date: 2011-06-24
forum: New to Ubuntu
---

### Post by TRex on 2011-06-24
**Word Wrap**
Is there a keystroke combination that can be used from within gedit to turn word wrap on and off?

If not, can a keystroke combination be created to do this and, if so, how?


**Horizontal Ruler**
Is there an add-on which will give gedit a horizontal ruler? If not, is there a text editor for gnome which includes a horizontal ruler?

---

### Post by Abir Valg on 2011-06-25
Have you seen the plugin to assign keyboard shortcuts?
[http://empty.23inch.de/pmwiki.php/Main/EditShortcuts](http://empty.23inch.de/pmwiki.php/Main/EditShortcuts)

I'm not sure if it handles WordWrap, please let me know.

---

### Post by TRex on 2011-06-25
I got the plugin installed without a problem and then found it under Edit/Preferences and made it active. That added an entry under Tools which had an entry for 'Edit Preferences', but not for anything within Preferences. That might have been a small step towards what I want, but when I pressed Ctrl+E to assign a shortcut to Edit Preferences, it displayed a 'Ctrl-Mod2-E' next to menu item -- don't know what a Mod2 key is -- but Ctrl+E didn't work. :(

---

### Post by jtarin on 2011-06-25
[don't know what a Mod2 key is]("http://kheyali.blogspot.com/2008/06/mathematica-problem-in-linux-hardy.html")

---

### Post by bab1 on 2011-06-25
> **TRex said:**
> I got the plugin installed without a problem and then found it under Edit/Preferences and made it active. That added an entry under Tools which had an entry for 'Edit Preferences', but not for anything within Preferences. That might have been a small step towards what I want, but when I pressed Ctrl+E to assign a shortcut to Edit Preferences, it displayed a 'Ctrl-Mod2-E' next to menu item -- don't know what a Mod2 key is -- but Ctrl+E didn't work. :(

The current default keymap can be seen with this command```
xmodmap
```

On my host it responds with this```
xmodmap:  up to 4 keys per modifier, (keycodes in parentheses):

shift       Shift_L (0x32),  Shift_R (0x3e)
lock        Caps_Lock (0x42)
control     Control_L (0x25),  Control_R (0x69)
mod1        Alt_L (0x40),  Meta_L (0xcd)
mod2        Num_Lock (0x4d)
mod3      
mod4        Super_L (0x85),  Super_R (0x86),  Super_L (0xce),  Hyper_L (0xcf)
mod5        ISO_Level3_Shift (0x5c),  Mode_switch (0xcb)

```

the command is located here```
/usr/bin/X11/xmodmap
```

This is on a pretty plain Ubuntu 10.04.2 Lucid install.  Of course you can modify the modemap and change the keys for mod1 thru 4.

You can read more [**_[COLOR="DarkSlateGray"]here[/COLOR]_**]("http://www-01.ibm.com/support/docview.wss?uid=swg21401951") under ***xmodemap***

---

