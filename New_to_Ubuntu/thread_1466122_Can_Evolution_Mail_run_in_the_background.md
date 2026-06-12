---
title: "Can Evolution Mail run in the background?"
date: 2010-04-30
forum: New to Ubuntu
---

### Post by thejakeman on 2010-04-30
I see that Evolution has both "Close Window" and "Quit" in the file menu, and I'd assume that the "Close Window" selection would have it hide in the background under the little mail icon in 10.04 but it doesn't seem to notify me of new emails when I tell it to just close the window and not quit, and I think that it is just terminating the process. Is there a fix for this?

Thanks in advance!

---

### Post by madjr on 2010-04-30
i havent used evolution in a while

but you can check if evolution **process** quits by looking in the **system monitor**

---

### Post by thejakeman on 2010-04-30
If I use a different email program will it still work with the neat notification system in 10.04?

---

### Post by madjr on 2010-04-30
> **thejakeman said:**
> If I use a different email program will it still work with the neat notification system in 10.04?

am not sure, which one you have in mind? they will be adding support for more

anyway, were you able to view if the evolution process was quiting in the system monitor?

---

### Post by swoll1980 on 2010-04-30
I'm pretty sure you can run any program as a daemon.

---

### Post by thejakeman on 2010-04-30
Yeah the process terminated. I'd prefer to keep it but if it can't hide then I'll switch to something else. I don't have anything in mind at the moment though.

---

### Post by thejakeman on 2010-05-06
The process does terminate. All I'm trying to do is make it so that when I do Ctrl+W (Close window) (instead of Ctrl+Q (Quit)) all it does is hide the window. Does what I'm saying make any sense?

---

### Post by eode on 2010-05-22
Yes, what you are trying to do makes sense, but Evolution doesn't do that.  :-(  It would be nice if it had a mail-checker program that would run in the background or the system tray.  I haven't gotten around to doing a feature request/bug report on launchpad.

---

### Post by Mr Coffee on 2010-08-11
> **eode said:**
> Yes, what you are trying to do makes sense, but Evolution doesn't do that.  :-(  It would be nice if it had a mail-checker program that would run in the background or the system tray.  I haven't gotten around to doing a feature request/bug report on launchpad.

Sorry, old and stuff but you can use [**alltray**]("apt:alltray") for that.

---

### Post by jtarin on 2010-08-11
Do you have a webmail account like Gmail? There are specific apps for some.

---

### Post by x-shaney-x on 2010-08-11
The short answer is you can't do what you want to do with evolution (or thunderbird) without using some kind of extra tray app.

Last time I checked into this the evolution devs were pretty adamant that in no way would they make evolution minimize to tray or run in background or anything like that.
So the only hope is a plugin to do it but I don't know if that will happen (there was a proof of concept one running around at one point but didn't work well).

Kmail does it (last time I checked) but of course it is a KDE app and won't work with the messaging menu in ubuntu.

---

### Post by mike555 on 2010-08-11
That can be done nicely using Thunderbird and the add-on " firetray  .......

---

### Post by Ron Carson on 2010-08-11
I used Kmail on my Ubuntu/Gnome desktop and the tray notification system worked fine.   I always had trouble with Kmail's address book, so I recently moved to Thunderbird. And like the OP stated, the Firetray addon works very well.  It minimizes to the tray and gives notice of new emails.

---

