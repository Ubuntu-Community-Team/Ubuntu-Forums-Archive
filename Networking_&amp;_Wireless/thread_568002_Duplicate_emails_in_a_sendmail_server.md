---
title: "Duplicate emails in a sendmail server"
date: 2007-10-05
forum: Networking &amp; Wireless
---

### Post by [S|G] on 2007-10-05
Hello,

I am running a sendmail server that has the following aliases:

group: user1, user2, user3
user2: user1, user2
user3: user1, user3

When anyone sends a message to group, it works fine, and user1, user2 and user3 get one message each. However, if I send a message to group AND to user2, user1 gets 2 messages, and so on.

How can I configure sendmail so that user1 will get only one message, even if the message is sent to "group, user1, user2, user3"?

Thank you!

---

