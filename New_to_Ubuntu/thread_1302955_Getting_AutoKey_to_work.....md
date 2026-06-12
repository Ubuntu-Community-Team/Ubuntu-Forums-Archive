---
title: "Getting AutoKey to work....?"
date: 2009-10-27
forum: New to Ubuntu
---

### Post by listerdl on 2009-10-27
Hi, has anyone been able to get the automatic text editor/replacer AutoKey to work?

Basically you make your own shortcuts so that if you type say "adr" minus the "" - it will fire up your address - very handy when writing emails/letters etc.

Anyway - I simply cant get it to work...am i missing something very basic here?

I really loved Texter for Windows which simply - just works.

Can anyone shed light on how to go ahead and make a text string?

THANKS!!!!!!!!

---

### Post by marshag63 on 2009-10-28
What exactly is the problem you are having? - installing or just how to get your abbreviations added and triggered?


[http://autokey.sourceforge.net/](http://autokey.sourceforge.net/)

[http://groups.google.com/group/autokey-users](http://groups.google.com/group/autokey-users)


MarshaG.

---

### Post by listerdl on 2009-10-29
> **marshag63 said:**
> What exactly is the problem you are having? - installing or just how to get your abbreviations added and triggered?


MarshaG.

Thanks.

Problem is getting text to be triggered...

Any idea what I could not have activated - ive looked everywhere.

---

### Post by marshag63 on 2009-10-29
If you are using a version of ubuntu older than 9.xx, you need to set interface to Xrecord (Advanced Settings > Interface and choose Xrecord).  If you are using Jaunty or newer, leave it at Xedev

Also, make sure that "Enable Monitoring" has a checkmark next to it (right click on icon in system tray to enable/disable and also access the configuration dialog).

When you set the abbreviation you want to use for your text and press the "set" key, it should take you to another dialog box - make sure it is set to trigger the way you want (i.e. case sensitive, as part of a word or whatever, etc.)

Let us know which version of Ubuntu you are using and if choose Xrecord or Xdev makes a difference.

MarshaG.

---

### Post by listerdl on 2009-10-29
> **marshag63 said:**
> If you are using a version of ubuntu older than 9.xx, you need to set interface to Xrecord (Advanced Settings > Interface and choose Xrecord).  If you are using Jaunty or newer, leave it at Xedev

Also, make sure that "Enable Monitoring" has a checkmark next to it (right click on icon in system tray to enable/disable and also access the configuration dialog).

When you set the abbreviation you want to use for your text and press the "set" key, it should take you to another dialog box - make sure it is set to trigger the way you want (i.e. case sensitive, as part of a word or whatever, etc.)

Let us know which version of Ubuntu you are using and if choose Xrecord or Xdev makes a difference.

MarshaG.

Hey thanks for the help. I am using: Ubuntu/8.10 (intrepid)

I tried everything you suggested but still no joy. I tried all the different variations and no joy. The Tray Phrases work but nothing seems to want to trigger any phrases...

thanks for your help - any other ideas?

(PS I re-booted too)

---

### Post by marshag63 on 2009-10-29
Did you install from the PPA?  If so, did you choose the Intrepid version?


One other thought, in the dialog box "Set Abbreviation" leave the "trigger on" option to "default" this means when you press the space bar or type a period, comma, colon, semicolon, enter key, etc, the abbreviation will trigger.  Try your abbeviations in a plain text editor and see what happens.

Do they trigger okay via mouse using the system tray icon? 

By the way, what version did you install?  The latest is 0.60.7a


[http://code.google.com/p/autokey/wiki/Troubleshooting](http://code.google.com/p/autokey/wiki/Troubleshooting)
How do I know which interface to use? (Settings->Advanced Settings->Device Interface)

When you start AutoKey for the first time, it attempts to choose the best possible option for you. For most people, this should work fine. As the dialog states, only change the setting if AutoKey is not responding to hotkeys and abbreviations. In that case, you can simply try the various options and see which works best for you. Note that some of the interfaces don't work at all, depending on your distribution. To summarise:

X Record: Will work in any distribution using X.org server prior to version 1.6. E.g. Ubuntu Jaunty upgrades the server to v1.6, and as a result XRecord will not work. X EvDev: Should work in most cases, except if you are using 'exotic' hardware such as Bluetooth keyboards (or any keyboard device that does not use the EvDev X driver). AT-SPI: Only works when the active window is a GTK-based application (including Firefox 3). Also requires certain configuration items in your Gnome environment to be enabled (see below). 

Again, let me know what version you installed and how.

MarshaG.

P.S.  I will hang out at the autokey forum:  irc.freenode.net #autokey for a while is case you want to drop in - maybe a dev will be there.

---

