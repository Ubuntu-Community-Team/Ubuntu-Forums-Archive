---
title: "Question About Update Manager"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by comsparks on 2009-06-30
Is Update Manager suppose to notify you if there are updates or are you suppose to check manually? I never get notified and have to check it manually at least once a week. Thanks

---

### Post by darthmob on 2009-06-30
There is a settings button at the bottom when you start the update manager. You can tell it to check for updates daily and select if it automatically downloads the updates or prints a notification.

---

### Post by mcduck on 2009-06-30
> **comsparks said:**
> Is Update Manager suppose to notify you if there are updates or are you suppose to check manually? I never get notified and have to check it manually at least once a week. Thanks

The current default behavior is that it notifies you about security updates immediately, but for normal updates only once a week.

Or, actually, that's 7 days from the last time you have opened the program, so if you open it yourself "at least once a week" it's never going to open on it's own.

(If you'd like Update Manager to behave like it did in previous Ubuntu versions, showing an icon in the notification area when updates are available, that's easy to achieve. Just open gconf-editor, browse to apps/update-notifier and disable "auto_launch"-key")

---

### Post by sadaruwan12 on 2009-06-30
Well normally the update manager will notify if there's any updates are available. If it doesn't go to System -> administration -> software sources and go to the tab updates. See whether the automatic update check has been disabled if it is disabled the re-enable it and click on close.

---

### Post by drs305 on 2009-06-30
> **sadaruwan12 said:**
> Well normally the update manager will notify if there's any updates are available. If it doesn't go to System -> administration -> software sources and go to the tab updates. See whether the automatic update check has been disabled if it is disabled the re-enable it and click on close.

sadaruwan12,

That *was* the way it worked until Jaunty. With Jaunty it now performs as described by mcduck. Since the OP doesn't have his version in the signature line, we cannot be sure which version he has but it sounds more like Jaunty.

Another reason to have which version you use in your profile.  ;-)
To add it, click on the User CP link (at top left of page) and select "Edit Your Details" in the left-side links, then scroll down to "Additional Information" on the right. Edit the "Ubuntu Version" selection box.

---

### Post by comsparks on 2009-06-30
I have V 9.04. I have read all comments thus far and have in fact the correct settings as you suggest. I still do not receive notifications. Before anyone asks I have the following checked:

Important Security Updates (Jaunty Security)
Recommended Updates (Jaunty Updates)

Check For Updates:  Daily

Only Notify About available Updates

Show New Distribution Releases: Normal Releases

---

### Post by mcduck on 2009-06-30
> **comsparks said:**
> I have V 9.04. I have read all comments thus far and have in fact the correct settings as you suggest. I still do not receive notifications. Before anyone asks I have the following checked:

Important Security Updates (Jaunty Security)
Recommended Updates (Jaunty Updates)

Check For Updates:  Daily

Only Notify About available Updates

Show New Distribution Releases: Normal Releases

Even if you make the update manager check for updates every day it will *still* only pop up once every seven days. Now it simply *checks* for updates more often. :D

The notification interval can be changed through the gconf-editor, in the same place I mentioned in my previous post for enabling the notification icon (which, by the way, will show immediately when updates are available)

---

### Post by comsparks on 2009-06-30
Thanks McDuck I'm trying but I get errors when I try to open the editor and when I do get it open I get a / and can't do anything.

---

### Post by comsparks on 2009-06-30
OK got it that time. Thanks again Mcduck for all the help. Also all the rest of you for your quick response! I was just curious about it and learn new things all the time here. Great bunch of folks!!!

---

### Post by comsparks on 2009-06-30
Thanks DRS305 I didn't know about or how to do that in the Signature line.

---

### Post by comsparks on 2009-07-02
Follow up to mcduck. The procedure works like a charm thank you. Now I don't have to check everyday or wait a week to find out that there are important security updates that need to be addressed. Thanks again!

---

