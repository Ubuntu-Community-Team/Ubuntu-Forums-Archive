---
title: "screenlet clock"
date: 2009-05-16
forum: New to Ubuntu
---

### Post by DarinB on 2009-05-16
i just discovered the screenlet clock
how do i make it appear automatically on my desktop each time i boot? instead of having to start it

---

### Post by rustutzman on 2009-05-16
In the screenlet app look at the lower left corner. You should see "All Screenlets" and checkboxes for "Start/Stop" and "Autostart at login". Check them both.

Russ

---

### Post by ninjapirate89 on 2009-05-16
Open screenlet manager and click on the clock icon. Then, while you have the clock icon selected, on the left side check the box labeled Auto Start on Login.

Edit-> Beat to it.

---

### Post by DarinB on 2009-05-16
argh now i have two clocks one on the left and one on the right. help i tried deleting the .screenlet file and app the reinstalling no fix, not hard i just want one clock at log in that stays on desktop and is covered by my windows when i open an app

---

### Post by DarinB on 2009-05-16
to be painfully honest sometimes loving Ubuntu is a love hate relationship.
i finally figured out how to solve my multiple clock thing i found a clear config file in the screenlet app.
so then i started over made sure the clock was picked and auto load at log in and treat as widget and below apps. also no screenlet on tray so i think for now i have my stupid clock. wow what a waste of an hour or more. so if any one is trying to figure out this program for gnome it is really just trial and  error and a few reboots to see if one or two clocks come up. and if you are unlucky maybe even three or four depending on how many you added by mistake........ :op

---

### Post by lovinglinux on 2009-05-16
> **DarinB said:**
> to be painfully honest sometimes loving Ubuntu is a love hate relationship.
i finally figured out how to solve my multiple clock thing i found a clear config file in the screenlet app.
so then i started over made sure the clock was picked and auto load at log in and treat as widget and below apps. also no screenlet on tray so i think for now i have my stupid clock. wow what a waste of an hour or more. so if any one is trying to figure out this program for gnome it is really just trial and  error and a few reboots to see if one or two clocks come up. and if you are unlucky maybe even three or four depending on how many you added by mistake........ :op

When you select a screenlet and click the "Launch/Add" button it will add a new instance (copy) of the screenlet selected, so you can have multiple screenlets of the same type on the screen. This is not particularly useful for a clock, but it is for other types like the disk usage. 

When you click the reset button, it will clear all configuration for that particular screenlet type, including all instances (copies) of it. While this is useful, sometimes you might want to delete only one instance instead of resetting the screenlet configuration, so you don't loose the settings for the copy you want to keep. To do that, right-click on the instance (copy) you want to remove and click "Delete this screenlet", this will remove the copy, but will preserve the settings for the remaining instances of that screenlet type. So, don't click the "Launch/Add" button if you don't want more copies of it.

---

