---
title: "Switch Between Screens (Keyboard Shortcut)"
date: 2009-06-02
forum: New to Ubuntu
---

### Post by sharpdust on 2009-06-02
I have a dual monitor setup. Is there a keyboard shortcut to move the focus to the other screen?

For example, if I click Alt-Tab, I get a list of windows on the current screen. I want to be able to be able to press some keyboard shortcut, and when I press Alt-Tab again, have a list of windows on the other screen.

---

### Post by sharpdust on 2009-06-03
bueller...bueller?

---

### Post by zippaplick on 2009-09-04
I've got the same question.

Got 2 monitors, separate xsession on each screen, I can move the mouse between screens but I want to switch screens via hot key.

Anybody know how? ( U9.04, nvidia)

Thanks!

---

### Post by zippaplick on 2009-09-04
Got it.
Found a handy utility here that I just bind to my <Super>-Tab hot keys. Works great.
[http://digamma.cs.unm.edu/trac.dmohr/wiki/DualscreenMouseUtils](http://digamma.cs.unm.edu/trac.dmohr/wiki/DualscreenMouseUtils)

For the impatient, do this:

wget [http://dsp.mcbf.net/releases/dualscreen-mouse-utils-0.5.tar.gz](http://dsp.mcbf.net/releases/dualscreen-mouse-utils-0.5.tar.gz)
tar xzf dualscreen-mouse-utils-0.5.tar.gz 
cd dualscreen-mouse-utils-0.5
less README
make
./mouse-switchscreen --help
./mouse-switchscreen -f 1    # mouse should be on other screen
./mouse-switchscreen -f 1    # mouse shou be back where you started.
cp mouse-switchscreen /somewhere/on/your/PATH

Bind your hot-key to" mouse-switchscreen -f 1".

Press hot-key, find mouse at last location on other screen.
Press alt-tab see other screen's window list.
 
Go back and forth, go crazy! 

;)

---

### Post by Seebi on 2009-10-21
Very useful! Tested successfully under Ubuntu 9.04 jaunty.

Note: To compile the tool, you will need some X header files: [FONT="Courier New"]sudo apt-get install xorg-dev[/FONT]

---

### Post by appleshampooid on 2011-12-02
I had some problems compiling the mouse-switchscreen utility, which I described [in this other thread](http://ubuntuforums.org/showthread.php?t=1011515).  I'm on 11.10 if that makes a difference.

---

