---
title: "Disabling Mouse Pad on Easy Peasy 1.0"
date: 2009-01-31
forum: New to Ubuntu
---

### Post by remontello on 2009-01-31
Running Easy Peasy 1.0 with Remix interface on a Eee PC 1000 and wish to disable the mouse pad while typing on the keyboard and also disabling mouse pad tapping.  I might be happy if I could just alter the sensitivity of the mouse pad.  Others seem bothered by this but I have not seen a solution that works!
Thanks

---

### Post by ugm6hr on 2009-01-31
This is a standard Ubuntu feature with syndaemon - assuming Easy Peasy has "SHMConfig" activated, it should work:
[http://mydellmini.com/forum/ignoring-trackpad-while-typing-t747.html#p22782](http://mydellmini.com/forum/ignoring-trackpad-while-typing-t747.html#p22782)

gsynaptics (in repo) might have the necessary sensitivity setting (I can't remember) - else you can edit xorg.conf manually to change sensitivity.  I have a reference for that - I'll look it up if the syndaemon trick isn't enough.

---

### Post by remontello on 2009-01-31
I am still unsuccessful in disabling touch pad!
I tried running:
**sudo syndaemon -t 1 -d -t -K**
but got in response:
**Can't access shared memory area. SHMConfig disabled?**

I found a way to enable SHMConfig by creating a file:
/etc/hal/fdi/policy/shmconfig.fdi

with the following lines in it:
[B]<?xml version="1.0" encoding="ISO-8859-1"?>
<deviceinfo version="0.2">
 <device>
  <match key="input.x11_driver" string="synaptics">
   <merge key="input.x11_options.SHMConfig" type="string">True</merge>
  </match>
 </device>
</deviceinfo>[/B]

The file did not exist before.  But still the syndeamon gave me the same response.

There seems to be a way of using synclient, however that also requires having SHMConfig set to true.

Finally there is some info on HAL but it not detailed enough for me to follow.  Furthermore, I am not sure whether it is a synaptic mousepad or something else.

I am wondering if running the remix front-end is causing some of the problems.  I would prefer to run the standard gnome gui since that's what my manuals cover.  In any case, I am not sure how to setup a switchable interface!

What do you think?

---

### Post by ugm6hr on 2009-02-01
OK.

Enabling SHMConfig is a bit trickier with 8.10 (which is presumably what Easy Peasy is based on).  The main reference I have found: [https://help.ubuntu.com/community/SynapticsTouchpad](https://help.ubuntu.com/community/SynapticsTouchpad)
Also: [http://www.samlesher.com/ubuntu/enable-shmconfig-for-synaptics-touchpad-on-ubuntu-intrepid-ibex-810/](http://www.samlesher.com/ubuntu/enable-shmconfig-for-synaptics-touchpad-on-ubuntu-intrepid-ibex-810/)

I would suggest trying "True", "true", "On", "on" and "1" to replace "Term" here:
 <merge key="input.x11_options.SHMConfig" type="string">True</merge>

Hopefully, one of those will work.  I use "true".

And syndaemon does not need sudo privileges.

---

### Post by remontello on 2009-02-01
Thanks for your help but these ideas don't work.  However at least this file allready exist:

/usr/share/hal/fdi/policy/20thirdparty/11-x11-synaptics.fdi

The other file references did not!

So I think it is the hal option that might eventually work.  I did install gsynaptics and then got a trackpad option on Preferences.  However when I click it, it too says that SHMConfig is not set to true.  Anyway perhaps gsynaptics is not needed with 8.10 (or does not work) which I believe Easy Peasy 1.0 is based on.

I do wonder if the netbook remix interface is part of the confusion.  The reference books I have describe only the standard gnome desktop which seems to have additional options to what remix displays.  Perhaps I am better off to buy a mouse and ignore the mousepad until I have learned more about Ubuntu.  I would like to switch desktops to full gnome however.  Can you point me in that direction?
Russ

---

### Post by ugm6hr on 2009-02-01
If it is similar to the Dell Netbook remix, you should have an option in the menu:
System -> Prefs -> switch Desktop mode

---

### Post by remontello on 2009-02-01
No such luck.  There is no such option within the so called netbook remix desktop.  There is an option at login that allows a "Change Session".  Two of the options are "1 Run Xclient Script" and "2 GNOME", but neither changes the desktop interface from the remix look.

---

### Post by theozzlives on 2009-02-01
under System > Preferences > Mouse you can disable clicking on the touchpad.

---

### Post by remontello on 2009-02-01
No such options are available on my system.  I have read that some folks have a tab on the mouse option and perhaps that is where you have seen it.  I have no such tab.  For now, I have installed something call eee-control that does several nice things but also lets me disable/enable the mousepad with a hot key.  Not the best solution, but avoids the cursor moving around while I am typing into gedit.

---

