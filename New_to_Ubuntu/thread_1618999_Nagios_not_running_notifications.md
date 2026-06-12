---
title: "Nagios not running notifications"
date: 2010-11-11
forum: New to Ubuntu
---

### Post by Maclor on 2010-11-11
I've been trying to get Nagios to send notifications for a few days now with no luck. I am using mutt to send emails through gmail but I recently noticed that Nagios doesn't even run the notifications. I changed service-notify-by-email to just touch /test/test and it won't even create the file. I have users assigned to the services and service-notify-by-email assigned to the users but it still will not run. I'm completely stumped on this one.

I'm not really sure which configs would be needed but will gladly post them if requested.

---

### Post by Maclor on 2010-11-11
I should probably say I followed this guide for the Nagios setup. 

[http://en.doc.centreon.com/Setup](http://en.doc.centreon.com/Setup)

---

### Post by Maclor on 2010-11-11
Checked my nagios log and found 

[1289497285] SERVICE NOTIFICATION: Admin;server;Memory;CRITICAL;service-notify-by-email;Connection refused

Not sure how the notification is getting refused but that seems to be the problem.

---

