---
title: "KDE apps think they're not connected"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by Tomkin on 2008-03-24
I posted this in Desktop Environments, but it seems to apply here as well.

I recently switched my primary computer to an old Thinkpad T42 (ironically, still works much better than my previous primary), and installed Kubuntu 7.10 on it. Every single piece of hardware, including wireless, works out of the box, but for some reason KDE applications will not connect to the Internet via wireless at all. When I try to check my e-mail with KMail it will instantly say "transmission complete, no new messages"; when I check RSS with Akregator it acts as though there are no new feeds; and Konqueror immediately gives me a "cannot connect to the server" error. However, Adept and non-KDE apps (i.e. Firefox, ping) are connecting fine, and everything connects via wired. I have a feeling that I'm using some nonstandard part of the KDE wireless packages that's causing this (wlassistant?), but I don't know which one, or what to do once I find out...

If you have any idea what's going wrong (or even what isn't), please say so! It's a rather crippling problem on an otherwise perfect setup!

Thanks,
 - Tomkin

---

### Post by xywa on 2008-05-02
I have got the same problem with my Kubuntu.
Kmail do not fetch emails - Transmission complete. No new messages
Sending works fine.
It used to work fine for 2 years, the probem happend after updating Kubuntu.

Any sollution?

THX

---

### Post by stephanallemon on 2008-06-22
Had the same problem after upgrading to Hardy. It is linked to the wireless interface. After some research, I installed the wlassistant, rebooted and it works now.

Update -> installing wlassistant is not the real trick. In fact KDE apps (konqueror, kontact, ...) don't see the wireless i/f after a hibernate. Hence the need to reboot. Any suggestions to fix this?

Update 2 -> fixed by adding "networking" to the STOP_SERVICES= line in /etc/default/acpi-support

Stéphan

---

