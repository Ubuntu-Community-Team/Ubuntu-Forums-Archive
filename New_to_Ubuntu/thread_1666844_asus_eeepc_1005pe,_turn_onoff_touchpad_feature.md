---
title: "asus eeepc 1005pe, turn on/off touchpad feature"
date: 2011-01-14
forum: New to Ubuntu
---

### Post by dumble on 2011-01-14
Netbook: asus eeepc 1005pe
OS: ubuntu 10.10 desktop edition

The function key fn-F3 to turn of the touchpad while typing is not working out of the box. This is really usefull (as the netbook is so small and you hit the touchpad when you type long emails or something)

How do I enable this function key? 

(almost all of the other fn-keys are working properly btw)

---

### Post by d3ngar on 2011-01-14
Chances are that the key command is not recognised by Ubuntu and, if this is really important you, you should file a bug-report to launchpad.

Here is where you should start: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)

The problem you describe can be solved: Go to System > Preferences > Mouse > Touchpad and check 'Disable touchpad while typing' and 'Enable mouse clicks with touchpad'

---

### Post by dumble on 2011-01-14
yeah sure its not detected, but I need the work-around to get it to work properly.. anyway ill file in the bug-report

(It was not working in the netbook version either.. )

---

### Post by laz777 on 2011-01-14
I have an 1005HA, ths worked for me:
[http://www.webupd8.org/2010/12/jupiter-0046-released-with-sata-link.html#more](http://www.webupd8.org/2010/12/jupiter-0046-released-with-sata-link.html#more)

---

### Post by dumble on 2011-01-15
he laz777

I installed it, but what are the key-combinations? What is the key-combination to turn on/off the touchpad for example? I can turn it off with my touchpad, but then I need to put in a USB mouse to turn ON my touchpad again.. not really usefull..

---

### Post by dumble on 2011-01-15
I found some information, but I dont really understand what to do. 
[http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Keybindings](http://sourceforge.net/apps/mediawiki/jupiter/index.php?title=Keybindings)

Can someone tell me in simple steps how to make the keybinding like this:
fn - F3

to turn on/off touchpad

---

### Post by laz777 on 2011-01-15
Duh! I forgot that I had to add a line in Grub.
acpi_osi="Linux"
to do this open a terminal and type:[FONT=Verdana]
[/FONT]```
sudo gedit /etc/default/grub
```change this line
 GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

to look like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi_osi=Linux"

save and exit, then back in the termnal type:
```
sudo update-grub
```then reboot, voila!

---

