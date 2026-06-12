---
title: "After messing with compiz config manager...Cant boot"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by human151 on 2009-01-18
hello.  I am pretty new to linux/ubuntu.  Now that that is out ofg the way, I have a problem.   I have a Lenovo Idea Pad S10 with XP and and an ubuntu partition.  I was messing around with compiz config setting manager and when I checked the button for "Negative" in the Accessibility section someting happened....something very bad indeed.

The screen was having some issues.  It seemed aas if it could no  longer display what what was onscreen.  Then I got kicked out to the logon screen where I enter my username and password.  Each time I try to logon on I get kicked back to this screen.

I can only open to the terminal now...and I obviously do not know how to fix it from there.

I need your help peoples....please.

Help me ubuntu community...your my only hope.

Thanks!!

---

### Post by PurposeOfReason on 2009-01-18
This will erase all your compiz settings but it should work just fine.
```
rm ~/.config/compiz/compizconfig/Default.ini
```
If you want to try to save it, try this
```
nano ~/.config/compiz/compizconfig/Default.ini
```
That will open an editor. Look for this part near the end:
```
[neg]
as_window_toggle_key = <Super>n
as_screen_toggle_key = <Super>m
s0_neg_match = any
s0_exclude_match = type=Desktop
```
It should have some other options on yours about being on. Turn it off.

---

### Post by human151 on 2009-01-19
> **PurposeOfReason said:**
> This will erase all your compiz settings but it should work just fine.
```
rm ~/.config/compiz/compizconfig/Default.ini
```
If you want to try to save it, try this
```
nano ~/.config/compiz/compizconfig/Default.ini
```
That will open an editor. Look for this part near the end:
```
[neg]
as_window_toggle_key = <Super>n
as_screen_toggle_key = <Super>m
s0_neg_match = any
s0_exclude_match = type=Desktop
```
It should have some other options on yours about being on. Turn it off.

Thank you for your reply.

I tried the first command and this is what I get:

rm:cannot remove/homedirectory/...  No such file or directory

and the second command brings me to a text editor that looks like this:

GNU nano2.0.7 File:  username/.config/...







G GET HELP   O WRITE OUT    R READ FILE
X EXIT


and a few other options but I didnt see any command about turning anything off

Any other ideas?

This is a fairly new install, if its just as easy, I can just wipe ubuntu and reinstall but I am not sure how to do that.  

If I install again as I did originally will it just format the ubuntu partition or will it affect the XP Partition?  Or try to make a third partition?

Sorry...im an OS Noob ;-)

Thanks...

---

