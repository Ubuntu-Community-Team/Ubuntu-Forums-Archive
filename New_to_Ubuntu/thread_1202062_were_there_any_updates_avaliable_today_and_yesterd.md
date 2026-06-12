---
title: "were there any updates avaliable today and yesterday?"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by heyyy on 2009-07-01
i saw on a pc of a friend of mine that some updates were avaliable to him but i hadn't any updates notification

maybe i hadn't set up correctly the notifications but for the moment i'm curious if you had any updates at all
so..?

---

### Post by Geoff918 on 2009-07-01
Well, that would depend on what repositories you have enabled, etc.  What you can always do is update your software sources. I prefer to do this from the command prompt, though it can all be done from within GNOME or w/e desktop you're using.  commands are as follows in a terminal window: - sudo aptitude update - sudo aptitude safe-upgrade  That will tell you what needs to be upgraded, etc. and do so. I prefer aptitude over apt-get for uninstall reasons, etc. You can just as easily substitute apt-get in there if you prefer.

---

### Post by heyyy on 2009-07-01
> **Geoff918 said:**
> Well, that would depend on what repositories you have enabled, etc.  What you can always do is update your software sources. I prefer to do this from the command prompt, though it can all be done from within GNOME or w/e desktop you're using.  commands are as follows in a terminal window: - sudo aptitude update - sudo aptitude safe-upgrade  That will tell you what needs to be upgraded, etc. and do so. I prefer aptitude over apt-get for uninstall reasons, etc. You can just as easily substitute apt-get in there if you prefer.

ok thanks but did you have any updates the the last 2 days?

---

### Post by Geoff918 on 2009-07-01
Well, I believe I did have some two days ago. Nothing today, however. Not sure if that really helps.

---

### Post by lisati on 2009-07-01
Whether or not there are updates can depend on what you have installed on your machine. Sometims (but not always) I find I have to start the update manager manually to be notified, e.g. System->Administration->Update manager then click on the "check" button

---

### Post by heyyy on 2009-07-01
for what i remember the updates had to do with linux headers...

---

### Post by heyyy on 2009-07-01
did you have any updates today?

---

### Post by Geoff918 on 2009-07-01
Linux-Headers? Hmm, sounds like your friend has the source repositories enabled. Unless you're busy about compiling something or build your system from source this generally isn't important. The headers shouldn't matter much to any normal computer usage.

---

### Post by heyyy on 2009-07-01
> **Geoff918 said:**
> Linux-Headers? Hmm, sounds like your friend has the source repositories enabled. Unless you're busy about compiling something or build your system from source this generally isn't important. The headers shouldn't matter much to any normal computer usage.

ok but did you have any updates to your system today?

---

### Post by Geoff918 on 2009-07-01
Okay, I found what you're talking about. Sorry for the earlier discussion. Go to System -> Administration -> Update Manager (input your password). There you will find the security updates you're looking for. I'm surprised that the general update from the command prompt didn't include these. So, I learned something new, and yes the headers are included there.

---

### Post by egalvan on 2009-07-02
> **heyyy said:**
> i saw on a pc of a friend of mine that some updates were avaliable to him but i hadn't any updates notification

maybe i hadn't set up correctly the notifications but for the moment i'm curious if you had any updates at all
so..?

This is so dependent on exactly what Linux he has installed.

What Release ?

Hardy?
Intrepid?
Jaunty?

Now, for each of the above we have...

What Desktop (if any)

Gnome?
KDE 3.x?
KDE 4.x?
XFCE?
none (command-line only)?

Now, exactly what repos are enabled?

Universe?
Mulitverse?
Medibuntu?
Backports?
Third Party?
other?

unless you have the exact same set-up, you cannot judge update availability on what others are getting.

I have a Hardy desktop and a Hardy laptop, and they get different updates,
and these are different from my Jaunty desktop...
On the same day. :)


[edit]
Just checked, Hardy and Jaunty both had kernel updates, 
but of course different versions.
They all looked to be security updates.


As for the aptitude/apt-get differences, they are a thing of the past.

---

