---
title: "[SOLVED] Broadcom Wireless was working, turned off?"
date: 2007-11-20
forum: Networking &amp; Wireless
---

### Post by mikeycantoon on 2007-11-20
HI, I just installed Ubuntu 7.10
I have a broadcom wireless card in my Compaq R3000 (Pentium Edition)
I went into Restricted Drivers and found the card listed, I enabled the firmware, it downloaded what I needed it to and my wireless card came to life.  I could even turn it on and off using the Button on the front of the case.

Well, I later turned off the laptop and didn't use it for the weekend and after I booted back up into linux my wireless wouldn't turn on using the button.  I did an "ifconfig -a" and it wasn't listed at all, just my ethernet card came up.

I went back into restricted drivers and disabled the firmware, restarted, re-enabled it dowloading the firmware from the internet using a wired connection and poof it's back on and controllable again.  And I'm typing this message using it right now. 

My main question is, what can I do to bring the card back up when it does that instead of having the remove and reinstall the firmware?

-Mikey

---

### Post by banewman on 2007-11-20
See if this link helps -
[http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)
:)

---

### Post by mikeycantoon on 2007-11-20
Whoa, that's a lot of info, and I didn't use ndiswrapper.  I'm a linux noob.  I'm a network engineer in windows but totally new at linux.

-Mikey

---

### Post by banewman on 2007-11-20
I thought lines 5 - 6 - 7 would be what you might need :)

---

### Post by mikeycantoon on 2007-11-20
If you mean lines 5-6-7 from the first post, when I went there my card wasn't listed there, or in ifconfig.  After I redid the firmware stuff it's there, but when it didn't come on after a cold boot it wasn't there.

-Mikey

---

### Post by Ayuthia on 2007-11-20
You might try adding bcm43xx to the list in /etc/modules.  That should load the driver when the OS starts up.

---

### Post by mikeycantoon on 2007-11-20
Um....how do I do that?  Whatever linux does when I enable the firmware in the restricted drivers window it activates the card.  Is there a command or something?

-Mikey

---

### Post by mikeycantoon on 2007-11-20
Okay I did a "sudo lshw -C Network" command and here
*-network:0 UNCLAIMED

This is for my wireless NIC only.  Can someone tell me what that means?

It will still come on if I remove the firmware in "Restricted Drivers" and then re-enable it.  But if I do a restart or cold boot, my wireless card doesn't come back on.  But when I check the "Restricted Drivers" Section it shows the firmware as "IN USE"??  There must be a command to get this sucker to kick back on.  If I need to provide more information, just tell me what you need.

-MIkey

---

### Post by mikeycantoon on 2007-11-20
I found the answer by accident.

By running the command "sudo modprobe bcm43xx" it kicked it back on.

Is there a way I can make this work everytime  it boots so I don't have to type it in everytime?

-Mikey

---

### Post by kevdog on 2007-11-20
echo bcm43xx | sudo tee -a /etc/modules

---

### Post by mikeycantoon on 2007-11-20
Thanx dude.  Where do I enter that line of code in the system?

-Mikey

---

### Post by Ayuthia on 2007-11-20
Just open a terminal window and type it in there.

---

### Post by mikeycantoon on 2007-11-20
Okay I typed that code in and this is what I got:

mikeycantoon@mikeycantoon-laptop:~$ echo bcm43xx | sudo tee -a/etc/modules
[sudo] password for mikeycantoon:
tee: invalid option -- /
Try `tee --help' for more information.

What am I doing wrong?

-MIkey

---

### Post by mikeycantoon on 2007-11-21
I got it, I did a copy and paste from your post and I see how I typed it wrong.  Thanks a lot for all your help guys, much appreciated.

-Mikey

---

