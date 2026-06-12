---
title: "Is there an email notifier that stays on the screen?"
date: 2010-09-26
forum: New to Ubuntu
---

### Post by begtognen on 2010-09-26
I'm very new to Ubuntu. When I was using Windows XP, I was using Trillian as an email notifier.

Whenever a new email came in, Trillian would pop up a box with the sender, subject, and date. It was there until I told it to go away.

Is there something similar for Ubuntu? 

I've kind of hacked something together using CheckGmail, but it only tells me the sender unless I hover over the taskbar icon, and the only way to get the notification to go away is by restarting CheckGmail (as I've purposefully set it to stay for 999 seconds).

The reason I'd like a notifier that I have to acknowledge is because I'm away from my computer a lot, and miss notifiers that stay for a few seconds (or even minutes) and then vanish on their own. (Though CheckGmail allows me to set it so that my email program is automatically opened when an email comes in, that's too much of an interruption to my work flow.)

Any help/suggestions are appreciated. Thanks so much.

---

### Post by begtognen on 2010-09-27
Hooray! I found Mail Notification, which makes a notification dialogue box that stays on the screen until you've acknowledged it. (If you tell it to "never expire" in the preferences.)

---

### Post by begtognen on 2010-09-29
To get Mail Notification to use Notify-OSD:

1. Run gconf-editor
2. Navigate to apps -> mail-notification -> popups
3. Delete all values for the 'actions' key

You don't get the dialogue box, but you *can* set it to expire in MORE than 10 seconds, which is exactly what I wanted. (Be careful not to set it *too* high; no other notifications can appear while that one's on the screen.)

---

