---
title: "Can connect to local unsecured Access Point, but not to my own WPA"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by AndyCinDallas on 2007-06-24
Wireless has been working flawlessly using Fesity Fawn with my D-link Airplus DWL-G650 and Linksys WRT54G router while using WEP.

I changed the router to WPA this morning (due to noticing someone else connected to my router - WEP is definitely not secure) and was able to connect the first time quite easily by clicking on "Make a new connection" and setting it up - so WPA itself is not a problem.

Once I rebooted, this option disappeared - if I click on the networking icon now in the system-tray, all I get is the "Manual Configuration" - which doesn't allow me to enter any WPA-type settings, only WEP. I'm currently connected to some poor bugger's local unsecured AP just so I can get online and type this (and feeling pretty bad about it, too), but I'm desperate to get this resolved.

---

### Post by AndyCinDallas on 2007-06-24
I just discovered something - I set it to "roaming mode" and suddenly I can put in the parameters and connect back onto my own wireless AP - yay.

Now, how do I save this as the default? Each time previously when I rebooted, I was prompted to enter a keyring manager key, whatever that is. Any idea how to get that back (the help-file for the keyring-manager is blank)?

---

### Post by p_quarles on 2007-06-24
The keyring manager stores your WPA key. It allows you to use a good, long key that you can't remember, and call it up by entering your keyring password (which can be the same as your user pw). It should have prompted you to make a keyring password when you first connected to your wireless router.

---

### Post by AndyCinDallas on 2007-06-24
Ahhhh, got it - it's now working, thanks so much! :)

---

