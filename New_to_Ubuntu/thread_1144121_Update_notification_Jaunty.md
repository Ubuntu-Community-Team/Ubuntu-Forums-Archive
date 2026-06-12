---
title: "Update notification Jaunty"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by dndrich on 2009-04-30
Ubuntupals:

I know this has been posted, but I just can't find it.  How do I make Jaunty use the previous method of update notification?  That is, in Intrepid a red arrow shows up on the upper panel.  In Jaunty the update manager just shows up running.

---

### Post by kanikilu on 2009-04-30
I've been skipping over these threads since I haven't used Gnome in Jaunty, but according to a blog/article I read today, I don't think there is a way to change this new update behavior.

Someone correct me if I'm misinformed...

---

### Post by kanikilu on 2009-04-30
Maybe I spoke too soon, this page seems to refer to a method to revert to the old behavior:

[http://brainstorm.ubuntu.com/idea/19283/](http://brainstorm.ubuntu.com/idea/19283/)

---

### Post by Razmear on 2009-04-30
I used this method yesterday: 

>> To disable the new behaviour and get the old behaviour use:
>>
>> gconftool -s --type bool /apps/update-notifier/auto_launch false
>>
>> Take into account that this gconf change is not supported.

and today I have my notification icon informing me about 3 updates waiting, so it works just fine. 

eb

---

### Post by donato roque on 2009-05-01
The Update Manager suddenly appearing in the bottom panel, minimized, 
and without the update icon (the red arrow) in the previous method of 
notification, does NOT constitute notification.

New users would be confused by this.

---

