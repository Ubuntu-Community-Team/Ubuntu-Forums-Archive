---
title: "Shutdown problems"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by ColinBrenton on 2010-09-18
Hi,

I think absolute beginner describes me well, so this is the place to post...

I've just started to use Ubuntu after years using XP (I know, I know...). Everything so far is good (even got my email working in Ubuntu, that was the last thing to overcome before I could ditch windows :-) ), but for an odd issue with shutting down the machine.

The computer is a laptop, and has a power button on it. The is also a menu for shutdown options at the top right of the screen. At the moment the power button has no effect, and any option in the menu logs me out and takes me back to the login screen.

How can I make the power button either shutdown the computer, or give me a choice (logoff, restart, shutdown), don't mind which?

Also, how can I fix the menu items so that they work correctly?

From searching here, this seems a common problem, but I haven't found any solutions.

Thanks in advance for any help.

Colin

---

### Post by scorchgeek on 2010-09-18
As for making the power button do what you want, you can choose System-->Preferences-->Power Management, go to the General tab, and select from there.

I can't help you with the menu problem, but if you just need to shut down you can run the command 
```
sudo halt
```
in a terminal. It's a clumsy solution, but it'll work for now. (Rebooting is the same, but with reboot instead of halt.)

Or you can hit Alt-F2 for the Run Application dialog and run
```
gksu halt
``` It does the same thing.

---

### Post by abs_kkk on 2010-09-18
first of all welcome to linux and ubuntu.
Secondly to make your power button work go to "system" menu (which is in the upper panel) then select "preferences" sub menu and select "power management"
when the window pops up select "general" tab there u will hav the options which u need.
 and u can also shut down with the menu from the top right,which u click on the computer name/admin
there is a menu in which it has options such as shutdown and such.Alternatively right click on the upper panel and select "add to panel" and search for "shut down" ,add it then u will have a shortcut button(just click it when u want to shutdown).

well then go ahead and enjoy ubuntu. ^_^

---

### Post by ColinBrenton on 2010-09-18
Hi,

Thanks for the suggestions.

To follow up, for the power button, the only  option I have is "Ask Me", which doesn't work.

I've been here [http://ubuntuforums.org/showthread.php?t=1466589](http://ubuntuforums.org/showthread.php?t=1466589) and tried all of the given suggestions (5 pages of them). They don't work, either.

Can anyone suggest anything else, or suggest an operating system where simple, basic essential fundamental features like being able to turn off the computer function correctly and were tested when the code was written?

How can something so simple be so difficult :mad:

I JUST WANT TO BE ABLE TO TURN THE COMPUTER OFF AT THE END OF THE DAY.

At the moment I have to unplug it and pull the battery out, nothing else will touch it.

---

### Post by scorchgeek on 2010-09-18
Like I said, if nothing else will work you can run one of the commands I mentioned. Have you tried the panel applet abs_kkk suggested?

---

### Post by scorchgeek on 2010-09-18
It seems to me that the problem may be that your power management settings on the hardware are either configured incorrectly or not supported. Have you tried any other operating systems on this computer? If so, do they shut down normally? How old is your computer?

This is certainly an unusual incident; don't be so quick to blame it on inadequate testing. In even the most polished software, there are some bugs and incompatibilities.

---

### Post by ColinBrenton on 2010-09-18
Hi,

Sorry, you are right, it's not fair to blame the authors of the software - lets face it, there are far fewer problems than in certain other applications....

I didn't in fact try the add-on to the panel, as there doesn't seem to be shutdown option to add.

I think in fact that I may have stumbled across a fix... Someone in another thread suggested editing the Grub config file and making the following change;

sudo gedit /etc/default/grub

change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

by : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"

Followed by sudo update-grub and then rebooting.

I did try this, but it seemed to make no difference, however it did allow me access to options for the power button, which I was then able to change from "Ask Me" to "Shut Down". I then reversed the change to Grub, as per the above. All now seems to be well.

I'll leave this for a couple of days to see if the fix really does work, and mark it solved. :D

Thanks to all for the suggestions, much appreciated.

Cheers,

Colin

---

### Post by dcsoldschool53 on 2010-09-18
> **ColinBrenton said:**
> Hi,

I think absolute beginner describes me well, so this is the place to post...

I've just started to use Ubuntu after years using XP (I know, I know...). Everything so far is good (even got my email working in Ubuntu, that was the last thing to overcome before I could ditch windows :-) ), but for an odd issue with shutting down the machine.

The computer is a laptop, and has a power button on it. The is also a menu for shutdown options at the top right of the screen. At the moment the power button has no effect, and any option in the menu logs me out and takes me back to the login screen.

How can I make the power button either shutdown the computer, or give me a choice (logoff, restart, shutdown), don't mind which?

Also, how can I fix the menu items so that they work correctly?

From searching here, this seems a common problem, but I haven't found any solutions.

Thanks in advance for any help.

Colin
try this in a terminal a code to shutdown pc
```
sudo telinit 0
```or

```
/usr/bin/gnome-session-save --shutdown-dialog
```This will bring up a menu whereby you can choose the shutdown option.

---

