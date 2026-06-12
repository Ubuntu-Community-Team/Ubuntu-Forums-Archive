---
title: "Getting serial port to work in vbox with Ubuntu 8.10"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by bhoth on 2009-02-20
Hi All,

I have done several searches on this and nothing seems to be helping me get the serial port working in VirtualBox 2.1.4. I have followed the instructions in the vbox users manual. I have made sure my user name is in the dialup group.

I don't get any errors when starting my winxp pro guest.

Anything else to try?

Thanks,

---

### Post by Odemia on 2009-03-23
Incase you haven't already figured it out:
You should start by testing that the port is working in Ubuntu.  Short pin 2 and 3 on the serial port and open gtkterm, minicom or another terminal of your choice.  if you can see what you are typing into gtkterm (or other) while the local echo is off the port is working.

Then toget the vbox/windowsconfig right see the link below.  In my experience you have to use Control Panel>System>Device Manager and pretty well force windows into using the correct COM device.  But there is better discussion in the link below.
[http://ubuntuforums.org/showthread.php?t=1012153](http://ubuntuforums.org/showthread.php?t=1012153)

---

