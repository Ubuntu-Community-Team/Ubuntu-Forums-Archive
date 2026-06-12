---
title: "Ibex cannot be accessed after update"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by SteelCore on 2009-02-25
Follow up from my unsolved post [http://ubuntuforums.org/showthread.php?p=6794653#post6794653](http://ubuntuforums.org/showthread.php?p=6794653#post6794653)

I now reformatted the whole system again; Ibex dual boot with Win xp. This time I successfully downloaded and installed all of the available 259 updates.  As before, after restart, I had the following entries in the bootloader:

Ubuntu 8.10, kernel 2.6.27-11 generic
Ubuntu 8.10, kernel 2.6.27-11 generic (recovery)
Ubuntu 8.10, kernel 2.6.27-7 generic
Ubuntu 8.10, kernel 2.6.27-7 generic (recovery)

Tried to access both 2.6.27-11 and 2.6.27-7 but all I got was a black screen although I do hear the startup drum sound.

Thank you in advance for any help.

---

### Post by yeats on 2009-02-25
Are you able to log into a terminal window (i.e., Ctrl-Alt-F1)?  If so, log in and do:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then post back.

---

### Post by SteelCore on 2009-02-25
OK.
From the bootloader I accessed Ubuntu 8.10, kernel 2.6.27-11 generic. At the black screen Ctrl+Alt+F1 and I entered your code.

```
xserver-xorg postinst warnig; overwriting possibly-customised configuration file; backup in /etc/x11/xorg.conf.20090225191732
```

tried to login afterwards but no use.

---

### Post by SteelCore on 2009-02-25
Seems I have found a page that specifically discusses my problem [https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen](https://wiki.ubuntu.com/X/Troubleshooting/BlankScreen) 
In workaround C (disable usplash) it says:
"There have been cases where a bug in usplash prevented X from loading. To check this, in the grub menu edit the kernel line and remove 'splash' from the end of the line, and boot. If that solves the issue, you can remove it from your /boot/grub/menu.lst as a workaround."

Can someone please give me a more detailed explanation on how to edit the kernel line in the grub menu.  And also how to 'remove it' for /boot/grub/menu.lst
Thanks for any help

---

### Post by pandajaune on 2009-02-25
hello,

i am from france and have the same issue.
you can edit this file just like you did for the two steps before in the link you gave with a sudo nano ....
as result for me : no good either

but it allowed me to notice firestarter initialization failed

next...

---

### Post by pandajaune on 2009-02-25
i got the solution. well, my solution. i hope it will work for you as well.

when you boot in recovery mode, go to console mode
then uninstall the catalyst

well i am thinking right now... do you have an ati graphic card?

so i uninstalled them and reboot. i had once again the black screen of death. even twice. but miracle happens sometimes, a little window appeared and i could finally solve my issue.

i hope you will do so soon

vZ

---

### Post by SteelCore on 2009-02-25
Thank you Pandajaune for your answer.  Regarding the first 2 workarounds I didnt really try them but I managed to open the menu.lst with vim although I couldn't find any occurance of the word 'usplash'.
And yes I do have an ATI graphic card.  I'm using an LG S1 Express Dual Laptop; these come with an ATI Mobility Radeon X1600.
Regarding the part about 'uninstalling the catalyst', can you plz give me the code to do that.
Merci again for your assistance

---

### Post by pandajaune on 2009-02-26
cd /usr/share/ati

sudo sh ./fglrx-uninstall.sh

---

### Post by SteelCore on 2009-02-26
Just checked.  I don't have an /ati in /usr/share which I think means I'm not even using the ATI proprietary driver.  Thanks anyway.

---

### Post by cvrse on 2009-02-27
i'm having the exact same problem after updating Ibex, i've tried the solutions on that page however they dont seem to make any difference.
if u'd like to test without usplash goto the kernel line your booting from in /grub/boot/menu.lst and remove "splash" from the end of the line. this removed the usplash for me but didnt make any difference, being i dont think the problem is X not starting as it seems to boot fine just cant access it

---

### Post by pandajaune on 2009-02-27
still, maybe this is a hint. find your own driver, uninstall it and restart.
there should some info in ubuntu online documentation as there is one for the french community.

good luck

---

### Post by SteelCore on 2009-03-02
Thanks to all for their replies.  I solved the problem by upgrading to Jaunty Alpha 5 and up to now its running fine. Would rather tolerate some unstability from Ubuntu than go back to xp :)

---

