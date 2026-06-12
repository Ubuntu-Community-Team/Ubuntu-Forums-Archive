---
title: "Wireless device disabled?"
date: 2010-03-25
forum: New to Ubuntu
---

### Post by mes0 on 2010-03-25
Need help with wireless device. I'm using an ASUS K60IJ and just installed ubuntu from a live disk...sudo lshw command, device came up as disabled. I haven't found a way to enable it without reinstalling windows, any suggestions?

---

### Post by J_Stanton on 2010-03-25
did you check system-administration-hardware drivers?

---

### Post by laidback on 2010-03-25
This maybe helpful:-

Look in Systems>Preferences>Network connections. Highlight the Wireless Option, choose Edit, you'll need your own password, check that Connect Automatically is checked. You might also have a look at the other settings whilst you're there. Note "Available to all users" check box at the bottom of the screen.

---

### Post by mes0 on 2010-03-25
system/administration/hardware drivers says 'no proprietary drivers are in use on this sytem'



and wireless tab does not allow you to click the 'edit' option

---

### Post by admiralspark on 2010-03-25
well, simple solution MIGHT be this:
Type ```
ifconfig
``` into a terminal. It will report all internet-capable hardware. Figure out which one is your wireless router and then type ```
sudo ifconfig WhichEverCardYoursIs up
``` in example: ```
sudo ifconfig wlan0 up
``` will start my wireless LAN. Your's might be ath0, wlan0, eth1, any number of things.

If you don't see the wireless card after typing in ifconfig, try typing iwconfig to see if the system recognises it. Report back here your results either way ;)

---

### Post by mes0 on 2010-03-25
typing iwconfig brings up the message "no wireless etensions"
I need to figure out how to enable the wireless card itself.

---

### Post by anewguy on 2010-03-25
Let's start first with what type of wireless we are talking about:

type the following in a terminal window and post the output back here:

lspci <press enter>

If using a USB adapter or if a laptop:

lsusb <press enter>

Once we see that we can be in a far better position to try to help.

Dave :)

---

