---
title: "Previously saved session keeps coming back to haunt me"
date: 2009-06-16
forum: New to Ubuntu
---

### Post by taber on 2009-06-16
I'm running Ubuntu 9.04, and I'm having problems with the functions in the Startup Applications Preferences dialog. I unchecked "Automatically remember running applications when logging out," and yet after logging out and logging in and restarting the computer entirely, Ubuntu still automatically opens the apps I had running the last time that box was checked every time I log in.

I checked the applications that are starting up (Pidgin, Firefox, Evolution, a terminal window), and none of them have a "Start at login" or similar config option that I've inadvertently enabled. Another thread suggested deleting ~/.gnome2/session**, **did that, no help.

How can I put this zombie session to bed?

---

### Post by Cheesemill on 2009-06-16
I think this is the answer you're looking for:

1 - Check the 'Automatically remember running applications when logging out' box.
2 - Close down all applications and then restart your machine.
3 - Uncheck the 'Automatically remember running applications when logging out' box and restart.

You should now be OK

---

### Post by billgoldberg on 2009-06-16
> **taber said:**
> I'm running Ubuntu 9.04, and I'm having problems with the functions in the Startup Applications Preferences dialog. I unchecked "Automatically remember running applications when logging out," and yet after logging out and logging in and restarting the computer entirely, Ubuntu still automatically opens the apps I had running the last time that box was checked every time I log in.

I checked the applications that are starting up (Pidgin, Firefox, Evolution, a terminal window), and none of them have a "Start at login" or similar config option that I've inadvertently enabled. Another thread suggested deleting ~/.gnome2/session**, **did that, no help.

How can I put this zombie session to bed?

File a bug report on launchpad.

---

### Post by penguin-power on 2009-06-16
close all apps, then check "remember" all apps. 

reboot.

after reboot, then uncheck "remember" all apps.

worked for me a while ago, never did it since.

hope this helps.

w

---

### Post by taber on 2009-06-16
> **Cheesemill said:**
> I think this is the answer you're looking for:

1 - Check the 'Automatically remember running applications when logging out' box.
2 - Close down all applications and then restart your machine.
3 - Uncheck the 'Automatically remember running applications when logging out' box and restart.

You should now be OK

This worked for killing the old session. Thanks a bunch!

As for the bug report, I found this one on Launchpad [https://bugs.launchpad.net/ubuntu/+bug/364023](https://bugs.launchpad.net/ubuntu/+bug/364023) and added a comment that I'd experienced the same issue.

---

### Post by Cheesemill on 2009-06-16
The bug is that when you uncheck the 'Automatically remember running applications when logging out' button it just stops updating the saved session data without actually clearing it. This is why the above steps are necessary.

---

### Post by cdaaawg on 2009-12-09
I had encountered the same problem and this solution worked for me. Thanks Cheesemill for the solution; [http://ubuntuforums.org/showpost.php?p=7466192&postcount=2](http://ubuntuforums.org/showpost.php?p=7466192&postcount=2). 

However, I would like to know where this setting is stored so I can use gconftool or any other terminal based method to script a solution. Thanks for any and all input to a scriptable workaround for this bug.

---

