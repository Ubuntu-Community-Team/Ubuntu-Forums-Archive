---
title: "Freeze at web and more (Compaq N600c)"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by Erik M on 2010-01-10
Howdy folks, good to see Linux up and conquering the wwworld!

Now then, I have this Compaq N600c and it freeze up when I start Firefox or run the Synaptic Package Installer.
It finds both internet and ethernet(wlan/Gigabyte) just fine, ie it connects just fine.

So I sit back a few hours and install Fedora12 instead.
Now I can run Firefox just fine, over the cable, but no way start the wireless. It finds it, but refuse to connect with it.

What's the problem? What can I do more?
I feel I want to use ubuntu, but really need help here.
Could I get some help with this?

---

### Post by Paqman on 2010-01-10
Can you be a bit more specific about what happens when your machine freezes? Does your browser window go grey for example?

---

### Post by Erik M on 2010-01-10
It doesn't get that far, it comes a bit into starting it up and then freeze. So it's while loading.

---

### Post by Paqman on 2010-01-10
So the whole machine freezes? Can you move the cursor at all? Is the hard drive light on and/or the hard drive is making noise? What do you do to get your system back?

---

### Post by Erik M on 2010-01-10
Right, the whole machine freeze up.
Cursor (circle with dots) is still and can't be moved.
It takes ~12 sec for it to freeze up and I get it back by making a forced switch off.

Notable is that this installation has been made on two other laptops with no problem.

---

### Post by Paqman on 2010-01-10
In future, instead of powering off, you might want to try Alt-PrintScreen-K, which should kill your session and dump you back at the login screen.

Have you checked the logs? And does it happen for any kind of app you open, or just one?

---

### Post by Erik M on 2010-01-11
Update Manager *[COLOR=SeaGreen]work[/COLOR]*
"Starting Administrativ... *[COLOR=Red]lock[/COLOR]*
Alt+PrntScrn+K [COLOR=Red]doesn't[/COLOR] work, perhaps because PrntScrn is a Fn-button?
BlackJack *[COLOR=SeaGreen]work[/COLOR]*
Install Multimedia Plugins *[COLOR=SeaGreen]work[/COLOR]*
_Installing_ Multimedia Plugins *[COLOR=Red]lock[/COLOR]*
"change size of window" *[COLOR=Red]lock[/COLOR]* ([COLOR=DarkOrange]![/COLOR])
Log File Viewer *[COLOR=Red]lock[/COLOR]* [COLOR=DarkOrange]Sic![/COLOR]

---

### Post by Paqman on 2010-01-11
You might want to try booting up into your LiveCD and running some of those apps. If they run fine from the CD then it's a software issue (or possibly hard drive), if you get similar behaviour then it's hardware.

---

### Post by Erik M on 2010-01-11
I got it all working. Went in under F1 (help) and then over to F6. Marked some off there and now it's smooth sailing. No idea what's not there. But it works...\\:D/
...VLC doesn't sem to work as well as under XP thou.](*,)

---

