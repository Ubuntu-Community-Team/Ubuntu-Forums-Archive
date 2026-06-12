---
title: "Evolution mail notification"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by scared0o0rabbit on 2009-12-04
So when I ran jaunty it came with evolution mail by default.  There was a notifier in the task bar that changed if I had mail or if I received a message in pidgin.

When I switched to karmic, it came with thunderbird by default.  Thunderbird runs poorly in ubuntu for me (worked great in windows), so I went ahead and removed it and installed evolution again and it works great.  However, I don't have something on the panel that changes when I get mail now (though there is a change in the mail icon on the panel when I get a message in pidgin).  Is there some way I can get this functionality back?

---

### Post by jediborger on 2009-12-05
I am rather confused by your install. Karmic shipped with Evolution as default, not Thunderbird. Are you saying that when you upgraded, Evolution was removed and Thunderbird installed?

As for the mail notification. The new Message Notifier that combines Empathy and Evolution notifications will only notify you of new messages if you have Evolution running. If you want something that notifies you of new mail without having Evolution constantly running I would look into Mail Notification. It's available in the Software Center. Basically this app polls a list of email inboxes that you setup and pops up a notification when there is new mail. The settings for this app are under System-Preferences-Mail Notification after you install it.

I would personally like to see this functionality integrated into the new Message Indicator but currently Evolution must be running unless you use another app such as Mail Notification. Hope this helps.

---

### Post by scared0o0rabbit on 2009-12-06
When I installed karmic it did not come with evolution installed by default, it came with thunderbird installed.  This was not an upgrade from jaunty.

Even when I have evolution open it doesn't change the icon when I get email.

---

