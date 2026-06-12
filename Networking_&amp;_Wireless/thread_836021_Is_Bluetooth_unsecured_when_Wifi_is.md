---
title: "Is Bluetooth unsecured when Wifi is?"
date: 2008-06-21
forum: Networking &amp; Wireless
---

### Post by Udibuntu on 2008-06-21
Hi Guys,

I'm using a Thinkpad R60e with a wireless killswitch. On it 7.04.

I'm connected with WEP encryption to a wireless router, only wifi, no BT.

Last night I saw that I have both wifi and BT lights on.

Can someone log on to my computer via BT, even if wifi is secured?

How can I see the BT activity, devices on Feisty?

How can I use Firestarter to block this kind of breach?

Thank you for your help!

Udi

PS - can someone tell me if Firestarter is on when the icon disappears?

---

### Post by rudihawk on 2008-06-21
Even if your Wi-fi connection is secured your bluetooth connection will remain unsecured as bluetooth is inherently insecure. However most bluetooth devices have a range of +-10m so if you are at home i doubt it will be problem.

As for your question about firestarter I am not sure.

---

### Post by Udibuntu on 2008-06-21
Thanks Rudi.

I live in an appartment building, so 10 meters is a range where some BT devices can be found, especialy cellphones.

Can a BT device connect to my lappy without me knowing about it?

I'm opening a new thread on Bluetooth setting control.

---

### Post by Kevbert on 2008-06-21
Bluetooth is inherently unsecure.  The only things you can set is allowed services (turn off all until you need them) and under the General tab deselect 'Automatically authorise incoming requests'.  These should suffice in most cases.  An open connection would allow complete access to all mounted drives.

---

### Post by Udibuntu on 2008-06-21
> **Kevbert said:**
>  The only things you can set is allowed services (turn off all until you need them) and under the General tab deselect 'Automatically authorise incoming requests'.  These should suffice in most cases.  

Thanks Kev.

1) where can i find the menu for those allowed services?
2) in what cases this method is not sufficient to block BT connection?
3) can't firestarter deal with incoming requests? (should i turn to security forum for that one?)

Udi

---

### Post by Kevbert on 2008-06-21
You should find Bluetooth under System - Preferences - Bluetooth Preferences.

---

### Post by Udibuntu on 2008-06-21
> **Kevbert said:**
> You should find Bluetooth under System - Preferences - Bluetooth Preferences.

Nope..no BT preferences there, nor anywhere else for that matter...

---

### Post by Kevbert on 2008-06-22
It may be that you have a missing program (that may not be installed by default).  Via Synaptic I have the following packages installed: bluetooth, bluez-gnome, bluez-utils, gnome-bluetooth, gnome-vfs-obexftp.  One of these gives you the options.

---

### Post by Udibuntu on 2008-06-22
I'll give it a shot, thanks!

---

