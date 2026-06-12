---
title: "Laptop Keyboard not working....."
date: 2011-08-06
forum: New to Ubuntu
---

### Post by dunbrokin on 2011-08-06
My wife was trying to set up wireless keyboard and big screen on her lap top....Her lap top keyboard is USA configured but (as she is back in the UK at the moment) the keyboard she bought is UK configured.....In trying to set it up, she seems to have disabled the onboard keyboard....well for normal log in anyway. The log in screen will not take the passowrd...nor will it work with on-screen keyboard. However, we can get in in recovery mode, repair files, startx etc.....but under that option I am not sure where to look or what to tell her to do (I have to talk her through it over the phone...aaarrgghhh!!!). I have tried rebooting umpteen times but nothing works. I cannot change the login screen in recovery mode! Help!. she is at the start of a 4 week stint looking after her aged mother and has loads of work to do.....Any suggestions really really appreciated.

---

### Post by grahammechanical on 2011-08-06
As a wild guess I would say that the differences between a US keyboard and a UK keyboard are somehow reflected in the password. Her password is coming out differently on the UK keyboard. If she can get into the OS she can use the keyboard utility Layout tab to create a US layout for that UK keyboard and try to change her password to something that will work on both a UK and a US keyboard.

Did she disable the onboard keyboard in the BIOS?

Regards.

---

### Post by dunbrokin on 2011-08-06
> **grahammechanical said:**
> As a wild guess I would say that the differences between a US keyboard and a UK keyboard are somehow reflected in the password. Her password is coming out differently on the UK keyboard. If she can get into the OS she can use the keyboard utility Layout tab to create a US layout for that UK keyboard and try to change her password to something that will work on both a UK and a US keyboard.

Did she disable the onboard keyboard in the BIOS?

Regards.

No she would not know how to disable the onboard key board and anyway it works in the recovery mode....I am ignoring the UK keyboard for now...if we can get back to the onboard USA keyboard and get that to work then she can at least log in and get on the net...she cannot get on the net in the recovery mode, though the onboard keyboard works....aaarrrgghhhh!

---

### Post by dunbrokin on 2011-08-06
Bump

---

### Post by dunbrokin on 2011-08-06
Just a thought....how do I change the log in screen in the recovery mode so that she logs in automatically in normal mode. I tried System/Administration/Login ..but it will not unlock and so I cannot get the GUI to work to change things.

---

### Post by dunbrokin on 2011-08-06
I am thinking that this may be the answer....I hope!


[http://ubuntuforums.org/showthread.php?t=14835](http://ubuntuforums.org/showthread.php?t=14835)

---

### Post by dunbrokin on 2011-08-07
Right, that was a wasted effort.....anybody know how to log in by not using the GUI log in screen.....I have deleted the .gnome2 file in recovery mode but that made no difference. I tried plugging in a USB drive in recovery mode but that was not recognised....so, now, we are stuck with a HP PC that does not have a CD drive...so we cannot boot from a CD. We cannot access the files in normal mode because we cannot log in. We can access the files in recovery mode but we cannot copy them on to a USB drive.....Nobody in the community seems to have any ideas on what to do....Does computing really have to be this hard?

---

### Post by dunbrokin on 2011-08-07
If I go to /etc/shadow and find the user name and then delete the hashed password between the two colons, will that allow her to log in without a password?

---

### Post by dunbrokin on 2011-08-07
I did not touch the /etc/shadow. But I got her to set up a new account from the recovery boot. I set up abc with a password of 12345....but again the same problem when she tried to log in...the password box will not accept the password.

I tried changing /etc/init/gdm.conf to /etc/init/gdm.disabled

she could not get in with that either.

In recovery mode I tried to use Tweak to change the log in screen...but log in screen not shown on Tweak.

I am very quickly running out of ideas....

How can I log in from a terminal that is not in the recovery mode?

---

