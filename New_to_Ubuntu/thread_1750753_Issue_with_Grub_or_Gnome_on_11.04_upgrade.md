---
title: "Issue with Grub or Gnome on 11.04 upgrade"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by urug01 on 2011-05-05
I upgraded my desktop from 10.10 to 11.04 earlier in the week.  Upon the initial login, I was given a message that my system could not support the new GUI and Gnome was brought up.  I did not get a black screen as indicated by other posts, but what I ran into was a completely erratic and pretty much non-functional Gnome interface resembling a monitor refresh rate issue.  I tried booting up while holding the Shift key and ran additional updated and tried opening in various safe modes with no improvement.  However the Gnome GUI is at least funtional enough that I could logout of my primary user and into a secondary user.  When I log in as the secondary user and the Gnome safemode everything functions as normal.  However, if I try to logout of the secondary user and back to the primary user I am not presented with the option to select the Gnome or Gnome safemode.  Can anyone walk me through the commands needed to fix this issue under the primary user?  Thanks for any help on the subject.

---

### Post by garvinrick4 on 2011-05-05
If while you are in the Unity interface, try ctrl/alt/T at same time, if terminal comes up:
```
gnome-session-save --kill
```then click on login and change on bottom button to classic instead of ubuntu.
and login to classic.
Or if you cannot get to a terminal can you right click and make a launcher with that command.
name it logout and go to open in terminal in the couple of settings.

---

### Post by urug01 on 2011-05-05
I never make it to the Unity interface due to a message that indicates my system will not support Unity.  Instead I am put straight into Gnome.

---

