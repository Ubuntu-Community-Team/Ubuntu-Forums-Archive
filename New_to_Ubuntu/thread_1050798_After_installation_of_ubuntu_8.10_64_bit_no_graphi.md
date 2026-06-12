---
title: "After installation of ubuntu 8.10 64 bit no graphical user interface"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by Julchen on 2009-01-26
Hi,
I first tried to install ubuntu 8.10 32bit on my laptop. I didn't get any error messages during the installation, but when I tried to reboot it, the booting got stuck after 2.5 boxes of the loading bar. Then I tried to install the 64 bit version. That went fine, I could boot and log on to the terminals. But when I wanted to switch to the graphical user interface the monitor was just black.
It's an Acer Travelmate 5730g-944g32n
Intel core duo T9400 Montevina 2.53 Ghz, 3mb cache
ATI Mobility Radeon™ HD 3650
Hope you can help me.
Julchen

---

### Post by HuaiDan on 2009-01-26
Do you have a command prompt?
If not, hit alt-f2
If so, type
sudo /etc/init.d/gdm start
then your password.
gdm stop is a command you can use to stop your gui, like when you're switching nvidia drivers and such.


Hope it helps.

---

### Post by Julchen on 2009-01-26
Unfortunately not. It tells me "Starting GNOME Display manager ... ok" but it doesn't change anything.
What else could the problem be?
Julchen

---

