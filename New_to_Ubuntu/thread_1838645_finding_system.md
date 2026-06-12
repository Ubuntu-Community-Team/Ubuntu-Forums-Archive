---
title: "finding system"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by racoffey63 on 2011-09-04
I'm trying to enable proprietary drivers and I can't find the system button.  it's almost as bad as not finding the on switch

---

### Post by 3rdalbum on 2011-09-04
It's literally in the top-right corner of the screen. It looks like an on/off switch. Click it and click System Settings... and then you'll find the Additional Drivers program within that.

---

### Post by racoffey63 on 2011-09-04
so the system>admin>additional drivers is just a ruse.  It's the same as the additional programs>additional drivers?

---

### Post by 3rdalbum on 2011-09-04
> **racoffey63 said:**
> so the system>admin>additional drivers is just a ruse.  It's the same as the additional programs>additional drivers?

Yes. People who are still using the old Gnome user interface would go to System > Administration > Additional Drivers, people using the new Unity interface use my method or go to the Applications button/lense and start typing "additional", then click on the Additional Drivers button when it appears.

---

### Post by PatrickD-52761 on 2011-09-04
> **racoffey63 said:**
> so the system>admin>additional drivers is just a ruse.  It's the same as the additional programs>additional drivers?

Well, yes and no. If you're on Ubuntu 11.04 or 11.10, the screen looks different from whatever version the directions were created for. In previous versions of Ubuntu, you had three menu items at the top left side of the screen (Applications, Places, and System). Under System, you had Preferences and Administration.

With Ubuntu 11.04 (Unity), you have the Applications menu item on the left-sidebar (little magnifying glass with a + in it), which allows you to search or scroll through all of the menu options that were divided into the three earlier menus; and the System Settings option under the power button (as mentioned by 3rdalbum).

If you click on the Applications button, and then click on "Refine Search" you can mimic the old functionality of the three menus by choosing a checkbox.  So, for example, since your looking for something in the "System" menu, you'd click the "System" Checkbox, and it will show you only those menu items which would be under "System > Administration" or "System > Preferences" in the older versions.

Also in your case, you may need to enable the restricted extras in the repository (Software Sources, or if you have Synaptic Package Manager open, click the "Settings" button or the "Repositories" menu option under Settings, and enable the Restricted Extras repository.).

Hope this clears things up a bit more, and have a great weekend :)
Patrick.

---

### Post by racoffey63 on 2011-09-04
Thank you to both of you.  That clears up most of it.  now if it's ok to do without starting a new thread, here is why I was looking.

I have a toshiba with an expresscard slot and a usb 3.0 card and rs-232 serial port cart to go in it, but the cards are not being recognized.  I'm figuring it's a drives problem.  although [I]'m not sure if it's the express slot drivers the card drivers or I just am not hitting the on switch for it.

Do you have any idea or input?

I think my machine might be recognizing it as a fingerprint reader.
[/I]

---

### Post by Mark Phelps on 2011-09-04
The "Additional Drivers" options is NOT going to find those drivers for you.  That option is basically for video drivers and LAN drivers.

---

