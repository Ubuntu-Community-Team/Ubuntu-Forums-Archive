---
title: "cannot find USB device"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by Michael1122 on 2009-04-24
I have loaded in ubuntu and I cannot find my USB port.  I have put in a USB with things that I kept from my old system, but it does not come up anywhere on my desktop.

Can someone assist?

Thanks

---

### Post by Michaelg14 on 2009-04-24
I noticed on mine that the usb drives are not showing up until I plug in another usb memory stick then they all come up at once.

---

### Post by anewguy on 2009-04-25
You might also try this in a terminal window, with the device plugged in:

sudo lsusb


If the device does show in the output, then the problem lies with the permissions when the usb device is mounted.  These are not the permissions on a file per se, but rather they are set via .rules files in the /etc/udev/rules folder.  They changed the way these things were handled and the syntax when 8.04 came out, and it was carried forward into 8.10.  I can only assume they were carried forward in 9.04 as well.  If your device does show in the output above, post back and we can work on it.

Dave :)

---

### Post by llamabr on 2009-04-25
You can also check dmesg when you plug it in.  If there's some error, you'll see it there.  If not, you'll see where the device is located.

---

### Post by Michaelg14 on 2009-04-25
I have two usb hard drives that are showing up in lsusb but are not recognized by the system until I plug in another flash stick.  Then they all show up.

---

### Post by Michael1122 on 2009-04-25
Sorry i am really new when it comes to finding these files.  Where would i look for them?

---

### Post by lovelyvik293 on 2009-04-25
Which files you are talking about?
With dmesg(display message) you get the diagnostic message when a driver is loaded.

---

### Post by anewguy on 2009-04-25
Both the sudo lsusb and the dmesg are command line commands.  To get to the command line, do the following:

- click on Applications on the top menu bar (should be on the left side of it)

- a drop-down menu appears - click on Accessories

- another drop-down menu appears - move your mouse over and down to Terminal and click

This brings up a terminal window where you can enter the commands.  The sudo lsusb will ask for a password - just type in your normal password and press enter.

Remember that after the sudo lsusb and also after the dmesg you must press the enter key of nothing will happen.

Hope that clarifies it a little for you.  If not, just post back and we'll go from there.

Dave :)

---

### Post by Michael1122 on 2009-04-25
i got on to dmesg but I have no idea what it says or where I am suppose to find the usb port.

I tried getting on the other through sudo but I do not get anywhere on that.

Can you let me know where I am suppose to find USB on the dmesg?

---

### Post by Michael1122 on 2009-04-25
when i type in sudo lsusb(I am guessing that is an L and not a one.  It just comes back to the root@micjhael-desktop function.  It does not show anything else.

Am I not finding the usb when I do that?

---

### Post by anewguy on 2009-04-25
The lsusb (yep -it's an "L" and an "S" for "list" - should just output something to your window.  Be sure the device is plugged in first, then try again as follows:

lsusb <press enter>

then

sudo lsusb <press enter>

I do know that the permissions problem has carried forward, as I have to run as superuser to see me cameras until I put the permissions file back in /etc/udev/rules.d  .

Post back what, if anything, you get back.

Dave :)

---

