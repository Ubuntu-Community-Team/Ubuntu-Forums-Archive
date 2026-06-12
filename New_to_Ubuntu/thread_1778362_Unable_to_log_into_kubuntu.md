---
title: "Unable to log into kubuntu"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by Tobey666 on 2011-06-08
Hi all,  I need your help.

I just installed kubuntu on my computer today (I wanted a change from unity for a while) however, after installation, when I tried to log in I received the following message:
> 
kstartupconfig4 does not exist or failed. The error code is 3. Check your installation

I've tried for the past hour to find something related to this, and while I've found many people with the same problem, none of them seems to be very recent and I haven't had any luck following their suggested solutions.

Any suggestions or help would be much appreciated.

Thank you.

---

### Post by ubudog on 2011-06-08
Hi!

Whenever that error pops up, press CTL>ALT>F1 and log in using your username and password.

Type the following.  There appears to be a permissions issue...
```
sudo chown -R username.username /home/username/.kde
```

*username = your username :-)

The thread I got this from may have some other useful information for you:
[http://ubuntuforums.org/showthread.php?t=1167436](http://ubuntuforums.org/showthread.php?t=1167436)

Let me know how it goes!  :-)

---

### Post by Tobey666 on 2011-06-09
> 
Whenever that error pops up, press CTL>ALT>F1 and log in using your username and password.


Thank you so much, that was the piece of information that I didn't have before.  Looks like things are working now.

---

### Post by ubudog on 2011-06-09
No problem, glad you got it working!  :-)

---

